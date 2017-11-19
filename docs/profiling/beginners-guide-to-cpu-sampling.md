---
title: "Przewodnik dla początkujących próbkowania Procesora w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords: vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- performance tools, wizard
- Performance Wizard
ms.assetid: 85161cc4-18ee-49b3-9487-33680e687597
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a13701dd85cfc2339650ec2df641ac1f5f15e75f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="beginners-guide-to-cpu-sampling"></a>Przewodnik dla początkujących próbkowanie Procesora
Visual Studio, narzędzia profilowania służy do analizowania problemów z wydajnością w aplikacji. Ta procedura przedstawia sposób użycia **próbkowania** danych.

> [!NOTE]
>  Zalecane jest użycie [użycie procesora CPU](../profiling/beginners-guide-to-performance-profiling.md) narzędzia w oknie narzędzia diagnostyczne zamiast starszej wersji narzędzia próbkowanie Procesora, chyba że potrzebne specjalne funkcje takie jak obsługa instrumentacji.
  
 **Próbkowanie** jest statystyczne metody profilowania, która pokazuje funkcje, które robią większość trybu użytkownika działać w aplikacji. Próbkowanie to dobre miejsce na start do wyszukania obszarów, aby przyspieszyć działanie aplikacji.  
  
 W określonych odstępach czasu **próbkowania** metody zbiera informacje o funkcjach, które są wykonywane w aplikacji. Po zakończeniu uruchom profilowanie **Podsumowanie** widok profilowania dane zostaną wyświetlone Najaktywniejsze drzewo wywołań funkcji o nazwie **aktywnej ścieżki**, gdzie większość pracy w aplikacji zostało wykonane. Widok również zawiera listę funkcji, które zostały wykonywania najwięcej indywidualnej pracy, a także wykres osi czasu, którym można skupić się na poszczególnych segmentów sesji próbkowania.  
  
 Jeśli **próbkowania** nie zapewnia dane, które chcesz dodać, inne profilowania metody kolekcji narzędzia udostępniają różne rodzaje informacji, które mogą być przydatne do Ciebie. Aby uzyskać więcej informacji o tych innych metod, zobacz [porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md).  
  
> [!TIP]
>  Jeśli profil jest kod, który wywołuje funkcje systemu Windows, należy upewnić się, czy masz najnowsze pliki PDB. Bez tych plików widoków raportu spowoduje wyświetlenie listy nazw funkcji systemu Windows, które są trudne do zrozumienia i są one niezrozumiałe. Aby uzyskać więcej informacji o sposobie upewnij się, że pliki potrzebne, zobacz [porady: Symbol Windows informacje](../profiling/how-to-reference-windows-symbol-information.md).  
  
##  <a name="Step1"></a>Tworzenie i uruchamianie sesji wydajności  
 Aby pobrać dane, które należy przeanalizować, należy najpierw utworzyć sesję wydajności, a następnie uruchom sesję. **Kreatora osiągów** pozwala wykonać obie czynności.  
  
 Jeśli to nie profilowanie aplikacji klasycznej systemu Windows lub aplikacji ASP.NET, należy użyć jednego z innych narzędzi do profilowania. Zobacz [narzędzia profilowania](../profiling/profiling-tools.md).  
  
#### <a name="to-create-and-run-a-performance-session"></a>Aby utworzyć i uruchomić sesję wydajności  
  
