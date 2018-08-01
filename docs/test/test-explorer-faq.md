---
title: Eksplorator testów programu Visual Studio — często zadawane pytania
ms.date: 1/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: douge
ms.openlocfilehash: 720a69b1eae8a14247027a52ef2972e43203163b
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382412"
---
# <a name="visual-studio-test-explorer-faq"></a>Eksplorator testów programu Visual Studio — często zadawane pytania

## <a name="test-discovery"></a>Odnajdywanie testów

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-are-dynamically-defined-for-example-theories-custom-adapters-custom-traits-ifdefs-etc-how-can-i-discover-these-tests"></a>1. Eksplorator testów nie jest odnajdywanie Moje testy, które są definiowane dynamicznie. (Na przykład teorii, niestandardowych kart, niestandardowe cech, #ifdefs itp.) Jak odnajdywanie, te testy?

  Skompiluj projekt i upewnij się, odnajdywanie na podstawie zestawu jest włączona w programie **narzędzia** > **opcje** > **testu**.

  [Wykrywanie testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824) jest odnajdywanie testów opartych na źródle. Nie można odnaleźć, testy, które korzystają z teorii, niestandardowe karty, niestandardowe cech `#ifdef` instrukcji, itp., ponieważ są one definiowane w czasie wykonywania. Kompilacja jest wymagana dla tych testów, aby dokładnie zostać odnalezione. W wersji 15.6 wersji zapoznawczych opartych na zestawie odnajdywania (wykrywacz tradycyjny) działa tylko po kompilacji. To ustawienie oznacza, że wykrywanie testów w czasie rzeczywistym umożliwia odnalezienie dowolną liczbę testów, jak można podczas edytowania i opartych na zestawie umożliwia dynamicznie definiowane testów są wyświetlane po kompilacji. Wykrywanie testów w czasie rzeczywistym poprawia czas odpowiedzi, ale aparaturze pozwala uzyskać kompletne i dokładne wyniki po kompilacji.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. Co to jest "+" (plus) symbol, który pojawia się w górnej linii średniej Eksploratora testów?

  "+" (Plus) symbol informuje, że może zostać odnalezionych więcej testów po kompilacji tak długo, jak odnajdywanie na podstawie zestawu jest włączona. Prawdopodobnie jeśli definiowane dynamicznie testy zostaną wykryte w projekcie.

  ![Symbol wiersz podsumowania plus](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. Odnajdywanie na podstawie zestawu już nie działa dla mojego projektu. Jak włączyć go ponownie?

  Przejdź do **narzędzia** > **opcje** > **testu** i pole wyboru dla **dodatkowo odnajduj testy z poziomu skompilowanych zestawów po kompilacje.**

  ![Na podstawie zestawu opcji](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. Testy są wyświetlane w Eksploratorze testów podczas pisania, bez konieczności tworzenia projektu. Co się zmieniło?

  Ta funkcja jest nazywana [wykrywanie testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824). Odnajduj testy i wypełnić Eksplorator testów w czasie rzeczywistym bez konieczności kompilowania projektu użyto analizatora Roslyn. Aby uzyskać więcej informacji o zachowaniu odnajdywania testów dla dynamicznie definiowane testów, takich jak TEORIE lub cechy niestandardowych zobacz często zadawane pytania dotyczące nr 1.

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. Jakich języków i środowisk testowych można użyć odnajdywaniem testów w czasie rzeczywistym?

  [Wykrywanie testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824) działa tylko dla języki zarządzane (C# i Visual Basic), ponieważ został skompilowany przy użyciu kompilator Roslyn. Na razie wykrywanie testów w czasie rzeczywistym działa tylko w przypadku xUnit, NUnit oraz MSTest struktur.

### <a name="6-how-can-i-turn-on-logs-for-the-test-explorer"></a>6. Jak można włączyć dzienniki dla Eksploratora testów?

  Przejdź do **narzędzia** > **opcje** > **testu** i znaleźć w sekcji rejestrowanie.

### <a name="7-why-are-my-tests-in-uwp-projects-not-discovered-until-i-deploy-my-app"></a>7. Dlaczego są moje testy w projektach platformy uniwersalnej systemu Windows, które nie zostało wykryte do momentu czy mogę wdrożyć mojej aplikacji?

  Testy platformy uniwersalnej systemu Windows przeznaczone różne środowiska uruchomieniowego, gdy aplikacja jest wdrożona. Oznacza to, aby odnaleźć testy dokładnie w projektach platformy uniwersalnej systemu Windows nie tylko konieczność Skompiluj projekt, ale także wdrożyć.

### <a name="8-how-does-sorting-test-results-work-in-the-hierarchy-view"></a>8. Jak działa sortowania wyników testów w widoku hierarchii

  Widok hierarchii sortowania testy alfabetycznie w przeciwieństwie do wyników. Grupy za pomocą ustawień zwykle sortować wyniki testów według wyników i następnie alfabetycznie. Aby wyświetlić innej grupy opcji na poniższej ilustracji do porównania. Możesz przekazywać opinie dotyczące projektowania [ten problem usługi GitHub](https://github.com/Microsoft/vstest/issues/1425).

  ![SortingExamples](media/testex-sortingex.png)

### <a name="9-in-the-hierarchy-view-there-are-passed-failed-skipped-and-not-run-icons-next-to-the-project-namespace-and-class-groupings-what-do-these-icons-mean"></a>9. W widoku hierarchii zostaną przekazane, zakończone niepowodzeniem, pominięto i nie uruchomiono ikony obok projektu, Namespace i klasa grupowania. Co oznaczają ikony

  Ikony obok projektu, Namespace i klasa grupowania odzwierciedlają stan testów w ramach tej grupy. Zobacz poniższą tabelę.

  ![Ikony hierarchii Eksploratora testów](media/testex-hierarchyicons.png)

### <a name="10-there-is-no-longer-a-file-path-filter-in-the-test-explorer-search-box"></a>10. Nie ma już filtru "Ścieżka pliku" w polu wyszukiwania Eksploratora testów.

Filtr ścieżki pliku w **Eksplorator testów** pole wyszukiwania została usunięta w wersji 15.7 programu Visual Studio 2017 w wersji zapoznawczej 3. Ta funkcja była o niskim użyciu i Eksplorator testów może pobrać szybszych metod testowych, z wyłączeniem tej funkcji. Jeśli ta zmiana przerywa przepływ rozwoju, Daj nam znać, przesyłając swoje opinie na [społeczności deweloperów](https://developercommunity.visualstudio.com/).

## <a name="features"></a>Funkcje

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>Jak można włączyć flagi funkcji, aby wypróbować nowe funkcje testowania?

Flagi funkcji są używane na potrzeby wysłania eksperymentalne lub niedokończone części produktu avid użytkownikom, którzy chcieliby przesłać opinię, zanim funkcje dostarczanie oficjalnie. Mogą one zdestabilizować środowiska IDE. Ich używać tylko w środowiskach programowania bezpiecznych, takich jak maszyny wirtualne. Flagi funkcji są zawsze Użyj your-own zagrożonej ustawienia. Można włączyć funkcji eksperymentalnych, za pomocą [flagi funkcji rozszerzenia](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension), lub za pomocą wiersza polecenia dla deweloperów.

![Rozszerzenie flagi funkcji](media/testex-featureflag.png)

Aby włączyć flagi funkcji za pomocą wiersza polecenia dla deweloperów programu Visual Studio, użyj następującego polecenia. Zmień ścieżkę, na którym zainstalowano program Visual Studio na komputerze i zmienić wartość klucza rejestru do flagi żądanej funkcji.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Flaga przy użyciu tego samego polecenia, można wyłączyć przy użyciu wartości 0 zamiast 1 po typu dword.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Tworzenie i Uruchamianie testów jednostkowych dla istniejącego kodu](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Kod testu jednostkowego](unit-test-your-code.md)
- [Testowanie jednostek — często zadawane pytania na żywo](live-unit-testing-faq.md)
