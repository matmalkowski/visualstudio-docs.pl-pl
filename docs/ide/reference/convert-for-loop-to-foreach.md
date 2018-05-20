---
title: Zrefaktoryzuj kod, aby przekonwertować dla pętli foreach — instrukcja
ms.date: 05/10/2018
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
ms.openlocfilehash: 6a200874cec92fada17c13eb45e226ce26119a60
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refaktoryzacja konwersję między dla pętli i instrukcji foreach

W tym artykule opisano refaktoryzacje szybkie akcje, które konwersji między dwoma struktury pętli. Obejmuje on przyczyny, dlaczego warto przełączania się między [dla](/dotnet/csharp/language-reference/keywords/for) pętli i [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji w kodzie.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Konwertuj dla pętli foreach — instrukcja

Jeśli masz [dla](/dotnet/csharp/language-reference/keywords/for) pętli w kodzie, umożliwia to refaktoryzacji przekonwertować go na [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji.

Dotyczy to refaktoryzacji:

- C#

> [!NOTE]
> **Przekonwertować foreach** refaktoryzacji szybkie akcja jest dostępna tylko dla [dla](/dotnet/csharp/language-reference/keywords/for) pętli, które zawierają wszystkie trzy części: inicjatora, warunek i iteratora.

### <a name="why-convert"></a>Dlaczego konwersji

Powodów, dla których ma zostać przekonwertowany [dla](/dotnet/csharp/language-reference/keywords/for) pętli do [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji obejmują:

- Za pomocą zmiennej lokalnej wewnątrz pętli, z wyjątkiem jako indeks nie można uzyskiwać dostęp do elementów.

- Chcesz uprościć kod i zmniejszyć prawdopodobieństwo wystąpienia błędów logiki inicjatora, warunek i sekcje iteratora.

### <a name="how-to-use-it"></a>Jak z niego korzystać

1. Umieść Twojej karetki w `for` — słowo kluczowe.

1. Naciśnij klawisz **Ctrl**+**.** lub kliknij przycisk śrubokręt ![ikona śrubokręt](../media/screwdriver-icon.png) ikony na marginesie pliku kodu.

   ![Konwertuj foreach menu](media/convert-to-foreach.png)

1. Wybierz **przekonwertować na "foreach"**. Lub wybierz **podgląd zmian** otworzyć [podgląd zmian](../../ide/preview-changes.md) okna dialogowego, a następnie wybierz **Zastosuj**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Konwertuj instrukcji foreach do pętli for

Jeśli masz [instrukcji foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) lub [For Each... Dalej (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) instrukcji w kodzie, umożliwia to refaktoryzacji przekonwertować go na [dla](/dotnet/csharp/language-reference/keywords/for) pętli.

Dotyczy to refaktoryzacji:

- C#

- Visual Basic

### <a name="why-convert"></a>Dlaczego konwersji

Powodów, dla których ma zostać przekonwertowany [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji [dla](/dotnet/csharp/language-reference/keywords/for) pętli obejmują:

- Chcesz użyć zmiennej lokalnej wewnątrz pętli do więcej niż tylko uzyskiwania dostępu do elementu.

- Jesteś [iteracji w tablicy wielowymiarowej](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) i chcesz mieć większą kontrolę nad elementów tablicy.

### <a name="how-to-use-it"></a>Jak z niego korzystać

1. Umieść Twojej karetki w `foreach` lub `For Each` — słowo kluczowe.

1. Naciśnij klawisz **Ctrl**+**.** lub kliknij przycisk śrubokręt ![ikona śrubokręt](../media/screwdriver-icon.png) ikony na marginesie pliku kodu.

   ![Konwertuj menu](media/convert-to-for.png)

1. Wybierz **przekonwertować na "for"**. Lub wybierz **podgląd zmian** otworzyć [podgląd zmian](../../ide/preview-changes.md) okna dialogowego, a następnie wybierz **Zastosuj**.

1. Ponieważ refaktoryzację wprowadza nową zmienną liczby iteracji **zmienić** pojawi się w prawym górnym rogu edytora. Jeśli chcesz wybrać inną nazwę zmiennej, wpisz go w, a następnie naciśnij klawisz **Enter** lub wybierz **Zastosuj** w **zmienić** pole. Jeśli nie chcesz wybrać nową nazwę, naciśnij klawisz **Esc** lub wybierz **Zastosuj** aby odrzucić **zmienić** pole.

> [!NOTE]
> Język C#, kod wygenerowany przez te refaktoryzacje używa jawnego typu lub [var](/dotnet/csharp/language-reference/keywords/var) dla typu elementów w kolekcji. Typ w wygenerowanym kodzie, bezpośrednie lub pośrednie, zależy od ustawień styl kodu, które znajdują się w zakresie. Te ustawienia określonego stylu kodu są konfigurowane na poziomie komputera w obszarze **narzędzia** > **opcje** > **Edytor tekstu**  >  **C#** > **styl kodu** > **ogólne** > **\'var " Preferencje**, lub na poziomie rozwiązania [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types) pliku. Jeśli zmienisz ustawienie stylu kodu **opcje**, otwórz plik kodu, aby zmiany zaczęły obowiązywać.

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)