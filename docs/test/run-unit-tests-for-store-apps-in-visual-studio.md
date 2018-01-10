---
title: Uruchom testy jednostkowe dla aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: uwp
author: gewarren
ms.openlocfilehash: b1cc13dfd81876f647178ebf3702c778cabb533e
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="run-unit-tests-for-uwp-apps-in-visual-studio"></a>Uruchom testy jednostkowe dla aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio
W tym temacie opisano sposób uruchamiania testów jednostkowych za pomocą Eksploratora testów w programie Microsoft Visual Studio  
  
> [!NOTE]
>  W tematach w tej sekcji opisano funkcji programu Visual Studio Express dla systemu Windows 8. Visual Studio Community, Enterprise i Professional oferują dodatkowe funkcje, w celu przeprowadzania testów jednostkowych.  
>   
>  -   Użyj dowolnej frameworka testów jednostkowych innych firm lub Otwórz źródła adapter dodatku dla Eksploratora testów został utworzony. Można także analizować i wyświetlić informacje o pokryciu kodu dla testów.  
> -   Uruchomienia testów po każdej kompilacji. Można również użyć Microsoft Fakes framework izolacji dla kodu zarządzanego skoncentrować się testy na swoim własnym kodem podstawiając badanie kodu systemu i funkcje innych firm.  
>   
>  Aby uzyskać więcej informacji, zobacz [swój kod testu jednostkowego](../test/unit-test-your-code.md) w bibliotece MSDN.  
  
