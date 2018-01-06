---
title: "Sesja wydajności — omówienie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4996f6cd60889412958765a02811b1b6728f2efa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="performance-session-overview"></a>Sesja wydajności — Omówienie
W tym omówieniu przedstawiono podstawowe profilowania. Deweloperzy, którzy dopiero zaczynasz korzystać z wydajności pracy zostanie wyświetlony jak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania pomoże im szybko stać się wydajność i zwiększyć wydajność ich kodu. Deweloperzy, którzy są w profilowania można zapoznać się z określonych funkcji w narzędziach profilowania i procesów.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Narzędzia profilowania pomagają zidentyfikować problemy z wydajnością w kodzie źródłowym i porównywać możliwych rozwiązań. Profilowanie kreatorów narzędzia i ustawienia domyślne umożliwiają błyskawiczny wgląd w wiele problemów z wydajnością. Funkcje i opcje narzędzi profilowania należy podać dokładną kontrolę nad procesem profilowania. Ten formant obejmuje dokładne wartości docelowej sekcji kodu, zbierania informacji na poziomie bloku i włączenia dodatkowe dane dotyczące wydajności procesora i systemu w danych.  
  
 Poniższe kroki tworzą podstawowego procesu za pomocą narzędzi profilowania:  
  
1.  Konfigurowanie sesji wydajności, określając metod gromadzenia danych i dane, które mają być zbierane.  
  
2.  Zbierz dane profilowania, uruchamiając aplikację w sesji wydajności.  
  
3.  Analizowanie danych, aby zidentyfikować problem z wydajnością.  
  
4.  Zmodyfikuj kod w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) do zwiększa wydajność aplikacji, kodu  
  
5.  Zbierania danych profilowania kodu zmienione, a następnie porównaj dane profilowania oryginalnego i zmiany danych.  
  
6.  Generowanie raportu, który dokumentów wzrost wydajności.  
  
 Aby pracować z informacjami pochodzącymi profilowania, powinien mieć informacji o symbolach dla danych binarnych, które mają być profilu i plików binarnych systemu operacyjnego Windows.  
  
## <a name="configure-the-performance-session"></a>Konfigurowanie sesji wydajności  
 Aby skonfigurować sesję profilowania, wybierz metodę profilowania, którego chcesz używać i dane, które mają być zbierane. Narzędzia profilowania **kreatora osiągów** można przeprowadzenia konfiguracji podstawowej, a następnie można użyć strony właściwości sesji wydajności, można dodać więcej opcji:  
  
-   Metody profilowania to próbkowania, śledzenia i alokacji pamięci.  
  
-   Wartości danych to czas procesora i liczniki wydajności systemu operacyjnego i zdarzeń aplikacji, takich jak błędów stron i przejścia jądra.  
  
 Możesz skonfigurować sesję wydajności w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu w ramach rozwiązania projektu lub dowolnego plików binarnych za pomocą profilu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Możesz określić właściwości sesji na stronach właściwości sesji wydajności lub można użyć Kreatora profilowania.  
  
## <a name="collect-profiling-data"></a>Zbieranie danych profilowania  
 Uruchom zbieranie danych z profilowania **Eksplorator wydajności**. Możesz wstrzymać i wznowić profilowanie, aby ograniczyć ilość zbieranych danych. Można także dołączyć do procesu, który jest już uruchomiony.  
  
 Zaraz po uruchomieniu aplikacji **kontroli zbierania danych** okno jest wyświetlane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Z **kontroli zbierania danych** okna, można profilu określonej części aplikacji przez wstrzymywanie i wznawianie procesu zbierania. Można również użyć **kontroli zbierania danych** okno, aby wstawić znaki do zbieranych danych. Znaczniki są punkty danych zdefiniowane przez użytkownika, które są wyświetlane w widokach profilu i który może służyć do filtrowania danych profilowania.  
  
 Podczas zamykania aplikacji docelowej, narzędzi profilowania generuje plik danych profilowania (*.vsp) i wyświetla widok raport z podsumowaniem w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.  
  
## <a name="analyze-the-data-and-identify-performance-issues"></a>Analizowanie danych i zidentyfikować problemy z wydajnością  
 Po zakończeniu przebiegu profilowania, dane są analizowane i w narzędziach profilowania zostanie wyświetlone podsumowanie **raport wydajności** wyświetlić systemu windows. Dane profilowania są zbierane dla stosu wywołań i pojedynczych funkcji w aplikacji docelowej. Raport analizy wydajności zakresy danych procesy, wątki, modułów, funkcje i wierszy kodu źródłowego aplikacji wyświetlanie widoków. Dane profilowania dla funkcji są następujące wartości:  
  
-   Całkowity czas przeznaczony w funkcji i funkcji podrzędnych, które zostały wywołane przez funkcję (wartości z wartościami granicznymi).  
  
-   Czas, jaki był poświęcony na wykonywanie tylko kod w funkcji (wyłączne wartości).  
  
 Ponad dwanaście różne widoki umożliwia analizowanie danych profilowania w najbardziej wydajny sposób. Dostosowywanie widoku umożliwiają filtrowanie i sortowanie danych znajdują się funkcje, które mogą być przyczyną problemów z wydajnością. Filtrowanie gorących ścieżka zawiera wyróżnianie Najaktywniejsze ścieżek w widokach drzewa wywołań i modułu.  
  
## <a name="modify-the-application-code"></a>Modyfikowanie kodu aplikacji  
 Po wykrycia co najmniej jeden problem odpowiednich wydajności, należy zmodyfikować kod przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, a następnie zbieranie danych zmiany profilowania.  
  
## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Zbieranie danych profilowania ponownie i porównywania danych między działa profilowania  
 Porównanie narzędzi profilowania widoku raportu wyświetla różnicę w module, funkcji lub wydajności linii między dwoma wybranych plików danych profilowania. Można określić profilowania wartości danych, które chcesz porównać i można przełączać się między Widok porównania i widoki poszczególnych plików.  
  
## <a name="generate-a-report-of-the-results"></a>Generowanie raportu dotyczącego wyników  
 Wiersze każdego widoku raportu wydajności można wkleić do wiadomości e-mail i arkusze kalkulacyjne i możesz generować raporty zawierające dane dla co najmniej jeden widok.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Wskazówki: Identyfikowanie problemów z wydajnością](../profiling/walkthrough-identifying-performance-problems.md)