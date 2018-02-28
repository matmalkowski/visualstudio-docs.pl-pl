---
title: "Wyzwalanie wstrzymania, wznowienia i zdarzeń w tle podczas debugowania aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- uwp
ms.openlocfilehash: 036362ec392e6deba9bed1ef185c602d508d4da4
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Wyzwalanie wstrzymania, wznowienia i zdarzeń w tle podczas debugowania aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio
Jeśli nie debugowania, Windows **Zarządzanie okresem istnienia procesu** (elementu) steruje stanem wykonywania aplikacji — uruchamianie, wstrzymywanie, wznawianie i przerywanie aplikacji w odpowiedzi na działania użytkownika i stan urządzenia. Podczas debugowania, system Windows wyłącza te zdarzenia aktywacji. W tym temacie opisano sposób uruchamiania tych zdarzeń w debugerze.  
  
 W tym temacie opisano również sposób debugowania **zadania w tle**. Zadania w tle umożliwiają wykonywania pewnych operacji w tle, nawet w przypadku aplikacji nie jest uruchomiona. Debuger umożliwia umieszczanie aplikacji w trybie debugowania, a następnie — bez uruchamiania interfejsu użytkownika — start i debugowania zadania w tle.  
  
 Aby uzyskać więcej informacji na temat zadań tła i zarządzanie okresem istnienia procesu zobacz [uruchamianie i wznawianie i wielozadaniowości](/windows/uwp/launch-resume/index).  
  
##  <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a>Wyzwalacz zdarzenia Zarządzanie okresem istnienia procesu  
 Systemu Windows można wstrzymać aplikacji, gdy użytkownik zmienia się od jego lub Windows wejścia w stan niskiego zużycia energii. Może odpowiadać na `Suspending` zdarzeń, aby zapisać odpowiednie dane aplikacji i użytkownika do magazynu trwałego i zwolnić zasoby. Po wznowieniu aplikacji **zawieszone** stanu, wejdzie ona **systemem** stanu, aby kontynuować, z którym był podczas został wstrzymany. Może odpowiadać na `Resuming` zdarzenie, aby przywrócić lub Odśwież stan aplikacji i odzyskać zasoby.  
  
 Chociaż system Windows podejmuje próbę przechowywać dowolną liczbę wstrzymane aplikacje w pamięci, jak to możliwe, systemu Windows może prowadzić aplikacji, jeśli nie ma za mało zasobów, aby przechowywać go w pamięci. Użytkownika można również jawnie Zamknij aplikację. Nie ma żadnego specjalnego zdarzenia, aby wskazać, że użytkownik zamknął aplikacji.  
  
 W debugerze programu Visual Studio można ręcznie wstrzymania, wznowienia i przerwanie debugowania zdarzenia cyklu życia procesu aplikacji. Debugowanie zdarzeń cyklu życia procesu:  
  
1.  Ustaw breakpooint w procedurze obsługi zdarzeń, który chcesz debugować.  
  
2.  Naciśnij klawisz **F5** można rozpocząć debugowania.  
  
