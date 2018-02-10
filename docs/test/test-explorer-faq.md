---
title: "Testowanie Explorer — często zadawane pytania | Dokumentacja firmy Microsoft"
ms.date: 1/15/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
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
ms.openlocfilehash: fd64bb3bce6b6477c0db1c7d0c5a15e518ae71ef
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="visual-studio-test-explorer-faq"></a>Eksplorator testów programu Visual Studio — często zadawane pytania

## <a name="test-discovery"></a>Odnajdywanie testów

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-have-theories-custom-adapters-custom-traits-use-ifdefs-or-are-dynamically-defined-how-can-i-discover-these-tests"></a>1. Eksplorator testów nie jest odnajdywania Moje testy, które mają teorii, kart niestandardowych, niestandardowe cech, użyj #ifdefs lub dynamicznie zdefiniowane. Jak można odnaleźć tych testów?

  Skompilowanie projektu i upewnij się, że jest włączone odnajdowanie na podstawie zestawu **Narzędzia > Opcje > Test**.

  [Odnajdywania testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824), która jest odnajdywania na podstawie źródła testu nie może odnaleźć testów, które korzystają z teorii, kart niestandardowych, niestandardowe cech `#ifdef` instrukcji lub który dynamicznie są zdefiniowane w inny sposób. Kompilacja jest wymagane dla tych testów dokładnie odnajdywania. 15.6 podglądu na podstawie zestawu (wykrywacz tradycyjny) odnajdywania tylko po kompilacji. Oznacza to, że wykrywania testów w czasie rzeczywistym wykryje tyle testów, ponieważ może on podczas edytowania i odnajdowania opartego na zestawie umożliwia teorii (lub wszystkie testy dynamicznie zdefiniowanych) są wyświetlane po kompilacji. Wykrywania testów w czasie rzeczywistym skraca czas odpowiedzi, ale aparaturze pozwala uzyskać kompletne i dokładne wyniki po kompilacji.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. Co to jest "+" (oraz) symbol, który jest wyświetlany w górnym wierszu średniej Eksploratora testów?

  "+" Symbol wskazuje, że większej liczby testów nie są wykrywane po kompilacji w przypadku włączonego odnajdowania opartego na zestawie (oraz). Jeśli zdefiniowano dynamicznie pojawi się się, że testy zostaną wykryte w projekcie.

  ![Symbol wiersz podsumowania plus](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. Odnajdowania opartego na zestawie już nie działa dla projektu. Jak włączyć go ponownie?

  Przejdź do **Narzędzia > Opcje > Test** i pole wyboru dla **Ponadto odnaleźć testów skompilowane z zestawów po kompilacji.**

  ![Na podstawie zestawu opcji](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. Testy są wyświetlane w Eksploratorze testów podczas wpisywania, bez konieczności tworzenia projektu. Co się zmieniło?

  Ta funkcja jest nazywana [wykrywania testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824). Analizator platformę .NET Complier ("Roslyn") używa odnaleźć testów i wypełnić Eksploratora testów w czasie rzeczywistym, bez konieczności skompilowanie projektu. Aby uzyskać więcej informacji dotyczących zachowania odnajdywania testu dynamicznie zdefiniowanych testów takich jak teorii lub cech niestandardowych, zobacz często zadawane pytania dotyczące #1.

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. Jakich języków i struktur test służy odnajdywania testów w czasie rzeczywistym?

  [Wykrywania testów w czasie rzeczywistym](https://go.microsoft.com/fwlink/?linkid=862824) działa tylko dla języków zarządzane (C# i Visual Basic), ponieważ jest utworzony przy użyciu kompilatora .NET ("Roslyn"). Na razie wykrywania testów w czasie rzeczywistym działa tylko dla xUnit NUnit i MSTest struktury.

## <a name="features"></a>Funkcje

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>Jak można włączyć funkcji flagi wypróbowanie nowych funkcji testowania?

Flagi funkcji są używane na potrzeby wysłania eksperymentalne lub niedokończone części produktu dla avid użytkowników, których chcesz przekazać opinię, przed oficjalnie funkcji. Mogą one zdestabilizować środowiska IDE. Zaleca się ich używać tylko w środowiskach bezpieczne programistycznych, takich jak maszyny wirtualne. Flagi funkcji zawsze są ustawienia użyj —-your właścicielem — zagrożony. Można włączyć funkcję eksperymentalną z [flagi funkcji rozszerzenia](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension), lub za pomocą wiersza polecenia dewelopera.

![Rozszerzenie flagi funkcji](media/testex-featureflag.png)

Aby włączyć flagę funkcji za pomocą wiersza polecenia programu Visual Studio developer, użyj następującego polecenia. Zmień ścieżkę, na którym jest zainstalowany program Visual Studio na komputerze i zmienić wartość klucza rejestru flagi żądanej funkcji.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise” HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Flaga przy użyciu tego samego polecenia, można wyłączyć za pomocą wartości 0 zamiast 1 po dword.
  
## <a name="see-also"></a>Zobacz także

<xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>  
[Tworzenie i Uruchamianie testów jednostkowych dla istniejącego kodu](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
[kod testu jednostkowego](unit-test-your-code.md)
[na żywo — często zadawane pytania testy jednostkowe](live-unit-testing-faq.md)
