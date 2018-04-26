---
title: Jednostka testowania w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ea1d186f280c41d5330b3860f5b0802fb001bf84
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="unit-test-your-code"></a>Kod testu jednostkowego

Testy jednostkowe nadaj deweloperów i testerów szybko wyszukać błędy logikę w metod klas w projektów C#, Visual Basic i C++.

Narzędzia do testów jednostkowych obejmują:

* **Testowanie Explorer**&mdash;można uruchomić testów jednostkowych i wyświetlać ich wyniki w **Eksploratora testów**. Można użyć dowolnego frameworka testów jednostkowych, w tym framework innych firm, zawierający kartę dla **Eksploratora testów**.

* **Framework testów jednostkowych firmy Microsoft dla kodu zarządzanego**&mdash;frameworka testów jednostkowych Microsoft dla kodu zarządzanego jest zainstalowany program Visual Studio i zapewnia platformę do testowania kodu platformy .NET.

* **Framework testów jednostkowych firmy Microsoft dla języka C++**&mdash;frameworka testów jednostkowych Microsoft dla języka C++ jest instalowane jako część **tworzenia klasycznych aplikacji w języku C++** obciążenia. Zapewnia to struktura do testowania kodu natywnego. Uwzględniane są również testu Google, Boost.Test i CTest struktury i karty innych firm są dostępne dla platform dodatkowych testów. Aby uzyskać więcej informacji, zobacz [pisania testów jednostkowych dla C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Narzędzia pokrycia kodu**&mdash;można określić ilość kod produktu, że urządzenia testów wykonywania polecenia w Eksploratorze testów.

* **Microsoft Fakes izolacji framework**&mdash;można tworzyć w ramach izolacji substytutów Microsoft zastępuje klasy i metody dla kodu produkcyjnego i systemu, które utworzyć zależności w kodzie w ramach testu. Poprzez implementowanie fałszywych delegatów dla funkcji kontroluje się zachowanie i dane wyjściowe obiektu zależności.

Można również użyć [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) do eksplorowania kodu .NET do generowania danych testowych i zestaw testów jednostkowych. Dla każdej instrukcji w kodzie, jest generowany wprowadzania testu który wykona tej instrukcji. Analizy przypadków jest wykonywane dla każdego gałąź warunkowa w kodzie.

## <a name="key-tasks"></a>Główne zadania

Należy skorzystać z następujących tematów, aby lepiej zrozumieć i z łatwością tworzyć testy jednostkowe:

|Zadania|Skojarzone tematy|
|-----------|-----------------------|
|**Szybki Start i wskazówki:** Użyj następujących tematach, aby dowiedzieć się testowania w programie Visual Studio z przykładów kodu jednostek.|-   [Wskazówki: Tworzenie i Uruchamianie testów jednostkowych zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Szybki Start: Test-driven programowanie za pomocą narzędzia Eksplorator testów](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)|
|**Testy jednostkowe za pomocą narzędzia Eksplorator testów:** Dowiedz się, jak narzędzia Eksplorator testów mogą pomóc tworzyć bardziej wydajnie i efektywnie testów jednostkowych.|-   [Teście jednostkowym](../test/unit-test-basics.md)<br />-   [Tworzenie projektu testu jednostki](../test/create-a-unit-test-project.md)<br />-   [Uruchom testy jednostkowe za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)<br />-   [Instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)|
|**Testy jednostkowe kodu zarządzanego:**|-   [Pisanie testów jednostkowych dla .NET Framework za pomocą Frameworka testów jednostkowych Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**Kod w języku C++ testy jednostkowe**|-   [Pisanie testów jednostkowych dla C/C++ Framework testów jednostkowych Microsoft dla języka C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**Izolowanie testów jednostkowych**|-   [Izolowanie testowanego pomocą struktury Microsoft Fakes kodu](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Umożliwia zidentyfikowanie, jaka część kodu projektu został przetestowany przez pokrycia kodu:** Dowiedz się więcej na temat funkcji pokrycia kodu programu Visual Studio, narzędzia do testowania.|-   [Korzystanie z pokrycia kodu do określenia, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Wykonywać analizy wydajności i obciążenia za pomocą testów obciążenia:** można tworzyć testu obciążenia i Dodaj testy jednostkowe do niej zdiagnozować wydajności i podkreślają problemy w aplikacji.|-   [Obciążenia testowania (VSTS i TFS)](/vsts/load-test/)|
|**Ustaw bramki jakości:** można utworzyć bramki jakości do wymuszania, że testy są uruchamiane przed kodu jest zaewidencjonowany, aby pomóc w zapewnieniu jakości kodu.|-   [Zasady ewidencjonowania (VSTS)](/vsts/tfvc/add-check-policies)|
|**Ustawianie opcji testowania:** na przykład określić, gdzie są przechowywane wyniki testu.|[Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Dokumentacji interfejsu API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> w tym artykule opisano UnitTesting przestrzeni nazw, co zapewnia potwierdzeń atrybuty, wyjątki, i inne klasy w tym testy jednostkowe pomocy technicznej.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> w tym artykule opisano przestrzeni UnitTesting.Web rozszerza przestrzeni nazw UnitTesting przez zapewnienie wsparcia dla testów jednostkowych usługi sieci Web i program ASP.NET.

## <a name="see-also"></a>Zobacz także

- [Podnoszenie jakości kodu](/visualstudio/test/improve-code-quality)
