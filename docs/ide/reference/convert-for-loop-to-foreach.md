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
ms.openlocfilehash: 34758473bcbee8ccad7d9dff9df2f1478ca1202c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refaktoryzacja konwersję między dla pętli i instrukcji foreach

Refaktoryzacje te dotyczą:

- C#

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Konwertuj dla pętli foreach — instrukcja

Jeśli masz [dla](/dotnet/csharp/language-reference/keywords/for) pętli w kodzie, umożliwia to refaktoryzacji przekonwertować go na [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji.

### <a name="why-convert"></a>Dlaczego konwersji

Powodów, dla których ma zostać przekonwertowany [dla](/dotnet/csharp/language-reference/keywords/for) pętli do [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji obejmują:

- Zmienna liczba iteracji w pętli, z wyjątkiem nie używaj jako indeks dostępu do elementu.

- Chcesz uprościć kod i zmniejszyć prawdopodobieństwo wystąpienia błędów logiki inicjatora, warunku i instrukcji iteracji.

### <a name="how-to-use-it"></a>Jak z niego korzystać

1. Umieść kursor w pierwszym wierszu `for` pętli.

1. Naciśnij klawisz **Ctrl**+**.** lub kliknij przycisk śrubokręt ![ikona śrubokręt](../media/screwdriver-icon.png) ikony na marginesie pliku kodu.

   ![Konwertuj foreach menu](media/convert-to-foreach.png)

1. Wybierz **przekonwertować na "foreach"**. Lub wybierz **podgląd zmian** otworzyć [podgląd zmian](../../ide/preview-changes.md) okna dialogowego, a następnie wybierz **Zastosuj**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Konwertuj instrukcji foreach do pętli for

Jeśli masz [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji w kodzie, umożliwia to refaktoryzacji przekonwertować go na [dla](/dotnet/csharp/language-reference/keywords/for) pętli.

### <a name="why-convert"></a>Dlaczego konwersji

Powodów, dla których ma zostać przekonwertowany [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) instrukcji [dla](/dotnet/csharp/language-reference/keywords/for) pętli obejmują:

- Chcesz użyć zmiennej liczby iteracji wewnątrz pętli do więcej niż tylko uzyskiwania dostępu do elementu.

- Jesteś [iteracji w tablicy wielowymiarowej](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) i chcesz mieć większą kontrolę nad elementów tablicy.

### <a name="how-to-use-it"></a>Jak z niego korzystać

1. Umieść kursor w pierwszym wierszu `foreach` instrukcji.

1. Naciśnij klawisz **Ctrl**+**.** lub kliknij przycisk śrubokręt ![ikona śrubokręt](../media/screwdriver-icon.png) ikony na marginesie pliku kodu.

   ![Konwertuj menu](media/convert-to-for.png)

1. Wybierz **przekonwertować na "for"**. Lub wybierz **podgląd zmian** otworzyć [podgląd zmian](../../ide/preview-changes.md) okna dialogowego, a następnie wybierz **Zastosuj**.

1. Ponieważ refaktoryzację wprowadza nową zmienną liczby iteracji **zmienić** pojawi się w prawym górnym rogu edytora. Jeśli chcesz wybrać inną nazwę zmiennej, wpisz go w, a następnie naciśnij klawisz **Enter** lub wybierz **Zastosuj** w **zmienić** pole. Jeśli nie chcesz wybrać nową nazwę, naciśnij klawisz **Esc** lub wybierz **Zastosuj** aby odrzucić **zmienić** pole.

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)