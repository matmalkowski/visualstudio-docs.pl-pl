---
title: "Przegląd raportu wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
caps.latest.revision: "45"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 915f7f3cbbee87f72c4643b8c5a2b4497bbd69dd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="performance-report-overview"></a>Przegląd raportu wydajności
Można wyświetlić danych profilowania w sesji wydajności **raport wydajności** okno programu Visual Studio Team System programowanie Edition zintegrowane środowisko programistyczne (IDE). Dane profilowania jest zapisywany w pliku Vsp i vsps plików. Podgląd raportów umożliwiają przeglądać i analizować problemy z wydajnością aplikacji.  
  
> [!CAUTION]
>  Plik danych profilowania zawiera poufne informacje, takie jak nazwa komputera, wersja systemu operacyjnego, ścieżki do pliku informacji o pamięci i innych informacji o instalacji na komputerze. Należy zachować ścisłą kontrolę nad dystrybucją danych, w formacie native plik Vsp i eksportowanych do pliku CSV lub plik XML.  
>   
>  Jeśli dane śledzenia zdarzeń są zbierane w ramach sesji wydajności, dodatkowe informacje mogą być wyświetlane zdarzeń śledzenia plik dziennika (ETL). Te informacje obejmują nazwę domeny i użytkownika; w związku z tym należy utrzymywać ścisłą kontrolę nad dystrybucji pliku dziennika.  
  
## <a name="performance-report-window"></a>Okno raportu wydajności  
 Okno Raport wydajności jest okna narzędzia, która jest używana do wyświetlania, zarządzania i filtrowanie danych wydajności, a także formantu można dostosowywać zapytania.  
  
 Na głównym pasku narzędzi okna Raport o wydajności można uzyskać dostępu do każdego widoku. Kliknij strzałkę obok pozycji **bieżący widok** listy do wyświetlania i wybierania poszczególnych widoków, które są dostępne.  
  
 Okno Raport wydajności zawiera następujące widoki danych:  
  
### <a name="summary-view"></a>Widok podsumowania  
 Domyślnie dane profilowania jest wyświetlany w widoku podsumowania. Ten widok stanowi punkt wyjścia w badaniu na problemy z wydajnością. Z każdego wiersza w widoku podsumowania można przenieść do bardziej szczegółowych widoków klikając prawym przyciskiem myszy nazwę funkcji lub modułu. Aby uzyskać więcej informacji, zobacz [widoku podsumowania](../profiling/summary-view.md).  
  
### <a name="callercallee-view"></a>Widok wywołujący/wywoływany  
 Widok wywołujący/wywoływany Wyświetla drzewo wywołań dla poszczególnych funkcji. Widok jest podzielone na trzy części:  
  
-   Funkcja docelowego jest wyświetlany w środku widoku.  
  
-   Funkcje, które wywołuje funkcję (obiekty wywołujące) są wyświetlane powyżej funkcja docelowej.  
  
-   Funkcje, które są wywoływane przez funkcję docelowego (callees) są wyświetlane poniżej wartości docelowej.  
  
 Aby wybrać inną funkcję, możesz kliknąć dwukrotnie dowolnej funkcji o nazwie liście lub lista wywoływany. Aby uzyskać więcej informacji, zobacz [widok wywołujący/wywoływany](../profiling/caller-callee-view.md).  
  
### <a name="call-tree-view"></a>Widok drzewa wywołań  
 Widok drzewa wywołań Wyświetla ścieżek wykonywania funkcji, które zostały przechodzić w profilowanych aplikacji. Korzeń drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcja zawiera wszystkie funkcje, które mu i dane wydajności dotyczące tych wywołań funkcji.  
  
 Widok drzewa wywołań można rozwinąć i wyróżnij ścieżkę wykonywania funkcji wykorzystany najwięcej czasu lub zostało pobrane najczęściej. Aby wyświetlić najbardziej aktywne ścieżki, kliknij prawym przyciskiem myszy funkcji, a następnie kliknij przycisk **rozwiń aktywnej ścieżki**. Aby uzyskać więcej informacji, zobacz [widok drzewa wywołań](../profiling/call-tree-view.md).  
  
### <a name="process-view"></a>Widok procesu  
 Widok procesu przedstawia dane wydajności dla każdego procesu i wątku, który został profilowaniu. Aby uzyskać więcej informacji, zobacz [widok procesu](../profiling/process-view.md).  
  
