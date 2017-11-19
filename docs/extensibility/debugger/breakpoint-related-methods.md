---
title: "Metody dotyczące punktu przerwania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0d743c98fd9e311f7f118c152e579178b07513d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="breakpoint-related-methods"></a>Metody dotyczące punktu przerwania
Aparat debugowania (DE) musi obsługiwać ustawienia punktów przerwania. Debugowanie programu Visual Studio obsługuje następujące typy punktów przerwania:  
  
-   Powiązany  
  
     Żądanie za pośrednictwem interfejsu użytkownika i pomyślnie powiązane z lokalizacji określony kod  
  
-   Oczekujące  
  
     Żądanie za pośrednictwem interfejsu użytkownika, ale nie są jeszcze powiązane z rzeczywistego instrukcje  
  
## <a name="discussion"></a>Omówienie  
 Na przykład oczekującym punktem przerwania występuje, gdy nie są jeszcze załadowane zgodnie z instrukcjami. Jeśli kod jest ładowany, oczekujących spróbuj punktów przerwania powiązać kodu w określonej lokalizacji, oznacza to, aby wstawić instrukcji podziału w kodzie. Zdarzenia są wysyłane do Menedżera debugowania sesji (SDM), aby wskazać Powiązanie pomyślne lub powiadamiania wystąpiły błędy podczas wiązania.  
  
 Oczekującym punktem przerwania również zarządza własną wewnętrzną listę odpowiednich powiązane punkty przerwania. Jeden oczekujący punkt przerwania może spowodować wstawiania wiele punktów przerwania w kodzie. Visual Studio debugowanie interfejsu użytkownika pokazano widok drzewa oczekujących punktów przerwania i odpowiednie powiązane punkty przerwania.  
  
 Tworzenie i używanie oczekujących punktów przerwania wymagają wykonania [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metody, a także z następujących metod [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfejsów.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Określa, czy określonej oczekujących punkt przerwania można powiązać z lokalizacji kodu.|  
|[BIND](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Wiąże określoną oczekujących punktu przerwania co najmniej jedna lokalizacja kodu.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Pobiera stan oczekujący punkt przerwania.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Pobiera żądanie przerwania, używany do tworzenia oczekującym punktem przerwania.|  
|[Włącz](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Włącza/wyłącza włączony stan oczekujący punkt przerwania.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Wylicza wszystkie punkty przerwania powiązana z oczekującym punktem przerwania.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Wylicza wszystkie punkty przerwania błędów wynikających z oczekującym punktem przerwania.|  
|[Usuń](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Usuwa oczekującym punktem przerwania i powiązany z niego wszystkie punkty przerwania.|  
  
 Wyliczyć powiązane punkty przerwania i błąd punktów przerwania, musisz zaimplementować wszystkie metody [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) i [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 Oczekujące punktów przerwania, które wiążą się z kodem lokalizacji wymaga wykonania następujących [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekującym punktem przerwania, która zawiera punkt przerwania.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Pobiera stan powiązania punktu przerwania.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Pobiera rozpoznawania punkt przerwania, opisujący punktu przerwania.|  
|[Włącz](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Włącza lub wyłącza punktu przerwania.|  
|[Usuń](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Usuwa powiązania punktu przerwania.|  
  
 Rozdzielczość i żądania informacji wymaga wykonania następujących [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Pobiera typ punktu przerwania reprezentowany przez rozwiązanie.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Pobiera informacje o rozdzielczości punkt przerwania, opisujący punktu przerwania.|  
  
 Rozpoznawanie błędów, które mogą wystąpić podczas tworzenia powiązania wymaga wykonania następujących [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekującym punktem przerwania, która zawiera błąd punktu przerwania.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Pobiera rozpoznawania błędu przerwania opisujący błąd punktu przerwania.|  
  
 Rozpoznawanie błędów, które mogą wystąpić podczas tworzenia powiązania wymaga również następujące metody [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Pobiera typ punktu przerwania.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Pobiera informacje o rozdzielczości punktu przerwania.|  
  
 Wyświetlanie kodu źródłowego w punkcie przerwania wymaga wykonania metody [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) i/lub metody [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania i oceny stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)