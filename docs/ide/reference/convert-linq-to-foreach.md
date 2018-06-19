---
title: Zrefaktoryzuj kod, aby skonwertować kwerendy LINQ do instrukcji foreach
ms.date: 05/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e3e4e448931e028c53d62c534e2785e4f026a7ec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268923"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refaktoryzacja przekonwertować LINQ do instrukcji foreach

Użyj tego refaktoryzacji, aby przekonwertować [składni zapytań LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) do [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji.

Dotyczy to refaktoryzacji:

- C#

## <a name="how-to-use-it"></a>Jak z niego korzystać

1. Wybierz całą LINQ zapytania początkowe z `from`.

   > [!NOTE]
   > Ta refaktoryzacji tylko można przekonwertować zapytań LINQ wyrażone składnia zapytania i nie składni metody.

1. Naciśnij klawisz **Ctrl**+**.** lub kliknij przycisk śrubokręt ![ikona śrubokręt](../media/screwdriver-icon.png) ikony na marginesie pliku kodu.

   ![Konwertuj menu Szybkie akcje foreach LINQ](media/convert-linq-to-foreach.png)

1. Wybierz **przekonwertować na "foreach"**. Lub wybierz **podgląd zmian** otworzyć [podgląd zmian](../../ide/preview-changes.md) okna dialogowego, a następnie wybierz **Zastosuj**.

> [!NOTE]
> Język C#, kod wygenerowany przez te refaktoryzacje używa jawnego typu lub [var](/dotnet/csharp/language-reference/keywords/var) dla zmiennej iteracji `foreach` pętli. Typ w wygenerowanym kodzie, bezpośrednie lub pośrednie, zależy od ustawień styl kodu, które znajdują się w zakresie. Te ustawienia określonego stylu kodu są konfigurowane na poziomie komputera w obszarze **narzędzia** > **opcje** > **Edytor tekstu**  >  **C#** > **styl kodu** > **ogólne** > **\'var " Preferencje**, lub na poziomie rozwiązania [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types) pliku. Jeśli zmienisz ustawienie stylu kodu **opcje**, otwórz plik kodu, aby zmiany zaczęły obowiązywać.

## <a name="see-also"></a>Zobacz także

- [LINQ](/dotnet/standard/using-linq)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)