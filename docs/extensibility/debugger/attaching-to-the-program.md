---
title: Dołączanie do programu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a4c9719f6258f3bbb5cc8323693001c7f1a9d47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107871"
---
# <a name="attaching-to-the-program"></a>Dołączanie do programu
Po zarejestrowaniu programy z odpowiedni port należy dołączyć debuger do programu, który chcesz debugować.  
  
## <a name="choosing-how-to-attach"></a>Wybór sposobu dołączyć  
 Istnieją trzy sposoby, w których próbuje dołączyć do debugowanego programu Menedżer debugowania sesji (SDM).  
  
1.  Dla programów, które będą uruchamiane przez aparat debugowania za pośrednictwem [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) uzyskuje SDM — metoda (typowe języków interpretowanego, na przykład), [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfejsu z [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) skojarzony z programem dołączony do obiektu. Jeśli można uzyskać SDM `IDebugProgramNodeAttach2` następnie wywołuje interfejs, SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody. `IDebugProgramNodeAttach2::OnAttach` Metoda zwraca `S_OK` oznacza, że nie dołączyć do programu i że inne próby możliwe do dołączenia do programu.  
  
2.  Jeśli SDM może uzyskać [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) interfejsu programu dołączany do wywołania SDM [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) metody. Ta metoda jest typowa dla programów, które zostały uruchomione zdalnie przez dostawcę portu.  
  
3.  Jeśli program nie może zostać dołączony do `IDebugProgramNodeAttach2::OnAttach` lub `IDebugProgramEx2::Attach` metod SDM ładuje aparat debugowania (Jeśli nie został jeszcze załadowany) przez wywołanie metody `CoCreateInstance` funkcji, a następnie wywołania [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metody. Ta metoda jest typowa dla programy uruchamiane lokalnie przez dostawcę portu.  
  
     Istnieje również możliwość dla dostawcy niestandardowego numeru portu do wywołania `IDebugEngine2::Attach` metody implementacji dostawcy niestandardowego numeru portu `IDebugProgramEx2::Attach` metody. Zazwyczaj w takim przypadku dostawcy niestandardowego numeru portu uruchamia aparat debugowania na zdalnym komputerze.  
  
 Załącznik jest osiągana, gdy Menedżer debugowania sesji (SDM) wywołuje [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metody.  
  
 Jeśli Uruchom Twojej DE w tym samym procesie jako aplikację do debugowania, a następnie musi implementować następujące metody [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 Po `IDebugEngine2::Attach` metoda jest wywoływana, wykonaj następujące kroki w implementacji `IDebugEngine2::Attach` metody:  
  
1.  Wyślij [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) obiekt zdarzenia do SDM. Aby uzyskać więcej informacji, zobacz [wysyłania zdarzeń](../../extensibility/debugger/sending-events.md).  
  
2.  Wywołanie [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metoda [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) obiektu, który został przekazany do `IDebugEngine2::Attach` metody.  
  
     To polecenie zwróci `GUID` używany do identyfikacji programu. `GUID` Musi być przechowywany w obiekcie reprezentuje lokalnej programu DE, czy należy zwracane, gdy `IDebugProgram2::GetProgramId` wywoływana jest metoda `IDebugProgram2` interfejsu.  
  
    > [!NOTE]
    >  W przypadku zastosowania `IDebugProgramNodeAttach2` interfejsu programu `GUID` jest przekazywana do `IDebugProgramNodeAttach2::OnAttach` metody. To `GUID` jest wykorzystywany przez program `GUID` zwrócony przez `IDebugProgram2::GetProgramId` metody.  
  
3.  Wyślij [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) obiekt zdarzenia powiadomiono SDM który lokalnej `IDebugProgram2` do reprezentowania program DE utworzenia obiektu. Aby uzyskać więcej informacji, zobacz [wysyłania zdarzeń](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  To nie jest taka sama `IDebugProgram2` obiekt, który został przekazany `IDebugEngine2::Attach` metody. Wcześniej przekazany `IDebugProgram2` obiekt jest rozpoznawana przez port tylko i oddzielny obiekt.  
  
## <a name="see-also"></a>Zobacz też  
 [Na podstawie uruchamiania załącznika](../../extensibility/debugger/launch-based-attachment.md)   
 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Dołącz](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)