---
title: "Wiązania punktów przerwania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 55416d6b156055d967424476f5add3b4ed75d18d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="binding-breakpoints"></a>Wiązania punktów przerwania
Jeśli punkt przerwania ustawiony przez użytkownika, prawdopodobnie naciskając F9 IDE formulates żądanie i wyświetla monit o sesji debugowania, aby utworzyć punkt przerwania.  
  
## <a name="setting-a-breakpoint"></a>Ustawienia punktu przerwania  
 Ustawienia punktu przerwania jest procesem dwuetapowym, ponieważ kod lub danych dotyczy punkt przerwania może jeszcze być niedostępne. Najpierw punktu przerwania musi być opisany, a następnie udostępnieniu kodu lub danych, jej musi być powiązana z tego kodu lub danych, w następujący sposób:  
  
1.  Punkt przerwania zażąda aparatami debugowania odpowiednich (DEs), a następnie punkt przerwania jest powiązane z kodu lub danych stanie się dostępny.  
  
2.  Żądanie przerwania jest wysyłane do sesji debugowania, który wysyła je do wszystkich odpowiednich DEs. Wszelkie DE, który wybiera do obsługi punktu przerwania tworzy odpowiadającego oczekujących punktu przerwania.  
  
3.  Sesja debugowania zbiera oczekujących punktów przerwania i wysyła je z powrotem do pakietu debugowania (składnik debugowania programu Visual Studio).  
  
4.  Pakiet debugowania monituje sesji debugowania, aby powiązać oczekującym punktem przerwania kodu lub danych. Sesja debugowania wysyła to żądanie do wszystkich odpowiednich DEs.  
  
5.  Jeśli DE jest w stanie powiązać punktu przerwania, wysyła się, że punkt przerwania powiązane zdarzenia do sesji debugowania. Jeśli nie, zamiast tego wysyła zdarzenie błędu punktu przerwania.  
  
## <a name="pending-breakpoints"></a>Oczekujące punkty przerwania  
 Oczekującym punktem przerwania można powiązać z wielu lokalizacji kodu. Na przykład wiersz kodu źródłowego dla szablonów języka C++ można powiązać z każdej kolejny kodu wygenerowane z szablonu. Sesja debugowania zdarzenia można użyć w punktu przerwania powiązanej wyliczyć kontekstów kod powiązany punkt przerwania w czasie, którego wysłano zdarzenie. Więcej kontekstów kod może być powiązana później, więc DE może wysłać zdarzenia dla każdego żądania bind powiązany wiele punktów przerwania. Jednak URZ należy wysłać tylko jedno zdarzenie błędu punktu przerwania na żądanie powiązania.  
  
## <a name="implementation"></a>Implementacja  
 Programowo, pakiet debugowania wywołanie sesji debugowania Menedżera (SDM) i nadaje mu [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfejs, który opakowuje [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) struktury, która opisuje punkt przerwania do ustawienia. Mimo że punktów przerwania może mieć wiele form, ostatecznie rozpoznają kontekst kodu lub danych.  
  
 SDM przekazuje tego wywołania do każdego odpowiednich DE przez wywołanie jego [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metody. Jeśli do obsługi punktu przerwania DE, tworzy i zwraca [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfejsu. SDM zbierania tych interfejsów i przekazuje je do debugowania pakiet jako pojedynczy `IDebugPendingBreakpoint2` interfejsu.  
  
 Do tej pory zostały wygenerowane żadne zdarzenia.  
  
 Pakiet debugowania podejmuje próbę powiązać oczekującym punktem przerwania kodu lub danych przez wywołanie metody [powiązać](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), który jest implementowany przez Niemcy.  
  
 Jeśli punkt przerwania jest powiązany, wysyła DE [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfejsu zdarzenia do pakietu debugowania. Używa pakietu debugowania wyliczyć wszystkie konteksty kodu (lub kontekstu danych) w tym interfejsie powiązany punkt przerwania przez wywołanie metody [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), która zwraca co najmniej jeden [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfejsów. [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) interfejsu zwraca [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfejsu i [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) zwraca [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) związkiem zawierającym kod lub dane kontekstu.  
  
 Jeśli nie można powiązać punktu przerwania DE, wysyła pojedynczy [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interfejsu zdarzenia do pakietu debugowania. Pakiet debugowania pobiera typ błędu (błąd lub ostrzeżenie) i komunikat informacyjny wywołując [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), a następnie [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) i [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). To polecenie zwróci [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) strukturę, która zawiera typ błędów i komunikatów.  
  
 Jeśli URZ obsługuje punkt przerwania, ale nie można powiązać ją, zwracany jest błąd typu `BPET_TYPE_ERROR`. Pakiet debugowania odpowiada wyświetlania okna dialogowego błędu, i IDE umieszcza symbolu wykrzyknika wewnątrz symbolu punktu przerwania na lewo od wiersza kodu źródłowego.  
  
 Jeśli URZ obsługuje punkt przerwania, nie można powiązać ją, ale niektóre inne DE może powiązać ją, zwracana jest ostrzeżenie. IDE odpowiada przez umieszczenie symbolu zapytania wewnątrz symbolu punktu przerwania na lewo od wiersza kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)