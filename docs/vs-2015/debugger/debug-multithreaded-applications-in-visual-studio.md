---
title: Debugowanie aplikacji wielowątkowych w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff0030baec409ae54dc5ebb219f5419e583a0efd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684060"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuguj aplikacje wielowątkowe w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [debugowania aplikacji wielowątkowych w programie Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debug-multithreaded-applications-in-visual-studio).  
  
Wątek jest sekwencją instrukcji, do których system operacyjny przydziela czas procesora. Każdy proces, który jest uruchomiony w systemie operacyjnym, składa się z co najmniej jeden wątek. Procesy, które mają więcej niż jeden wątek nazywane są wielowątkowymi.  
  
 Komputery z wieloma procesorami, procesory wielordzeniowe lub procesy hyperthreading mogą uruchomić wiele wątków, w tym samym czasie. Równoległe przetwarzanie wiele wątków może znacznie poprawić wydajność programów, ale może również sprawić, że debugowanie trudniejsze ponieważ wprowadza konieczność, aby śledzić wiele wątków.  
  
 Ponadto wielowątkowość wprowadza kilka nowych rodzajów potencjalnych błędów. Często na przykład dwa lub więcej wątków, trzeba mieć dostęp do tego samego zasobu, ale tylko jeden wątek może bezpiecznie uzyskać dostępu do zasobu w danym momencie. Niektóre forma wzajemnego wykluczania jest niezbędne upewnić się, że tylko jeden wątek uzyskuje dostęp do zasobów w danym momencie. Jeśli wzajemne wykluczanie jest wykonywane niepoprawnie, może utworzyć *zakleszczenia* warunku, gdzie żaden wątek nie może wykonać. Zakleszczenia mogą być problemem szczególnie trudnym do debugowania.  
  
 Program Visual Studio udostępnia **wątków** okna, okno wątków GPU, okno czujki równoległej i inne funkcje, które debugowanie wielowątkowe. Najlepszym sposobem, aby dowiedzieć się więcej o funkcjach wątkowości jest wykonanie instrukcji opisanych w przewodnikach. Zobacz [wskazówki: debugowanie aplikacji wielowątkowych](../debugger/walkthrough-debugging-a-multithreaded-application.md) i [wskazówki: debugowanie aplikacji C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).  
  
 Visual Studio udostępnia również zaawansowane punkty przerwania i punkty śledzenia, które mogą być bardzo przydatne podczas debugowania aplikacji wielowątkowych. Filtry punktów przerwania można użyć, aby umieścić punkty przerwania na jednym z wątków. Zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md)  
  
 Debugowanie aplikacji wielowątkowej, która ma interfejs użytkownika może być szczególnie trudne. W takim przypadku można rozważyć uruchamiania aplikacji na drugim komputerze i za pomocą zdalnego debugowania. Aby uzyskać informacje, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Debugowanie wątków i procesów](../debugger/debug-threads-and-processes.md)  
 W tym artykule wyjaśniono podstawowe informacje dotyczące debugowania wątków i procesów.  
  
 [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)  
 Wyjaśnia, jak debugowanie wielu procesów.  
  
 [Porady: Korzystanie z okna wątków](../debugger/how-to-use-the-threads-window.md)  
 Użyteczne procedury dotyczące debugowania wątków przy użyciu **wątków** okna.  
  
 [Porady: przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Trzy sposoby przełączenia kontekstu debugowania do innego wątku.  
  
 [Porady: Oflagowanie i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md)  
 Oznacz lub Oflaguj wątki, które chcesz poświęcić szczególną uwagę podczas debugowania.  
  
 [Porady: Ustawianie nazw wątków w kodzie natywnym](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Nadaj wątkowi nazwę, którą można wyświetlić w **wątków** okna.  
  
 [Porady: Ustawianie nazw wątków w kodzie zarządzanym](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Nadaj wątkowi nazwę, którą można wyświetlić w **wątków** okna.  
  
 [Wskazówki: Debugowanie aplikacji wielowątkowych](../debugger/walkthrough-debugging-a-multithreaded-application.md).  
 Przewodnik po funkcjach debugowania wątku, z naciskiem na funkcje jak do [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].  
  
 [Porady: debugowanie w klastrze o wysokiej wydajności](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Techniki debugowania aplikacji, która działa w klastrze wysokiej wydajności.  
  
 [Porady dotyczące debugowania wątków w kodzie natywnym](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Proste techniki, które mogą być przydatne podczas debugowania wątków natywnych.  
  
 [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)  
 Wyświetla listę wszystkich obiektów zadań zarządzanych lub natywnych, łącznie z ich stanami i innymi przydatnymi informacjami.  
  
 [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)  
 Wywołanie pokazuje stosy wielu wątków (lub zadaniami) w jednym widoku, a ponadto scala segmenty stosów, które są wspólne miedzy wątkami (lub zadaniami).  
  
 [Wskazówki: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Przewodnik, który pokazuje, jak używać okien zadań równoległych i stosów przetwarzania równoległego.  
  
 [Porady: Korzystanie z okna równoległego wyrażenia kontrolnego](../debugger/how-to-use-the-parallel-watch-window.md)  
 Sprawdź wartości i wyrażenia przez wiele wątków.  
  
 [Porady: Korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
 Badanie i Praca z wątków, które są uruchomione w procesorze GPU podczas debugowania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)  
 -   Filtry punktów przerwania należy użyć, gdy chcesz umieścić punkt przerwania na jednym z wątków.  
  
-   Punkty śledzenia pozwalają na wykonywanie śledzenia programu bez przerywania. Może to być przydatne do badania problemów, takich jak zakleszczenia.  
  
 [Wątkowość](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87)  
 Pojęcia wielowątkowości w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programowania, w tym przykładzie kodu.  
  
 [Wielowątkowość w składnikach](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 Jak używać wielowątkowości w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] składników.  
  
 [Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](http://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c)  
 Pojęcia wielowątkowości i przykładowy kod dla programistów C++ przy użyciu biblioteki MFC.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie wątków i procesów](../debugger/debug-threads-and-processes.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)



