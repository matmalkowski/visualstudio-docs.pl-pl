---
title: Program kontrolki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c227f38c926cb6d764ddf47541b8bd744eb6f7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="program-control"></a>Formant programu
W programie Visual Studio debugowanie wszystkich stepping następujących i kontynuowanie procedury są wykonywane na poziomie programu:  
  
-   Oznacza to, że ustawienie następnej instrukcji, ustawienie komputera na następną instrukcję, która ma być wykonywana w środowisku klatek  
  
-   Oznacza to, że kontynuowanie wykonywania, wyjść z trybu wykonywania krokowego  
  
-   Przechodzenie do następnej instrukcji  
  
-   Kontynuowanie bieżący tryb wykonywania krokowego  
  
-   Zawieszanie wątków zawartych w programie  
  
-   Wznawianie wątków zawartych w programie  
  
> [!NOTE]
>  Wyświetlanie stos wywołań jest wdrażana w poziomie wątku. Aby wyliczyć informacji ramki, podczas wyświetlania stos wywołań dla wątku, musisz zaimplementować wszystkich metod z [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfejsu.  
  
## <a name="methods-of-program-control"></a>Metody kontroli programu  
 W poniższej tabeli przedstawiono metody [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) musi zostać wdrożone dla aparatu debugowania minimalny funkcjonalności (DE) i kontrola wykonywania.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Nadal uruchomione wszystkie wątki zawarty w program w stanie zatrzymania. Wymagane do wykonywania kontroli.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Nadal uruchomione wszystkie wątki zawarty w program w stanie zatrzymania. Wymagane do wykonywania kontroli.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Wykonuje kroku dla danego wątku. Nadal uruchomione inne wątki zawartych w programie. Wymagane do wykonywania kontroli.|  
  
 W przypadku programów wielowątkowych musi także implementować [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) — metoda i wszystkie metody [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)