1.  Otwórz rozwiązanie w programie Visual Studio. Ustawienie konfiguracji do zlecenia. (Znajdź **konfiguracje rozwiązania** na pasku narzędzi, która jest ustawiona na **debugowania** domyślnie. Zmień, aby **wersji**.)  
  
    > [!IMPORTANT]
    >  Jeśli nie jesteś administratorem na komputerze, którego używasz, należy uruchomić program Visual Studio jako administrator, podczas używania profilera. (Kliknij prawym przyciskiem myszy ikonę aplikacji programu Visual Studio, a następnie kliknij przycisk **Uruchom jako administrator**.  
  
2.  Na **debugowania** menu, wybierz opcję **profilera**, a następnie wybierz **wydajności programu profilującego**.  
  
3.  Sprawdź **kreatora osiągów** opcji, a następnie kliknij przycisk **Start**.  
  
4.  Sprawdź **próbkowania procesora CPU (zalecane)** opcję i kliknij przycisk **Zakończ**.  
  
5.  Uruchamia aplikację i uruchamia profilera do zbierania danych.  
  
6.  Wykonuje funkcje, które mogą zawierać problemy z wydajnością.  
  
7.  Zamknij aplikację w zwykły sposób.  
  
     Po zakończeniu działania aplikacji, **Podsumowanie** widok danych profilowania pojawia się w oknie głównym programu Visual Studio i ikona dla nowej sesji w **Eksplorator wydajności** okna.  
  
##  <a name="Step2"></a>Krok 2: Analizowanie danych próbkowania  
 Po zakończeniu pracy sesję wydajności **Podsumowanie** widok raportu profilowania pojawia się w oknie głównym w programie Visual Studio.  
  
 Zalecamy rozpocząć analizowanie danych, sprawdzając **aktywnej ścieżki** , a następnie na liście funkcji wykonywania najbardziej pracy i na koniec przez koncentrujących się na inne funkcje za pomocą **osi czasu Podsumowanie** . Można również wyświetlić profilowania sugestie i ostrzeżeń w **listy błędów** okna.  
  
 Należy pamiętać, że metoda pobierania próbek może nie można uzyskać informacje potrzebne. Na przykład próbki są zbierane tylko wtedy, gdy aplikacja jest wykonywany kod trybu użytkownika. W związku z tym niektóre funkcje, takie jak operacje wejścia i wyjścia, nie przechwytuje próbkowania. Narzędzia profilowania zapewniają kilka metod kolekcji, które pozwala skupić się na ważnych danych. Aby uzyskać więcej informacji na temat innych metod, zobacz [porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md).  
  
 Poszczególnych numerowane obszar na ilustracji odnosi się do kroku w procedurze.  
  
 ![Wyświetl raport z podsumowaniem do próbkowania](../profiling/media/summary_sampling.png "Summary_Sampling")  
  
#### <a name="to-analyze-sampling-data"></a>Do analizowania danych próbkowania  
  
1.  W **Podsumowanie** widoku **aktywnej ścieżki** pokazuje gałęzi drzewo wywołań aplikacji z najwyższym przykłady włącznie. Jest to ścieżka wykonywania, który był aktywny najbardziej podczas zbierania danych. Wysokiej wartości z wartościami granicznymi może wskazywać, algorytm generuje drzewo wywołań mogą być optymalizowane. Znajdź funkcji w kodzie najniższe w ścieżce. Należy zauważyć, że ścieżka mogą również obejmować lub funkcji systemu w modułach zewnętrznych.  
  
     ![Aktywnej ścieżki profilera](../profiling/media/profiler_hotpath.png "Profiler_HotPath")  
  
    1.  **Przykłady z wartościami granicznymi** wskazuje ilość pracy została wykonana przez funkcję i wszystkie funkcje wywoływane przez go. Wysoka liczba włącznie wskaż funkcje, które są najbardziej kosztownych ogólne.  
  
    2.  **Wyłącznych próbek** wskazuje ilość pracy została wykonana przez kod w treści funkcji, z wyłączeniem pracy wykonanej przez funkcje, które zostały wywołane przez nią. Wysoka liczba wyłącznego może wskazywać wąskie gardło w samej funkcji.  
  
2.  Kliknij nazwę funkcji, aby wyświetlić **szczegółów funkcji** widoku danych profilowania. **Szczegółów funkcji** widoku przedstawia widoku graficznego elementów danych profilowania dla wybranej funkcji wyświetlane wszystkie funkcje, które wywołuje się, że funkcja i wszystkie funkcje, które zostały wywołane przez wybranej funkcji.  
  
    -   Rozmiar bloków funkcji wywołującego i o nazwie stanowią względną częstotliwość funkcji o nazwie lub były nazywane.  
  
    -   Można kliknąć nazwę telefonicznej lub wywołał funkcję, aby była wybranej funkcji Widok szczegółów funkcji.  
  
    -   W dolnym okienku **szczegółów funkcji** system windows wyświetli kodu funkcji. Jeśli Sprawdź kod i znaleźć możliwość zoptymalizować jego wydajność, kliknij nazwę pliku źródłowego, aby otworzyć go w edytorze programu Visual Studio.  
  
3.  Aby kontynuować analizę, wróć do **Podsumowanie** widoku, wybierając **Podsumowanie** z listy rozwijanej widoku. Sprawdź funkcje w **funkcje wykonujące najwięcej indywidualnej pracy**. Lista funkcji o najwyższym wyłącznych próbek. Kod w treści funkcji tych funkcji wykonywane wiele pracy oraz można zoptymalizować go. Dodatkowo analizować określonej funkcji, kliknij nazwę funkcji, aby wyświetlić je w **szczegółów funkcji** widoku.  
  
     ![Lista funkcje wykonujące najwięcej pracy](../profiling/media/functions_mostwork.png "Functions_MostWork")  
  
     Kontynuowanie badaniu profilowania Uruchom możesz można Analizuj ponownie segment dane profilowania za pomocą osi czasu w **Podsumowanie** widok do pokazania **aktywnej ścieżki** i **funkcji Wykonanie najwięcej indywidualnej pracy** z wybranego segmentu. Na przykład koncentrujących się na mniejsze szczytu na osi czasu może ujawnić drzewa wywołań kosztowne i funkcje, które nie zostały wyświetlone w analizy całego przebiegu profilowania.  
  
     Aby Analizuj ponownie segmentu, wybierz segment, w polu podsumowania osi czasu, a następnie kliknij przycisk **Filtruj według wyboru**.  
  
     ![Oś czasu widoku podsumowania wydajności](../profiling/media/performancesummary.png "PerformanceSummary")  
  
4.  Profiler używa również zestaw reguł sugerowanie sposobów poprawy przebiegu profilowania i zidentyfikować problemy wydajność. W przypadku znalezienia problemu, wyświetlane jest ostrzeżenie **listy błędów** okna. Aby otworzyć **listy błędów** okna na **widoku** kliknij menu **listy błędów**.  
  
    -   Aby wyświetlić funkcja, która wywołała ostrzeżenie **szczegółów funkcji** wyświetlić, kliknij dwukrotnie to ostrzeżenie.  
  
    -   Aby wyświetlić szczegółowe informacje na temat tego ostrzeżenia, kliknij prawym przyciskiem myszy błąd, a następnie kliknij przycisk **Pokaż błąd pomóc**  
  
##  <a name="Step3"></a>Krok 3: Korygowanie kodu i uruchom ponownie sesję  
 Po znaleźć i zoptymalizować jedną lub więcej funkcji, można powtórzyć przebiegu profilowania i porównywania danych, aby wyświetlić tą różnicą, że zmiany zostały wprowadzone na wydajność aplikacji.  
  
#### <a name="to-revise-code-and-rerun-the-profiler"></a>Aby poprawić kod i ponownie uruchom profilera  
  
1.  Zmień swój kod.  
  
2.  Aby otworzyć **Eksplorator wydajności**na **debugowania** kliknij menu **profilera**, następnie **Eksplorator wydajności** , a następnie kliknij przycisk **Pokaż Eksplorator wydajności**.  
  
3.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesji, który chcesz ponownie uruchomić, a następnie kliknij przycisk **uruchomienie z profilowania.**  
  
4.  Po ponownym uruchomieniu sesji inny plik danych jest dodawany do **raporty** folderu dla sesji w **Eksplorator wydajności**. Wybierz oba oryginalny i profilowanie nowych danych, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij przycisk **raporty porównanie wydajności**.  
  
     Otwiera nowe okno raportu, wyświetlania wyników porównania. Aby uzyskać więcej informacji o sposobie używania Widok porównania, zobacz [porady: porównywanie plików danych wydajności](../profiling/how-to-compare-performance-data-files.md).
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)   
 [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)   
 [Omówienie](../profiling/overviews-performance-tools.md)  
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przegląd funkcji profilowania](../profiling/profiling-feature-tour.md)