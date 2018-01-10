---
title: "Deweloper testowanie narzędzia, scenariusze i możliwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: unit testing, create unit tests
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 0da910ddf48d0f270aa5e624628d0d6b937e9ae1
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>Deweloper testowania narzędzi, scenariusze i funkcje

Obsługa kodu kondycji z testowania jednostek. Program Visual Studio oferuje szeroką gamę zaawansowanych narzędzi i technik dla deweloperów do użycia podczas testowania aplikacji:

**Scenariusze i funkcje:**

* [Unikaj regresji i osiągnięcia pokrycia kodu z IntelliTest](#intellitest)
* [Testowanie kodowanego interfejsu użytkownika i Selenium za pomocą interfejsu użytkownika](#ui-testing)
* [Skuteczne testowanie jednostkowe na platformie pokrycia kodu w usłudze Visual Studio](#unit-testing)
* [Testy jednostkowe za pomocą dowolnej architektury przy użyciu wysokiej wydajności Eksplorator testów](#test-explorer)
* [Wprowadzenie do przeprowadzania testów jednostkowych](getting-started-with-unit-testing.md)

<a name="intellitest"></a>
## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>Unikaj regresji i osiągnięcia pokrycia kodu z IntelliTest

W tradycyjnych jednostki testów każdy przypadek testowy reprezentuje użycia przykładowy scenariusz, a potwierdzenia uwzględnić relacji między danych wejściowych i wyjściowych.  Weryfikuje, że kilka takich scenariuszy może również być wystarczająca, ale doświadczonych programistów wie usterki znajomą nawet w dobrze przetestowany kodu, gdy jest to poprawny, ale dane wejściowe zastosowaniem powodować nieprawidłowe odpowiedzi.

Zwiększenia zapotrzebowania i uniknąć regresji z IntelliTest.
IntelliTest znacznie zmniejsza nakład pracy można tworzyć i obsługiwać testów jednostkowych dla nowego lub istniejącego kodu. 

![IntelliTest w akcji](media/devtest-intellitest.png)

* [Wprowadzenie do IntelliTest w programie Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [IntelliTest — jeden Test do wszystkich reguł](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx)
* [IntelliTest wideo](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [Rozpoczynanie pracy z IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Podręcznik dotyczący funkcji IntelliTest](intellitest-manual/index.md)

<a name="ui-testing"></a>
## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Testowanie kodowanego interfejsu użytkownika i Selenium za pomocą interfejsu użytkownika

Test interfejsu użytkownika (UI) z najlepszymi rasy lub społeczności zatwierdzone testów interfejsu użytkownika.
Kodowane testy interfejsu użytkownika umożliwiają tworzenie pełni zautomatyzowanych testów w celu zweryfikowania funkcji i zachowania interfejsu użytkownika.
Ich można zautomatyzować testów interfejsu użytkownika w różnych technologii, w tym aplikacji opartych na języku XAML platformy uniwersalnej systemu Windows, aplikacje przeglądarki i aplikacje programu SharePoint.

Wybierz najlepsze rasy kodowany testów interfejsu użytkownika lub ogólnego w przeglądarce testów UI z Selenium, Visual Studio udostępnia wszystkie narzędzia, które są potrzebne. 

![Testowanie kodowanego interfejsu użytkownika za pomocą interfejsu użytkownika](media/devtest-codeduitest.png)

* [Używanie automatyzacji interfejsu użytkownika do testowania kodu](use-ui-automation-to-test-your-code.md)
* [Rozpoczynanie pracy z tworzeniem, edytowaniem i obsługa kodowanego testu interfejsu użytkownika](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Test aplikacji platformy uniwersalnej systemu Windows za pomocą kodowanych testów interfejsu użytkownika](test-windows-store-8-1-apps-with-coded-ui-tests.md)
* [Aplikacje Windows Phone testu z kodowanych testów interfejsu użytkownika](test-windows-phone-8-1-apps-with-coded-ui-tests.md)
* [Testowanie aplikacji SharePoint z kodowanych testów interfejsu użytkownika](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [Wprowadzenie do kodowanych testów interfejsu użytkownika z Visual Studio Enterprise (laboratorium)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

<a name="unit-testing"></a>
## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Skuteczne testowanie jednostkowe na platformie pokrycia kodu w usłudze Visual Studio

Aby ustalić, jaka część kodu projektu jest rzeczywiście testowane przez kodowane testy, takie jak testy jednostkowe, służy funkcja pokrycia kodu programu Visual Studio. Aby skutecznie ochronić usterki, testy należy wykonywać lub obejmuje dużą część kodu.

Analizy pokrycia kodu mogą dotyczyć zarówno kodów zarządzanych (CLI), jak i niezarządzanych (natywnych).

Pokrycie kodu jest opcją w przypadku uruchamiania metod testowych przy użyciu Eksploratora testów. Tabela wyników zawiera procent kodu, który został uruchomiony w każdym zestawie, każdej klasie i metodzie. Ponadto edytor źródła zawiera kod, który został przetestowany.

![Testu z Team Foundation Server i Visual Studio Team Services](media/devtest-codecoverage.png)

* [Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Jednostka testowania, pokrycie kodu i analizy kodu klonowania z programem Visual Studio (laboratorium)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Dostosowywanie analizy pokrycia kodu](customizing-code-coverage-analysis.md)

<a name="test-explorer"></a>
## <a name="unit-testing-with-any-framework-using-the-high-performance-test-explorer"></a>Testy jednostkowe za pomocą dowolnej architektury przy użyciu wysokiej wydajności Eksplorator testów

Przetestuj pomoc Eksploratora deweloperom tworzenia, zarządzania i uzyskać maksymalną korzyści z testowania jednostek.

![Eksplorator testów programu Visual Studio](media/devtest-testexplorer.png)

* [Rozpoczynanie pracy z testów jednostkowych](unit-test-your-code.md)
* [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md)
* [Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)
* [Instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md)

Visual Studio także i otwiera drzwi testowania kart sieciowych, takich jak NUnit i xUnit.net jednostek innych firm. Ponadto możliwość klonowania kodu przejdzie do strony dostępnych z dostarczanie oprogramowania wysokiej jakości pomaga zidentyfikować bloki kodu semantycznie podobne, co może być kandydatów do typowych poprawki lub refaktoryzacji.

![Integracja testu innych firm](media/devtest-thirdparty.png)

## <a name="see-also"></a>Zobacz także

* [Wprowadzenie do przeprowadzania testów jednostkowych](getting-started-with-unit-testing.md)
* [Przyspieszenie wykonywania testów jednostkowych w programie Team Foundation Server](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/30/speeding-up-test-execution-in-tfs.aspx)
* [Wykonywanie testu równoległe i kontekstowej jednostki](https://blogs.msdn.microsoft.com/visualstudioalm/2016/02/08/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Jednostka testowania, pokrycie kodu i analizy kodu klonowania z programem Visual Studio (laboratorium)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
