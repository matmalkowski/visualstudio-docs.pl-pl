---
title: "Dołączanie bezpośrednio do programu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c528925e323e4cff5784365e3097cc7f5f414963
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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