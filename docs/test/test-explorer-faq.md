---
title: Eksplorator testów programu Visual Studio — często zadawane pytania | Dokumentacja firmy Microsoft
ms.date: 1/15/2018
ms.technology: vs-ide-test
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 9e64528b6b0669a0403188b540a90e9b921bfb34
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="visual-studio-test-explorer-faq"></a>Eksplorator testów programu Visual Studio — często zadawane pytania

## <a name="test-discovery"></a>Odnajdywanie testów

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-are-dynamically-defined-for-example-theories-custom-adapters-custom-traits-ifdefs-etc-how-can-i-discover-these-tests"></a>1. Eksplorator testów nie jest odnajdywania Moje testów, które są zdefiniowane dynamicznie. (Na przykład teorii, kart niestandardowych, niestandardowe cech, #ifdefs, itp.) Jak można odnaleźć tych testów?

  Skompilowanie projektu i upewnij się, że jest włączone odnajdowanie na podstawie zestawu **Narzędzia > Opcje > Test**.

  [Odnajdywania testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824) jest odnajdywania na podstawie źródła testu. Nie można odnaleźć testów, które korzystają z teorii, kart niestandardowych, niestandardowe cech `#ifdef` instrukcje, itp., ponieważ są one zdefiniowane w czasie wykonywania. Kompilacja jest wymagane dla tych testów dokładnie odnajdywania. 15.6 podglądu na podstawie zestawu (wykrywacz tradycyjny) odnajdywania tylko po kompilacji. To ustawienie oznacza wykrywania testów w czasie rzeczywistym wykryje tyle testów, ponieważ może on podczas edytowania i odnajdowania opartego na zestawie pozwala dynamicznie zdefiniowanych testów są wyświetlane po kompilacji. Wykrywania testów w czasie rzeczywistym skraca czas odpowiedzi, ale aparaturze pozwala uzyskać kompletne i dokładne wyniki po kompilacji.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. Co to jest "+" (oraz) symbol, który jest wyświetlany w górnym wierszu średniej Eksploratora testów?

  "+" Symbol wskazuje, że większej liczby testów nie może odnaleźć po kompilacji tak długo, jak jest włączone odnajdowanie na podstawie zestawu (oraz). Wygląda na to, czy dynamicznie zdefiniowane się, że testy zostaną wykryte w projekcie.

  ![Symbol wiersz podsumowania plus](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. Odnajdowania opartego na zestawie już nie działa dla projektu. Jak włączyć go ponownie?

  Przejdź do **Narzędzia > Opcje > Test** i pole wyboru dla **Ponadto odnaleźć testów z wbudowanych zestawów po kompilacji.**

  ![Na podstawie zestawu opcji](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. Testy są wyświetlane w Eksploratorze testów podczas wpisywania, bez konieczności tworzenia projektu. Co się zmieniło?

  Ta funkcja jest nazywana [wykrywania testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824). Analizator Roslyn używa odnaleźć testów i wypełnić Eksploratora testów w czasie rzeczywistym, bez konieczności skompilowanie projektu. Aby uzyskać więcej informacji dotyczących zachowania odnajdywania testu dynamicznie zdefiniowanych testów takich jak teorii lub cech niestandardowych zobacz często zadawane pytania dotyczące #1.

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. Jakich języków i struktur test służy odnajdywania testów w czasie rzeczywistym?

  [Wykrywania testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824) działa tylko dla języków zarządzane (C# i Visual Basic), ponieważ jest utworzony przy użyciu kompilatora Roslyn. Na razie wykrywania testów w czasie rzeczywistym działa tylko dla xUnit NUnit i MSTest struktury.

### <a name="6-how-can-i-turn-on-logs-for-the-test-explorer"></a>6. Jak można włączyć dzienniki dla Eksploratora testów?

  Przejdź do **Narzędzia > Opcje > Test** i znaleźć w sekcji rejestrowanie.

### <a name="7-why-are-my-tests-in-uwp-projects-not-discovered-until-i-deploy-my-app"></a>7. Dlaczego są testy Moje projekty platformy UWP nie zostało wykryte do momentu wdrożyć mojej aplikacji?

  Testy platformy uniwersalnej systemu Windows docelowego innego środowiska uruchomieniowego, gdy aplikacja jest wdrożona. Oznacza to, czy odnaleźć testów dokładnie dla projektów uniwersalnych systemu Windows nie wystarczy skompilowanie projektu, ale również wdrożyć.

### <a name="8-how-does-sorting-test-results-work-in-the-hierarchy-view"></a>8. Jak działa sortowania wyników testów w widoku hierarchii

  Widok hierarchii testy alfabetycznie w przeciwieństwie do sortowania wyników. Inne grupy za pomocą ustawień zwykle sortować wyniki testu wyników, a następnie alfabetycznie. Aby wyświetlić innej grupy opcji na poniższej ilustracji do porównania. Możesz podać swoją opinię na temat projektowania [ten problem GitHub](https://github.com/Microsoft/vstest/issues/1425).

  ![SortingExamples](media/testex-sortingex.png)

### <a name="9-in-the-hierarchy-view-there-are-passed-failed-skipped-and-not-run-icons-next-to-the-project-namespace-and-class-groupings-what-do-these-icons-mean"></a>9. W widoku hierarchii są przekazywane, nie powiodło się, zostało pominięte, a nie uruchomiono ikonami obok projektu, Namespace i klasa grupowania. Co oznaczają ikony

  Ikony obok projektu, Namespace i klasa grupowania odzwierciedlają stan testów w ramach tej grupy. Zobacz poniższą tabelę.

  ![Ikony hierarchii Eksploratora testów](media/testex-hierarchyicons.png)
  
### <a name="10-there-is-no-longer-a-file-path-filter-in-the-test-explorer-search-box"></a>10. Nie ma filtru "Ścieżka pliku" w polu wyszukiwania Eksploratora testów.

Filtr ścieżki pliku w **Eksploratora testów** pole wyszukiwania został usunięty w wersji zapoznawczej programu Visual Studio 2017 wersji 15.7 3. Ta funkcja ma niskie obciążenie i Eksploratora testów można pobrać metody testowe szybsze, wyłączając tę funkcję. Jeśli ta zmiana przerwania z przepływem programowanie, prosimy o kontakt poprzez przesłanie opinii na [społeczność deweloperów](https://developercommunity.visualstudio.com/).

## <a name="features"></a>Funkcje

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>Jak można włączyć funkcji flagi wypróbowanie nowych funkcji testowania?

Flagi funkcji są używane na potrzeby wysłania eksperymentalne lub niedokończone części produktu dla avid użytkowników, których chcesz przekazać opinię, przed oficjalnie funkcji. Mogą one zdestabilizować środowiska IDE. Ich używać tylko w środowiskach programistycznych bezpieczne, takich jak maszyny wirtualne. Flagi funkcji zawsze są ustawienia użyj —-your właścicielem — zagrożony. Można włączyć funkcję eksperymentalną z [flagi funkcji rozszerzenia](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension), lub za pomocą wiersza polecenia dewelopera.

![Rozszerzenie flagi funkcji](media/testex-featureflag.png)

Aby włączyć flagę funkcji za pomocą wiersza polecenia programu Visual Studio developer, użyj następującego polecenia. Zmień ścieżkę, na którym jest zainstalowany program Visual Studio na komputerze i zmienić wartość klucza rejestru flagi żądanej funkcji.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise” HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Flaga przy użyciu tego samego polecenia, można wyłączyć za pomocą wartości 0 zamiast 1 po dword.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Tworzenie i Uruchamianie testów jednostkowych dla istniejącego kodu](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Testowanie jednostek kodu](unit-test-your-code.md)
- [Live Unit Testing — często zadawane pytania](live-unit-testing-faq.md)
