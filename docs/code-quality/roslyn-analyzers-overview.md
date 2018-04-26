---
title: Analizatory Roslyn w programie Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: aaa989347744e015b90cca186c6aa9756dfe90fe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Omówienie analizatorów platformę .NET kompilatora

Visual Studio 2017 zawiera zestaw wbudowanych analizatorów platformy kompilatora .NET, których analiza kodu C# lub Visual Basic podczas pisania. Można zainstalować dodatkowe analizatorów jako rozszerzenia programu Visual Studio lub na podstawie-projekt jako pakietu NuGet. Analizatory przyjrzeć się styl kodu, jakości kodu i utrzymanie kodu projektu i inne problemy.

W przypadku znalezienia naruszeń zasady przez analizatora są zgłaszane w edytorze kodu jako *dowolnym kształcie* kodem ataku i w **listy błędów**.

Wiele reguł analizatora, lub *diagnostyki*, występuje jeden lub kilka skojarzonych *kodu poprawki* można zastosować do rozwiązania problemu. Diagnostyka analizatora, które są wbudowane w program Visual Studio ma poprawka skojarzonego kodu. Poprawki kodu są wyświetlane w menu ikoną żarówki wraz z innych typów *szybkie akcje*. Informacje te poprawki kodu, zobacz [wspólnej szybkie akcje](../ide/common-quick-actions.md).

![Naruszenie analizator i Popraw kod szybkich akcji](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analizatory Roslyn a statycznej analizy kodu

Po pewnym czasie zastąpi analizatorów platformy kompilatora .NET ("Roslyn") [statycznej analizy kodu](../code-quality/code-analysis-for-managed-code-overview.md) dla kodu zarządzanego. Ma wiele reguł analizy kodu statycznych zostało już przepisany Roslyn analizator diagnostyki.

Podobnie jak naruszenia reguły analizy kodu statycznych, naruszeń analizator Roslyn są wyświetlane w **listy błędów**. Ponadto naruszeń analizator Roslyn również wyświetlane w edytorze kodu jako *squigglies* kodem ataku. Kolor o dowolnym kształcie zależy od [ustawienia ważność](../code-quality/use-roslyn-analyzers.md#rule-severity) reguły. Poniższy zrzut ekranu przedstawia trzy naruszeń&mdash;jeden czerwony, jeden zielony i jeden szary:

![Squigglies w edytorze kodu](media/diagnostics-severity-colors.png)

Analizatory Roslyn analizowania kodu w czasie kompilacji, takie jak statycznej analizy kodu, jeśli jest włączona, ale także na żywo podczas wpisywania! Analizatory Roslyn można też podać czasu projektowania analizy plików kodu, które nie jest otwarty w edytorze, jeśli włączysz [Pełna analiza rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Czas kompilacji błędów i ostrzeżeń z analizatorów Roslyn są wyświetlane tylko jeśli analizatorów są zainstalowane jako pakietu NuGet.

Nie będą zgłaszać Roslyn analizatory te same rodzaje problemów, które statycznej analizy kodu jest tylko one ułatwić można rozwiązać co najmniej wszystkich wystąpień naruszenia w pliku lub projektu. Te akcje są nazywane *kodu poprawki*. Poprawki kodu są specyficzne dla IDE; w programie Visual Studio są zaimplementowane jako [szybkie akcje](../ide/quick-actions.md). Nie wszystkie diagnostyki analyzer ma poprawka skojarzonego kodu.

> [!NOTE]
> Opcja menu **Analizuj** > **uruchamiania analizy kodu** ma zastosowanie tylko do statycznej analizy kodu. Ponadto w ramach projektu **analizy kodu** strony właściwości **Włącz analizę kodu podczas kompilacji** i **Pomijaj wyniki z wygenerowanego kodu** pola wyboru tylko do zastosowania statycznej analizy kodu. Ich nie mają wpływu na Roslyn analizatorów.

W celu rozróżnienia naruszeń z analizatorów Roslyn i statycznej analizy kodu w **listy błędów**, obejrzyj **narzędzia** kolumny. Jeśli wartość narzędzia zgodny z jednym z zestawów analizator w **Eksploratora rozwiązań**, na przykład **Microsoft.CodeQuality.Analyzers**, naruszenie pochodzi z analizatora Roslyn. W przeciwnym razie naruszenie pochodzi z statycznej analizy kodu.

![Narzędzie kolumny listy błędów](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-vs-extension"></a>Pakiet NuGet, a rozszerzenia

Platforma .NET kompilatora analizatory mogą być zainstalowane na projekt za pośrednictwem pakietu NuGet, lub Visual Studio na poziomie jako rozszerzenia programu Visual Studio. Istnieją pewne różnice zachowanie klucza te dwie metody [instalowanie analizatorów](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Zakres

Po zainstalowaniu analizatorów jako rozszerzenia programu Visual Studio, dotyczą one na poziomie rozwiązanie wszystkich wystąpień programu Visual Studio. Jeśli zainstalujesz analizatorów jako pakietu NuGet, który jest preferowaną metodą, mają one zastosowanie tylko do projektu, na którym zainstalowano pakiet NuGet. W środowiskach zespołu analizatorów zainstalowany jako pakiety NuGet są w zakresie *wszystkich deweloperów* współpracujące z tego projektu.

### <a name="build-errors"></a>Błędy kompilacji

Reguły wymuszane w czasie kompilacji, w tym za pomocą wiersza polecenia lub w ramach ciągłej integracji (CI) kompilacji, aby zainstalować analizatorów jako pakietu NuGet. Analizator ostrzeżeń i błędów nie są wyświetlane w raporcie kompilacji po zainstalowaniu analizatorów jako rozszerzenie.

Poniższy zrzut ekranu przedstawia tworzenie projekt, który zawiera naruszenia reguły analizatora dane wyjściowe kompilacji wiersza polecenia:

![Dane wyjściowe programu MSBuild z naruszeniem reguł](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Ważność reguły

Nie można ustawić ważność reguły z analizatorów, które zostały zainstalowane jako rozszerzenia programu Visual Studio. Aby skonfigurować [reguły ważność](../code-quality/use-roslyn-analyzers.md#rule-severity), zainstaluj analizatorów jako pakietu NuGet.

## <a name="next-steps"></a>Następne kroki

- [Zainstaluj analizatorów Roslyn w programie Visual Studio](../code-quality/install-roslyn-analyzers.md)
- [Użyj analizatorów Roslyn w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje w programie Visual Studio](../ide/quick-actions.md)
- [Napisać własny analizator Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Zestaw SDK platformy kompilatora .NET](/dotnet/csharp/roslyn-sdk/)