---
title: "Debuguj aplikacje wielowątkowe w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.gputthreads
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
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8b32134abff19965edac150ac5f69db25640ee08
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuguj aplikacje wielowątkowe w programie Visual Studio
Wątek jest sekwencję instrukcji, do których system operacyjny przydziela czas procesora. Każdy proces, który jest uruchomiony w systemie operacyjnym składa się z co najmniej jeden wątek. Procesy, które mają więcej niż jeden wątek są nazywane wielowątkowych.  
  
Komputery z wielu procesorów wielordzeniowych procesorów i procesy wielowątkowość można uruchomić wiele wątków jednocześnie. Przetwarzanie równoległe wielu wątków może znacznie poprawić wydajność programu, ale może również wprowadzać debugowania trudniejsze ponieważ wprowadza ona potrzeba, aby śledzić wiele wątków.  
  
Ponadto wielowątkowość wprowadzono kilka nowych typów potencjalne błędy. Często na przykład dwa lub więcej wątków ma dostęp do tego samego zasobu, ale tylko jeden wątek można bezpiecznie uzyskać dostępu do zasobu naraz. Jakiegoś wzajemne wykluczenie jest niezbędne upewnić się, że tylko jeden wątek jest dostęp do zasobu naraz. Jeśli niepoprawnie odbywa się wzajemne wykluczenie, można utworzyć *zakleszczenie* warunku, gdy wątek nie może zostać uruchomiony. Zakleszczenie może stanowić problem szczególnie twarde do debugowania.

Program Visual Studio udostępnia różnych narzędzi do użycia w debugowanie aplikacji wielowątkowych.

- Wątki, podstawowe narzędzia do debugowania wątki są **wątków** okna, znaczniki wątku w systemie windows źródła **stosów równoległych** okna, **czujki równoległej** okna, i **debugowania lokalizacji** paska narzędzi. Aby dowiedzieć się więcej o **wątków** okna i **debugowania lokalizacji** narzędzi, zobacz [wskazówki: debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md). Aby dowiedzieć się, jak używać **stosów równoległych** i **czujki równoległej** systemu windows, temacie [rozpocząć debugowanie aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md). Zarówno tematach opisano sposób użycia znaczników wątku.
  
- Kod, który używa [zadań biblioteki równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) lub [współbieżność środowiska wykonawczego](/cpp/parallel/concrt/concurrency-runtime/), podstawowe narzędzia do debugowania są **stosów równoległych** okna, **Czujki równoległej** okno i **zadania** okna ( **zadania** okna obsługuje również JavaScript). Aby rozpocząć, zobacz [wskazówki: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md) i [wskazówki: debugowanie aplikacji C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- Debugowanie wątków na procesor GPU, jest podstawowym narzędziem **wątki GPU** okna. Zobacz [porady: Korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Dla procesów, podstawowe narzędzia są **dołączyć do procesu** okno dialogowe **procesów** okno i **debugowania lokalizacji** paska narzędzi.  
  
Visual Studio udostępnia również zaawansowane punktów przerwania i tracepoints, który może być bardzo przydatne podczas debugowania aplikacji wielowątkowych. Można umieścić punkty przerwania w poszczególnych wątków można użyć warunków punktu przerwania i filtry. Zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md). 
  
Debugowanie aplikacji wielowątkowych, który ma interfejsu użytkownika mogą być szczególnie trudne. W takim przypadku warto rozważyć uruchomienie aplikacji na drugim komputerze i użycie, zdalnego debugowania. Aby uzyskać informacje, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).  
  
## <a name="in-this-section"></a>W tej sekcji
 [Rozpocząć debugowanie aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md).  
 Samouczek debugowania funkcji, ze szczególnym uwzględnieniem funkcji w wątku **stosów równoległych** okna i **czujki równoległej** okna.

 [Narzędzia debugowania wątków i procesów](../debugger/debug-threads-and-processes.md)  
 Zawiera listę funkcji, narzędzi debugowania wątków i procesów.  
  
 [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)  
 Wyjaśniono, jak można debugować wielu procesów.

 [Wskazówki: Debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md).  
 Wskazówki, która przedstawia sposób użycia **wątków** okna i **debugowania lokalizacji** paska narzędzi. 

 [Wskazówki: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Wskazówki, która przedstawia sposób użycia **stosów równoległych** i **zadania** systemu windows.  
  
 [Porady: przełączanie na inny wątek podczas debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Trzy sposoby przełączyć kontekst debugowania do innego wątku.  
  
 [Porady: Oflagowanie i usuwanie oflagowania wątków](../debugger/how-to-flag-and-unflag-threads.md)  
 Znak lub flagi wątków, które chcesz zwracać szczególną uwagę podczas debugowania.    
  
 [Porady: debugowanie w klastrze wysokiej wydajności](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Techniki do debugowania aplikacji, która działa w klastrze wysokiej wydajności.  

 [Wskazówki dotyczące debugowanie wątków w kodzie natywnym](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Proste techniki, które mogą być przydatne w przypadku debugowania natywnego wątków. 

 [Porady: Ustawianie nazw wątków w kodzie natywnym](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Nadaj nazwę, którą można wyświetlić w Twojej wątku **wątków** okna.  
  
 [Porady: Ustawianie nazw wątków w kodzie zarządzanym](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Nadaj nazwę, którą można wyświetlić w Twojej wątku **wątków** okna. 
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)

 - Użyj warunków punktu przerwania lub filtrów, jeśli chcesz debugować poszczególnych wątku.  
  
 - Tracepoints włączyć do śledzenia realizacji programu bez podziału. Może to być przydatne w przypadku badania problemów, takich jak zakleszczenia.  
  
 [Wątkowość](/dotnet/standard/threading/index)  
 Wątkowość pojęcia związane z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] programowania, w tym przykładzie kodu.  
  
 [Wielowątkowość składników](http://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
 Jak używać wielowątkowości w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] składników.  
  
 [Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](/cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 Wątkowość pojęcia i przykładowy kod dla programistów języka C++ za pomocą MFC.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie wątków i procesów](../debugger/debug-threads-and-processes.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)