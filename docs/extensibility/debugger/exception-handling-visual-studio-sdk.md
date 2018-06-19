---
title: Obsługa (Visual Studio SDK) wyjątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 646479184061b093d5d84f81827a4106bd3cda47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100793"
---
# <a name="exception-handling-visual-studio-sdk"></a>Obsługa (Visual Studio SDK) wyjątków
Poniżej opisano proces, który występuje, gdy są zgłaszane wyjątki.  
  
## <a name="exception-handling-process"></a>Proces obsługi wyjątków  
  
1.  Zgłoszono wyjątek, ale przed jego jest obsługiwany przez program obsługi wyjątku w programie debugowany, aparat debugowania (DE) wysyła [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) do menedżera sesji debugowania (SDM) jako zdarzeniem zatrzymującym. `IDebugExceptionEvent2` Jest wysyłany, gdy tylko ustawienia wyjątków (określony w oknie dialogowym Wyjątki w pakiecie debugowania) określ, czy użytkownik chce zatrzymać na powiadomienia o wyjątkach pierwszej szansy.  
  
2.  Wywołania SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) do pobrania właściwości wyjątku.  
  
3.  Wywołania pakietu debugowania [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) Aby ustalić, jakie opcje do przedstawienia użytkownikowi.  
  
4.  Pakiet debugowania pyta użytkownika, jak obsługiwać wyjątek, otwierając okno dialogowe wyjątkach pierwszej szansy.  
  
5.  Jeśli użytkownik wybierze opcję kontynuowania, wywołuje metodę SDM [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Jeśli metoda zwraca wartość S_OK, wywołuje metodę [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         —lub—  
  
         Jeśli metoda zwraca wartości S_FALSE, program debugowany znajduje się drugiej szansy do obsługi wyjątku.  
  
6.  Jeśli debugowany program obsługi wyjątku drugiej szansy, wysyła DE `IDebugExceptionEvent2` do SDM jako **EVENT_SYNC_STOP**.  
  
7.  Pakiet debugowania pyta użytkownika, jak obsługiwać wyjątek, otwierając okno dialogowe wyjątkach pierwszej szansy.  
  
8.  Wywołania pakietu debugowania [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) Aby ustalić, jakie opcje do przedstawienia użytkownikowi.  
  
9. Pakiet debugowania pyta użytkownika sposobu obsługi wyjątku, otwierając okno dialogowe wyjątek drugiej szansy.  
  
10. Jeśli metoda zwraca wartość S_OK, wywołuje metodę `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)