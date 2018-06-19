---
title: Zainstaluj analizatorów Roslyn w programie Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: fb2f681de16a53c97954c8c37b8dd28b163998ee
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927536"
---
# <a name="install-net-compiler-platform-analyzers"></a>Zainstaluj platformę .NET kompilatora analizatorów

Visual Studio 2017 zawiera zbiór platformy kompilatora .NET (*Roslyn*) analizatorów. Te analizatory są zawsze włączone. Można zainstalować dodatkowe analizatorów jako pakietów NuGet, albo jako rozszerzenia programu Visual Studio w *VSIX* plików.

## <a name="to-install-nuget-package-analyzers"></a>Aby zainstalować analizatorów pakietu NuGet

1. [Ustalić, która wersja pakietu analizator](https://github.com/dotnet/roslyn-analyzers#recommended-version-of-analyzer-packages) do zainstalowania, zależnie od wersji programu Visual Studio.

1. Zainstaluj pakiet w programie Visual Studio za pomocą [Konsola Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) lub [interfejsu użytkownika Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Strona nuget.org dla każdego pakietu analizatora zawiera polecenie, aby wkleić **Konsola Menedżera pakietów**. Istnieje nawet przydatną przycisk, aby skopiować tekst do Schowka.
   >
   > ![Strona NuGet.org przedstawiający polecenie konsoli Menedżera pakietów](media/nuget-package-manager-command.png)

   Zestawy analizatora są zainstalowane i są wyświetlane w **Eksploratora rozwiązań** w obszarze **odwołania** > **analizatorów**.

   ![Węzeł analizatorów w Eksploratorze rozwiązań](media/solution-explorer-analyzers-node.png)

## <a name="to-install-vsix-analyzers"></a>Aby zainstalować analizatory pliku VSIX

1. W programie Visual Studio, wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

   **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.

   > [!NOTE]
   > Można również pobrać rozszerzenia bezpośrednio z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Rozwiń węzeł **Online** w okienku po lewej stronie, a następnie wybierz **Visual Studio Marketplace**.

1. W polu wyszukiwania wpisz "Analiza kodu" i wyszukaj **2017 analizy kodu Microsoft** rozszerzenia.

   ![Rozszerzenia Microsoft kod — analiza](media/extensions-and-updates-code-analysis.png)

1. Wybierz **Pobierz**.

   Rozszerzenie zostanie pobrana.

1. Wybierz **OK** aby zamknąć okno dialogowe, a następnie zamknij wszystkie wystąpienia programu Visual Studio, aby uruchomić **Instalatora VSIX**.

   **Instalatora VSIX** zostanie otwarte okno dialogowe.

   ![Instalator VSIX dla Microsoft analizy kodu](media/vsix-installer-code-analysis.png)

1. Wybierz **Modyfikuj** do rozpoczęcia instalacji.

1. Po minucie lub dwóch zakończeniu instalacji. Wybierz **Zamknij**.

1. Otwórz ponownie program Visual Studio.

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz pozycję **narzędzia** > **rozszerzenia i aktualizacje**. W **rozszerzenia i aktualizacje** okno dialogowe, wybierz opcję **zainstalowana** kategorii po lewej stronie, a następnie Wyszukaj według nazwy rozszerzenia.

## <a name="next-steps"></a>Następne kroki

- [Użyj analizatorów Roslyn w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz także

- [Omówienie analizatorów Roslyn w programie Visual Studio](../code-quality/roslyn-analyzers-overview.md)