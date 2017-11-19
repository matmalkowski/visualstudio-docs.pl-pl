---
title: Program kontrolki | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb69afe513010a7da4b4a85669bbc5f145f8dbc5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Kontrola wykonywania i oceny stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)