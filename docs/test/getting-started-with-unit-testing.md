---
title: Rozpoczynanie pracy z jednostką testowania w programie Visual Studio
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 302dc958892fb79e93ed87d515c1a5b1ac3c5aab
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="get-started-with-unit-testing"></a>Wprowadzenie do przeprowadzania testów jednostkowych

Definiowanie i Uruchamianie testów jednostek do obsługi kondycji kodu, upewnij się, pokrycie kodu, a także znalezienia błędów i błędy, zanim klienci za pomocą programu Visual Studio.

## <a name="create-unit-tests"></a>Tworzenie testów jednostkowych

Utwórz testy jednostkowe i uruchom je często, aby upewnić się, że kod działa prawidłowo.

1. Tworzenie projektu testu jednostki.

   ![Dodaj jednostkowy projekt testowy do rozwiązania](media/createunittest1.png)

1. Nazwa projektu.

   ![Szablon projektu testu jednostki](media/createunittest2.png)

   Projekt zostanie dodany do rozwiązania.

   ![Jednostkowy projekt testowy w Eksploratorze rozwiązań](media/createunittest5.png)

1. W jednostkowy projekt testowy Dodaj odwołanie do projektu, który ma zostać przetestowana.

   ![Dodaj odwołanie do projektu testu jednostki](media/createunittest6.png)

1. Wybierz projekt, który zawiera kod, który będzie testu.

   ![Wybierz odwołanie do dodania](media/createunittest7.png)

1. Kod testu jednostki.

   ![Dodaj kod, aby z testu jednostkowego](media/createunittest8.png)

Można również utworzyć testu jednostkowego klas zastępczych metody z **tworzenia testów jednostkowych** [polecenia](create-unit-tests-menu.md).