3.  Na **debugowania lokalizacji** narzędzi wybierz zdarzenie, które chcesz uruchomić:  
  
     ![Wstrzymywanie, wznawianie, przerwanie i zadania w tle](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
     Należy pamiętać, że **zawieszenia i zakończyć** zamyka aplikację i kończy się sesja debugowania.  
  
##  <a name="BKMK_Trigger_background_tasks"></a>Wyzwalacz zadania w tle  
 Dowolna aplikacja można zarejestrować zadania w tle odpowiadają na określone zdarzenia systemowe, nawet wtedy, gdy aplikacja nie jest uruchomiona. Zadania w tle nie może uruchomić kod, który bezpośrednio aktualizacje interfejsu użytkownika; Zamiast tego zawierają one informacje dla użytkownika z kafelka aktualizacje, aktualizacje badge i wyskakujące powiadomienia. Aby uzyskać więcej informacji, zobacz [Obsługa aplikacji za pomocą zadania w tle](http://msdn.microsoft.com/en-us/4c7bb148-eb1f-4640-865e-41f627a46e8e)  
  
 Możesz wyzwolić zdarzenia, które uruchomienia zadania w tle dla aplikacji z debugera.  
  
> [!NOTE]
>  Debuger może wyzwolić tylko te zdarzenia, które nie zawierają danych, takich jak zdarzenia, które wskazują zmiany stanu urządzenia. Należy ręcznie uruchomić zadania w tle, które wymagają danych wejściowych użytkownika lub innych danych.  
  
 Najbardziej realistyczne sposobem wyzwala zdarzenia zadania tła jest gdy aplikacja nie jest uruchomiona. Jednak wyzwolenie zdarzenia w standardowej sesji debugowania jest również obsługiwany.  
  
###  <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a>Wyzwalacz zdarzenia zadania tła z sesji debugowania standardowe  
  
1.  Ustaw punkt przerwania w kodzie zadania tła, który chcesz debugować.  
  
2.  Naciśnij klawisz **F5** można rozpocząć debugowania.  
  
3.  Z listy zdarzeń **debugowania lokalizacji** narzędzi, wybierz pozycję zadania w tle, który chcesz uruchomić.  
  
     ![Wstrzymywanie, wznawianie, przerwanie i zadania w tle](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
###  <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a>Wyzwalanie zadania w tle, gdy aplikacja nie jest uruchomiona.  
  
1.  Ustaw punkt przerwania w kodzie zadania tła, który chcesz debugować.  
  
2.  Otwórz stronę właściwości debugowania projektu rozruchu. W Eksploratorze rozwiązań wybierz projekt. Na **debugowania** menu, wybierz **właściwości**.  
  
     W przypadku projektów C++ i JavaScript, rozwiń **właściwości konfiguracji** , a następnie wybierz **debugowanie**.  
  
3.  Wykonaj jedną z następujących czynności:  
  
    -   Projekty Visual C# i Visual Basic, wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu**  
  
         ![K & 35; &#47; Właściwości aplikacji uruchamiania debugowania VB](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")  
  
    -   Dla projektów języka JavaScript i program Visual C++, wybierz **nr** z **uruchamianie aplikacji** listy.  
  
         ![C &43; &#43; &#47; Uruchamianie VB właściwości debugowania aplikacji](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")  
  
4.  Naciśnij klawisz **F5** umieścić aplikacji w trybie debugowania. Uwaga **procesu** listy na **debugowania lokalizacji** narzędzi Wyświetla nazwę pakietu aplikacji, aby wskazać, że jesteś w trybie debugowania.  
  
     ![Lista procesów zadania tła](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")  
  
5.  Z listy zdarzeń **debugowania lokalizacji** narzędzi, wybierz pozycję zadania w tle, który chcesz uruchomić.  
  
     ![Wstrzymywanie, wznawianie, przerwanie i zadania w tle](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
##  <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a>Wyzwalacz zdarzenia Zarządzanie okresem istnienia procesu, a w tle zadań z zainstalowaną aplikację  
 Użyj **Debuguj zainstalowany pakiet aplikacji** okno dialogowe, aby załadować aplikację, która jest już zainstalowana w debugerze. Na przykład może debugować aplikację, która została zainstalowana z Microsoft Store lub debugowania aplikacji, jeśli masz pliki źródłowe dla aplikacji, ale nie projektu programu Visual Studio dla aplikacji. **Debuguj zainstalowany pakiet aplikacji** okno dialogowe pozwala uruchomić aplikację w trybie debugowania na komputerze programu Visual Studio lub na urządzeniu zdalnym lub ustawienie aplikacji do uruchamiania w trybie debugowania, ale nie można go uruchomić. Aby uzyskać więcej informacji, zobacz [debugowania pakietu aplikacji zainstalowanych](../debugger/debug-installed-app-package.md).
  
 Po załadowaniu aplikacji w debugerze, można użyć dowolnej z opisanych procedur.  
  
##  <a name="BKMK_Diagnosing_background_task_activation_errors"></a>Diagnozowanie błędów aktywacji zadania w tle  
 Dzienniki diagnostyczne w Podglądzie zdarzeń systemu Windows dla infrastruktury tła zawiera szczegółowe informacje, które można użyć do diagnozowania i rozwiązywania problemów, zadania tła. Aby wyświetlić dziennik:  
  
1.  Otwórz aplikację Podgląd zdarzeń.  
  
2.  W **akcje** okienku wybierz **widoku** i upewnij się, że **dzienniki Pokaż analityczne i debugowania** jest zaznaczony.  
  
3.  Na **podglądu zdarzeń (lokalne)** drzewa, rozwiń węzły **Dzienniki aplikacji i usług** > **Microsoft** > **systemu Windows**   >  **BackgroundTasksInfrastructure**.  
  
4.  Wybierz **diagnostycznych** dziennika.  
  
## <a name="see-also"></a>Zobacz też  
 [Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Cykl życia aplikacji](/windows/uwp/launch-resume/app-lifecycle)   
 [Uruchamianie, wznawianie i wielozadaniowości](/windows/uwp/launch-resume/index)