### <a name="modules-view"></a>Widok modułów  
 Widok modułów Wyświetla listę modułów w projekcie i przedstawia dane profilowania dla każdego modułu. Rozwiń lub Zwiń nazwę modułu, aby wyświetlić dane profilowania funkcji. Podczas zbierania danych za pomocą metody pobierania próbek, źródła kodu wiersza i instrukcji wskaźnika danych profilowania jest również dostępna. Aby uzyskać więcej informacji, zobacz [widok modułów](../profiling/modules-view.md).  
  
### <a name="functions-view"></a>Widok funkcji  
 Widok funkcji zawiera listę funkcji, które zostały wywołane podczas profilowania. Aby uzyskać więcej informacji, zobacz [widoku funkcji](../profiling/functions-view.md).  
  
### <a name="line-view"></a>Widok wiersza  
 Widok linii umożliwia wyświetlenie wierszy kodu określone źródło, które zostały wykonane podczas profilowania próbkowania. Aby uzyskać więcej informacji, zobacz [widok linii](../profiling/lines-view.md).  
  
### <a name="instruction-pointer-ip-view"></a>Widok wskaźnika (IP) instrukcji  
 Widok wskaźnika instrukcji można wyświetlić szczegółowe instrukcje, które zostały wykonane podczas profilowania próbkowania. Aby uzyskać więcej informacji, zobacz [widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view.md).  
  
### <a name="allocation-view"></a>Widok alokacji  
 Widok alokacji jest dostępny jeśli **zbieranie .NET obiektu alokacji** został wybrany na **ogólne** strony **sesji wydajności** okno dialogowe właściwości. Zobacz [sesja wydajności — omówienie](../profiling/performance-session-overview.md). Widok alokacji wyszczególniono obiekty .NET przydzielone przez aplikację lub składnik. Po rozwinięciu wiersza obiektu jest wyświetlany drzewo wywołań. Drzewo wywołań pokazuje ścieżek wykonywania, które spowodowało utworzenie obiektu. Są także informacje o liczbę włącznie i wyłącznego alokacji dla każdej funkcji w drzewie wywołań. Widok alokacji można rozwinąć i wyróżnij ścieżkę wykonywania funkcji, które przydzielone największej liczby obiektów. Aby wyświetlić najbardziej aktywne ścieżki, kliknij prawym przyciskiem myszy funkcji, a następnie kliknij przycisk **rozwiń aktywnej ścieżki**. Aby uzyskać więcej informacji, zobacz [zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) i [Widok alokacji](../profiling/dotnet-memory-allocations-view.md).  
  
### <a name="objects-lifetime-view"></a>Widok okresu istnienia obiektów  
 Widok okresu istnienia obiektu jest dostępna jeśli **.NET zbierać informacje dotyczące alokacji obiektów** i **również zbierać informacje dotyczące okresu istnienia obiektu platformy .NET** zostały wybrane na **ogólne**strony **sesji wydajności** okno dialogowe właściwości.  
  
 Widok okresu istnienia obiektu wyświetla całkowita liczba wystąpień poszczególnych typów i liczbę obiektów, które zostały zebrane podczas generowania kolekcji każdego pamięci. Aby uzyskać więcej informacji, zobacz [widok okresu istnienia obiektu](../profiling/object-lifetime-view.md).  
  
## <a name="customizable-filter-control"></a>Formant filtru dostosowania  
 Formant filtru można dostosowywać ma następujące opcje:  
  
-   **Importowanie filtru** -pobiera wcześniej zapisane zapytanie niestandardowe.  
  
-   **Eksportowanie filtru** -zapisuje niestandardowe zapytanie do określonej lokalizacji.  
  
-   **Wykonanie kwerendy** — uruchamia zapytania jako wyświetlanych w formancie zapytanie niestandardowe.  
  
-   **Zatrzymaj kwerendę** -zatrzymuje wykonanie zapytania, który jest uruchomiony. Ten przycisk jest niedostępny, jeśli jest uruchomiony bez określenia zapytania.  
  
-   **Pokaż kwerendy** -Pokazuje/ukrywa kontroli niestandardowe zapytania.  
  
-   **Zapisz Analyzed** -raport wraz z jego bieżącej analizy jest zapisywany jako plik vsps.  
  
-   **Eksportuj** -zapisuje w bieżącym raporcie. Sformatowany CVS lub. Pliku w formacie XML, z opcjami, aby zapisać różne widoki.  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie wydajności narzędzi danych](../profiling/analyzing-performance-tools-data.md)   
 [Widoki raportu wydajności](../profiling/performance-report-views.md)