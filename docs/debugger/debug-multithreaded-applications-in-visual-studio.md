---
title: Debugowanie aplikacji wielowątkowych w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/05/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 80618257e61356285d9b8c9c2bcf2a7a2e11e831
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279549"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuguj aplikacje wielowątkowe w programie Visual Studio
Wątek jest sekwencją instrukcji, do których system operacyjny przydziela czas procesora. Każdy proces, który jest uruchomiony w systemie operacyjnym, składa się z co najmniej jeden wątek. Procesy, które mają więcej niż jeden wątek nazywane są wielowątkowymi.  
  
Komputery z wieloma procesorami, procesory wielordzeniowe lub procesy hyperthreading mogą uruchomić wiele wątków, w tym samym czasie. Równoległe przetwarzanie wiele wątków może znacznie poprawić wydajność programów, ale może również sprawić, że debugowanie trudniejsze ponieważ wprowadza konieczność, aby śledzić wiele wątków.  
  
Ponadto wielowątkowość wprowadza kilka nowych rodzajów potencjalnych błędów. Często na przykład dwa lub więcej wątków, trzeba mieć dostęp do tego samego zasobu, ale tylko jeden wątek może bezpiecznie uzyskać dostępu do zasobu w danym momencie. Niektóre forma wzajemnego wykluczania jest niezbędne upewnić się, że tylko jeden wątek uzyskuje dostęp do zasobów w danym momencie. Jeśli wzajemne wykluczanie jest wykonywane niepoprawnie, może utworzyć *zakleszczenia* warunku, gdzie żaden wątek nie może wykonać. Zakleszczenia mogą być problemem szczególnie trudnym do debugowania.

Visual Studio zapewnia różne narzędzia do użycia podczas debugowania aplikacji wielowątkowych.

- Dla wątków, podstawowe narzędzia do debugowania wątków to **wątków** okna, znaczniki wątków w oknach źródłowych **stosów równoległych** oknie **równoległego wyrażenia kontrolnego** oknie i **Lokalizacja debugowania** paska narzędzi. Aby dowiedzieć się więcej na temat **wątków** okna i **Lokalizacja debugowania** narzędzi, zobacz [wskazówki: debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md). Aby dowiedzieć się, jak używać **stosów równoległych** i **równoległego wyrażenia kontrolnego** systemu windows, zobacz [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md). Zarówno tematach opisano sposób użycia znaczników wątków.
  
- Dla kodu, który używa [Biblioteka zadań równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) lub [współbieżność środowiska wykonawczego](/cpp/parallel/concrt/concurrency-runtime/), podstawowe narzędzia do debugowania są **stosów równoległych** okna, **Równoległego wyrażenia kontrolnego** oknie i **zadania** okna ( **zadania** okna obsługuje również JavaScript). Aby rozpocząć pracę, zobacz [wskazówki: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md) i [wskazówki: debugowanie aplikacji C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- Do debugowania wątków na procesor GPU, jest podstawowym narzędziem **wątków GPU** okna. Zobacz [porady: Korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Dla procesów, podstawowe narzędzia to **dołączyć do procesu** okno dialogowe **procesy** oknie i **Lokalizacja debugowania** paska narzędzi.  
  
Visual Studio udostępnia również zaawansowane punkty przerwania i punkty śledzenia, które mogą być bardzo przydatne podczas debugowania aplikacji wielowątkowych. Aby umieścić punkty przerwania na jednym z wątków, można użyć warunków punktu przerwania i filtry. Zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md). 
  
Debugowanie aplikacji wielowątkowej, która ma interfejs użytkownika może być szczególnie trudne. W takim przypadku można rozważyć uruchamiania aplikacji na drugim komputerze i za pomocą zdalnego debugowania. Aby uzyskać informacje, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
## <a name="in-this-section"></a>W tej sekcji
 [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md).  
 Przewodnik po funkcjach debugowania wątku, z naciskiem na funkcje w **stosów równoległych** okna i **równoległego wyrażenia kontrolnego** okna.

 [Narzędzia do debugowania wątków i procesów](../debugger/debug-threads-and-processes.md)  
 Wyświetla listę funkcji narzędzia do debugowania wątków i procesów.  
  
 [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)  
 Wyjaśnia, jak debugowanie wielu procesów.

 [Przewodnik: Debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md).  
 Przewodnik, który pokazuje, jak używać **wątków** okna i **Lokalizacja debugowania** paska narzędzi. 

 [Przewodnik: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Przewodnik, który pokazuje, jak używać **stosów równoległych** i **zadania** systemu windows.  
  
 [Instrukcje: przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Trzy sposoby przełączenia kontekstu debugowania do innego wątku.  
  
 [Instrukcje: flagowanie i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md)  
 Oznacz lub Oflaguj wątki, które chcesz poświęcić szczególną uwagę podczas debugowania.    
  
 [Instrukcje: debugowanie w klastrze o wysokiej wydajności](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Techniki debugowania aplikacji, która działa w klastrze wysokiej wydajności.  

 [Wskazówki dotyczące debugowania wątków w kodzie natywnym](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Proste techniki, które mogą być przydatne podczas debugowania wątków natywnych. 

 [Instrukcje: ustawianie nazw wątków w kodzie natywnym](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Nadaj wątkowi nazwę, którą można wyświetlić w **wątków** okna.  
  
 [Instrukcje: ustawianie nazw wątków w kodzie zarządzanym](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Nadaj wątkowi nazwę, którą można wyświetlić w **wątków** okna. 
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)

 - Warunki punktu przerwania lub filtrów należy używać do debugowania wątków.  
  
 - Punkty śledzenia pozwalają na wykonywanie śledzenia programu bez przerywania. Może to być przydatne do badania problemów, takich jak zakleszczenia.  
  
 [Wątkowość](/dotnet/standard/threading/index)  
 Pojęcia wielowątkowości w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] programowania, w tym przykładzie kodu.  
  
 [Wielowątkowość w składnikach](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
 Jak używać wielowątkowości w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] składników.  
  
 [Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 Pojęcia wielowątkowości i przykładowy kod dla programistów C++ przy użyciu biblioteki MFC.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie wątków i procesów](../debugger/debug-threads-and-processes.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)