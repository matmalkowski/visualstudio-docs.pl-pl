---
title: Dołączanie bezpośrednio do programu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6885cb0dea801ab95e2e88e3f8168c139fea0e0c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="attaching-directly-to-a-program"></a>Dołączanie bezpośrednio do programu
Użytkownicy, którzy chcą do debugowania programów w procesie, która jest już uruchomiona zwykle skorzystać z tego procesu:  
  
1.  W środowisku IDE, wybierz **debugowanie procesów** polecenie **narzędzia** menu.  
  
     **Procesów** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz proces, a następnie kliknij przycisk **Attach** przycisku.  
  
     **Dołączyć do procesu** zostanie wyświetlone okno dialogowe, wyświetlone wszelkie aparatami debugowania (DEs) zainstalowane na tym komputerze.  
  
3.  Określ DEs na potrzeby debugowania wybrany proces, a następnie kliknij przycisk **OK**.  
  
 Pakiet debugowania uruchamia sesję debugowania i przekazuje listę DEs. Sesja debugowania z kolei przekazuje tej listy, wraz z funkcję wywołania zwrotnego do wybranego procesu i następnie prosi procesu wyliczyć jego uruchomione programy.  
  
 Programowo w odpowiedzi na żądanie użytkownika, pakiet debugowania tworzy wystąpienie Menedżera debugowania sesji (SDM) i przekazuje do listy wybranych DEs. Wraz z listy, pakiet debugowania przekazuje SDM [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfejsu. Pakiet debugowania przekazuje listę DEs do wybranego procesu przez wywołanie metody [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Następnie wywołuje SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) na porcie wyliczyć programów uruchomionych w procesie.  
  
 Od tego momentu każdy aparat debugowania jest dołączony do programu dokładnie zgodnie z opisem w [dołączanie po uruchamianie](../../extensibility/debugger/attaching-after-a-launch.md), z dwoma wyjątkami.  
  
 W celu zwiększenia wydajności DEs, które są wdrożone na udostępnianie przestrzeń adresową SDM są grupowane tak, aby każdy DE zestaw programów, które będzie dołączać. W takim przypadku [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) wywołania [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) i przekazuje je programów do dołączenia do tablicy.  
  
 Drugi wyjątek to, że zdarzenia uruchamiania wysyłane przez DE, dołączenie do programu, który jest już uruchomiona nie dołączaj zwykle zdarzenie punktu wejścia.  
  
## <a name="see-also"></a>Zobacz też  
 [Wysyłanie zdarzeń do uruchomienia po Launch](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)