---
title: Dołączanie po Launch | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69f9f9cde76c5fa66294fd2cdbdc5252169e0183
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="attaching-after-a-launch"></a>Dołączanie po Launch
Po uruchomieniu programu sesji debugowania jest gotowy do podłączenia aparat debugowania (DE) do wspomnianej program.  
  
## <a name="design-decisions"></a>Decyzje dotyczące projektu  
 Ponieważ komunikacja jest łatwiejsze w współużytkowanego obszaru adresów, należy zdecydować, czy warto więcej ułatwiają komunikację między sesji debugowania i DE lub między Urządzeniom i program. Wybierz jedną z następujących:  
  
-   Jeśli warto więcej komunikację między sesji debugowania i DE, sesji debugowania wspólnie tworzy DE i prosi o DE można dołączyć do programu. Spowoduje to pozostawienie sesji debugowania i DE razem w jedną przestrzeń adresową i środowisko wykonawcze i programie razem w innym.  
  
-   Jeśli warto więcej komunikację między Urządzeniom i program, następnie środowisko wykonawcze wspólnie tworzy DE. Spowoduje to pozostawienie SDM w jedną przestrzeń adresową, a DE, środowisko wykonawcze i program w innym razem. To jest typowe dla DE, który jest realizowana za pomocą tłumacza, aby uruchomić języków skryptowych.  
  
    > [!NOTE]
    >  Jak DE dołącza do program jest zależny od implementacji. Komunikacja między DE i programem również jest zależne od implementacji.  
  
## <a name="implementation"></a>Implementacja  
 Programistycznie, gdy Menedżer debugowania sesji (SDM) otrzymuje najpierw [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) wywołuje obiekt, który reprezentuje program do uruchomienia, [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) metody przekazanie jej [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) obiektu, który jest nowsza służy do przekazywania zdarzenia debugowania do SDM. `IDebugProgram2::Attach` Metoda wywołuje [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody. Więcej informacji dotyczących sposobu odbiera SDM `IDebugProgram2` interfejsu, zobacz [Port powiadamiania](../../extensibility/debugger/notifying-the-port.md).  
  
 Jeśli Twoje DE musi być uruchamiane w przestrzeni adresowej programu debugowany, zwykle ponieważ DE jest częścią tłumacza, uruchomienie skryptu, `IDebugProgramNodeAttach2::OnAttach` metoda zwraca `S_FALSE`, wskazującą, czy zakończyła się procesu dołączania.  
  
 Jeśli z drugiej strony, DE uruchamia się w przestrzeni adresowej SDM, `IDebugProgramNodeAttach2::OnAttach` metoda zwraca `S_OK` lub [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfejsu nie jest zaimplementowana w ogóle na [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) obiekt skojarzony z debugowany program. W takim przypadku [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) wywoływana jest metoda po pewnym czasie ukończyć operacji dołączania.  
  
 W drugim przypadku należy wywołać [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metoda `IDebugProgram2` obiektu, który został przekazany do `IDebugEngine2::Attach` metody, magazyn `GUID` w lokalnym programie obiektu i zwraca to `GUID` po `IDebugProgram2::GetProgramId` następnie wywoływana jest metoda w tym obiekcie. `GUID` Służy do unikatowego identyfikowania program między różnymi składnikami debugowania.  
  
 Należy pamiętać, że w przypadku programu `IDebugProgramNodeAttach2::OnAttach` metody zwracanie `S_FALSE`, `GUID` do użycia dla programu jest przekazywany do metody i jest `IDebugProgramNodeAttach2::OnAttach` metodę, która ustawia `GUID` na obiekt lokalny program.  
  
 Niemcy zostanie dołączony do programu i są gotowe do wysyłania zdarzeń uruchomienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Dołączanie bezpośrednio do programu](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Port powiadamiania](../../extensibility/debugger/notifying-the-port.md)   
 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Dołącz](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)