##  <a name="BKMK_In_this_topic"></a>W tym temacie  
 [Platform testów jednostkowych i projekty testowe](#BKMK_Unit_test_frameworks_and_test_projects)  
  
 [Uruchamianie testów w narzędzia Eksplorator testów](#BKMK_Running_tests_in_Test_Explorer)  
  
-   [Uruchamianie testów](#BKMK_Running_tests)  
  
 [Wyświetlanie wyników testu](#BKMK_Viewing_test_results)  
  
-   [Wyświetlanie szczegółów testu](#BKMK_Viewing_test_details)  
  
-   [Wyświetlanie kodu źródłowego metody testowej](#BKMK_Viewing_the_source_code_of_a_test_method)  
  
 [Organizowanie listy testów](#BKMK_Organizing_the_test_list)  
  
-   [Grupowanie testów](#BKMK_Grouping_tests)  
  
-   [Wyszukiwanie i filtrowanie listy testów](#BKMK_Searching_and_filtering_the_test_list)  
  
 [Debugowanie testów jednostkowych](#BKMK_Debugging_unit_tests)  
  
##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a>Platform testów jednostkowych i projekty testowe  
 Visual Studio Express dla aplikacji platformy uniwersalnej systemu Windows zawiera struktury testowania jednostki Microsoft zarządzanego i natywnego kodu C++. Eksplorator testów można uruchomić testy z wielu projektów testów w rozwiązaniu i klasy testowe, które należą do projektów kodu produkcyjnego. Projekty testowe może być dowolną kombinacją języka Visual C++ lub platform testów jednostkowych programu Visual C# i Visual Basic. Jeśli kod w ramach testu są zapisywane dla programu .NET Framework, w dowolnym języku .NET Framework, niezależnie od języka kodu docelowego można napisać projektu testowego. Natywny projektów kodu C/C++, należy sprawdzić za pomocą frameworka testów jednostkowych C++.  
  
##  <a name="BKMK_Running_tests_in_Test_Explorer"></a>Uruchamianie testów w narzędzia Eksplorator testów  
 Podczas kompilowania projektu testowego, testy są wyświetlane w Eksploratorze testów. Eksploratora testów nie jest widoczny, jeśli **testu** w menu programu Visual Studio, wybierz **systemu Windows**, a następnie wybierz pozycję **Eksploratora testów**.  
  
 ![Eksplorator testów jednostkowych](../ide/media/ute_failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  
  
 Jak uruchamiać, zapisu i ponownie uruchomić testy narzędzia Eksplorator testów wyświetla wyniki w domyślnych grup z **testy nie powiodło się**, **przekazany testy**, **pominięte testy** i  **Nie uruchamiać testów**. Możesz zmienić sposób Eksploratora testów grupy testów.  
  
 Można wykonać większość zadań znajdowanie, organizowanie i uruchamiania testów na pasku narzędzi Eksplorator testów.  
  
 ![Uruchamianie testów za pomocą narzędzi Eksploratora testów](../test/media/ute_toolbar.png "UTE_ToolBar")  
  
###  <a name="BKMK_Running_tests"></a>Uruchamianie testów  
 Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy z grupy lub zestawu testów, które można wybrać. Wykonaj jedną z następujących czynności:  
  
-   Aby uruchomić wszystkie testy w rozwiązaniu, wybierz pozycję **Uruchom wszystkie**.  
  
-   Aby uruchomić wszystkie testy w domyślnej grupy, wybierz pozycję **Uruchom...**  , a następnie wybierz grupę, w menu.  
  
-   Wybierz poszczególne testy, które chcesz uruchomić, otwórz menu skrótów dla wybranego testu, a następnie wybierz pozycję **uruchomić wybrane testy**.  
  
 Na pasku przebiegu/Niepowodzenie w górnej części okna Eksploratora testów jest animowany jako Uruchom testy. Po zakończeniu uruchomienia testu na pasku przebiegu/niepowodzenie włącza zielony wszystkie testy przekazany lub czerwony, jeśli żadnego testu nie powiodła się.  
  
##  <a name="BKMK_Viewing_test_results"></a>Wyświetlanie wyników testu  
 Jak uruchamiać, zapisu i ponownie uruchomić testy narzędzia Eksplorator testów wyświetla wyniki w grupach **testy nie powiodło się**, **przekazany testy**, **pominięte testy** i **nie działać Testy**. W okienku szczegółów w dolnej części Wyświetla Eksploratora testów Uruchom Podsumowanie testu.  
  
###  <a name="BKMK_Viewing_test_details"></a>Wyświetlanie szczegółów testu  
 Aby wyświetlić szczegółowe informacje o poszczególnych testów, wybierz testu.  
  
 W okienku szczegółów testu zawiera następujące informacje:  
  
-   Nazwa pliku źródłowego i numer wiersza metody testowej.  
  
-   Stan testu.  
  
-   Czas, który miał metody testowej do uruchomienia.  
  
 Jeśli test ma wynik negatywny, są wyświetlane również w okienku szczegółów:  
  
-   Komunikat zwrócony przez platformy testów jednostkowych dla testu.  
  
-   Ślad stosu w czasie testu nie powiodło się.  
  
###  <a name="BKMK_Viewing_the_source_code_of_a_test_method"></a>Wyświetlanie kodu źródłowego metody testowej  
 Aby wyświetlić kodu źródłowego metody testowej w edytorze programu Visual Studio, wybierz testu, a następnie wybierz **Otwórz Test** menu skrótów (klawiatury: F12).  
  
##  <a name="BKMK_Organizing_the_test_list"></a>Organizowanie listy testów  
  
###  <a name="BKMK_Grouping_tests"></a>Grupowanie testów  
 Domyślnie narzędzia Eksplorator testów są wyświetlane jako węzły podrzędne testów **testy nie powiodło się**, **przekazany testy**, **pominięte testy** i **nie Uruchom testy**.  
  
|||  
|-|-|  
|![Przycisk Eksploratora testów](../test/media/ute_groupby_btn.png "UTE_GroupBy_btn")|Do grupowania testów przez czas potrzebny na wykonanie ich, otwórz **Group By** listę i wybierz **czas trwania**. Wybierz **wynik testu** Aby przełączyć się do oryginalnej grupowania.|  
  
###  <a name="BKMK_Searching_and_filtering_the_test_list"></a>Wyszukiwanie i filtrowanie listy testów  
 Jeśli masz dużą liczbę testów, można wpisać w polu wyszukiwania Eksploratora testów, aby filtrować listę według określonego ciągu. Filtr można ograniczyć do określonych typów ciągów, wybierając z listy filtrów przed wprowadź ciąg wyszukiwania.  
  
 ![Wyszukaj filtr kategorii](../test/media/ute_searchfilter.png "UTE_SearchFilter")  
  
##  <a name="BKMK_Debugging_unit_tests"></a>Debugowanie testów jednostkowych  
 Aby rozpocząć sesję debugowania dla testów, można użyć narzędzia Eksplorator testów. Krokowe wykonywanie kodu z debuger programu Visual Studio bezproblemowe przejście i z powrotem między testów jednostkowych i projektu w ramach testu. Można rozpocząć debugowania:  
  
1.  W edytorze programu Visual Studio należy ustawić punkt przerwania w metody testowe, które chcesz debugować.  
  
    > [!NOTE]
    >  Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustaw punkty przerwania w wszystkie metody testowe, które chcesz debugować.  
  
2.  W Eksploratorze testów, wybierz metody testowe, a następnie wybierz **Debuguj zaznaczone testy** menu skrótów.  
  
 Aby uzyskać więcej informacji o debugera, zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md).