![Za pomocą polecenia Create testy jednostkowe](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Uruchom testy jednostkowe

1. Otwórz Eksploratora testów.

   ![W menu Test Otwórz Eksplorator testów](media/rununittest1.png)

1. Uruchom testy jednostkowe.

   ![Uruchom testy jednostkowe w narzędzia Eksplorator testów](media/rununittest2.png)

   Można zauważyć, że jednostka testów, które przekazany lub Niepowodzenie w Eksploratorze testów.

   ![Przejrzyj wyniki testów jednostkowych w Eksploratorze testów](media/rununittest3.png)

## <a name="view-live-unit-test-results"></a>Wyświetlanie wyników testu jednostki na żywo

Jeśli używasz MSTest, xUnit lub NUnit framework testowych w Visual Studio 2017 lub nowszej widoczny na żywo wyniki testów jednostkowych.

> [!NOTE]
> Testy jednostkowe na żywo jest tylko dostępne w programie Visual Studio 2017 Enterprise Edition.

1. Włącz testy z jednostkowe na żywo **testu** menu.

   ![Włącz testy jednostkowe na żywo](media/live-test-results-start.png)

1. W oknie edytora kodu należy wyświetlić wyniki testów, jak zapisać i Edycja kodu.

   ![Wyświetl wyniki testów](media/live-test-results-ui.png)

1. Wybierz test wskaźniki wyników, aby uzyskać więcej informacji.

   ![Wybierz wskaźniki wyników testu](media/live-test-results-details.png)

Aby uzyskać więcej informacji, zobacz [testy jednostkowe na żywo](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generowanie testów jednostkowych z IntelliTest

Po uruchomieniu IntelliTest, można łatwo Zobacz które testy kończą się niepowodzeniem i Dodaj wszelkie niezbędne kod, aby je naprawić. Można wybrać, które wygenerowane testy do zapisania do projektu testowego, aby zapewnić mechanizm regresji. Jak zmienić swój kod, należy ponownie uruchomić IntelliTest, aby zachować synchronizację ze zmianami kodu wygenerowane testy. Aby dowiedzieć się więcej, zobacz temat [Generowanie testów jednostek dla kodu za pomocą IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

![Generowanie testów jednostkowych z IntelliTest](media/intellitest.png)

## <a name="run-unit-tests-with-test-explorer"></a>Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów

Użyj Eksploratora testów do uruchamiania testów jednostkowych programu Visual Studio lub projektów testów jednostkowych innych firm, grupowanie testów w kategorii, filtrowanie listy testów i tworzenia, zapisywania i uruchom listy odtwarzania testów. Można również Debuguj testy i Analizuj pokrycie testu wydajności i kod. Aby dowiedzieć się więcej, zobacz temat [uruchamiania testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md).

![Uruchamianie testów jednostkowych z Eksploratora testów](media/testexplorer.png)

## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Użyj pokrycie kodu, aby określić, ile kodu jest poddawana testom

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie zabezpieczyć się przed błędami, testy powinny obejmować lub pokrywać znaczną część kodu. Aby dowiedzieć się więcej, zobacz temat [pokrycia kodu używany do określenia, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

![Aby określić, ile kodu jest poddawana testom korzystanie z pokrycia kodu](media/codecoverage.png)

## <a name="use-a-different-unit-test-framework"></a>Użyj struktury testowej inną jednostkę

Za pomocą platform testów innych firm, takich jak zwiększenie wydajności, Google i nUnit można uruchomić testów jednostkowych programu Visual Studio. Użyj wtyczki dla struktury, że Visual Studio test runner może współpracować z tej struktury.

Poniżej przedstawiono kroki, aby włączyć platform testów do innych części:

1. Wybierz **narzędzia** > **rozszerzenia i aktualizacje...**  na pasku menu.

1. W **rozszerzenia i aktualizacje** okna dialogowego rozwiń **Online** kategorii, a następnie **Visual Studio Marketplace**. Następnie wybierz pozycję **narzędzia** > **testowanie**.

   ![Visual Studio Marketplace](media/extensions-and-updates-testing.png)

1. Wybierz framework lub chcesz zainstalować, a następnie wybierz kartę **Pobierz**.

1. Tworzenie projektu biblioteki klas, a następnie dodaj go do rozwiązania.

   ![Nazwa projektu biblioteki klas i dodaj go](media/create3rdpartyunittest3.png)

1. Zainstaluj wtyczkę. W **Eksploratora rozwiązań**wybierz projektu biblioteki klas, a następnie wybierz pozycję **Zarządzaj pakietami NuGet...**  menu kliknij prawym przyciskiem myszy lub kontekstu.

   ![Zarządzanie pakietami NuGet, aby zainstalować dodatek typu plug-in](media/create3rdpartyunittest3a.png)

   [NuGet](https://www.nuget.org/) to rozszerzenie programu Visual Studio, która umożliwia dodawanie i aktualizowanie bibliotek i narzędzi dla projektów.

1. W **Menedżera pakietów NuGet** okna, wyszukaj i wybierz wtyczki, a następnie wybierz **zainstalować**.

   ![Zainstaluj z framework 3rd firm](media/create3rdpartyunittest4.png)

   Platformę odwołuje się do projektu.

   ![Dokumentacja dla platformy testów jednostkowych firmy 3rd została dodana do rozwiązania](media/create3rdpartyunittest6.png)

1. Z projektu biblioteki klas **odwołania** węzła, wybierz opcję **Dodawanie odwołania...** .

   ![Dodaj odwołanie do projektu](media/createunittest6.png)

1. W **Menedżera odwołań** oknie dialogowym Wybierz projekt, który zawiera kod przetestujesz.

   ![Wybierz projekt kodu do testowania](media/createunittest7.png)

1. Kod testu jednostki.

   ![Dodaj kod, aby z testu jednostkowego](media/create3rdpartyunittest7.png)

## <a name="see-also"></a>Zobacz także

* [Polecenie Utwórz testy jednostkowe](create-unit-tests-menu.md)
* [Generowanie testów z IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Uruchamianie testów za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md)
* [Określić pokrycie kodu](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Podnoszenie jakości kodu](improve-code-quality.md)