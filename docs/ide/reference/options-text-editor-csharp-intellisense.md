---
title: Opcje, Edytor tekstu, C#, IntelliSense | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 78763e0257334065b1fdbcbcab5f106face20dee
ms.sourcegitcommit: 238cd48787391aa0ed1eb684f3f04e80f7958705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2018
---
# <a name="options-text-editor-c-intellisense"></a>Opcje, edytor tekstu, C#, IntelliSense

Użyj **IntelliSense** Strona opcji, aby zmodyfikować ustawienia, które wpływają na zachowanie IntelliSense dla języka C#. Aby uzyskać dostęp do tej strony opcji, należy wybrać **narzędzia** > **opcje**, a następnie wybierz pozycję **Edytor tekstu** > **C#**  >  **IntelliSense**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

**IntelliSense** opcje strona zawiera następujące opcje:

## <a name="completion-lists"></a>Listy uzupełniania

- Pokaż listę uzupełniania po wpisaniu znaku *

   Gdy ta opcja jest zaznaczona, IntelliSense automatycznie wyświetla listę uzupełniania po rozpoczęciu wpisywania. Gdy ta opcja nie jest zaznaczona, uzupełniania IntelliSense jest nadal dostępny z **IntelliSense** menu lub naciskając klawisz **Ctrl**+**miejsca**.

- Pokaż listę uzupełniania po usunięciu znak

- Wyróżnianie pasujących części listy uzupełniania

- Pokaż ukończenie listy filtrów

- Pokaż sugestie dotyczące nazwy

### <a name="snippets-behavior"></a>Zachowanie wstawki kodu programu

- Nigdy nie dołączaj wstawki kodu programu

   Gdy ta opcja jest zaznaczona, IntelliSense nigdy nie dodaje do listy uzupełniania aliasów wstawki kodu C#.

- Zawsze należy uwzględniać wstawki kodu programu

   Gdy ta opcja jest zaznaczona, IntelliSense dodaje aliasy wstawki kodu C# do listy zakończenia. W przypadku, gdy alias fragment kodu jest taka sama jak słowem kluczowym, na przykład [klasy](/dotnet/csharp/language-reference/keywords/class), słowo kluczowe zastępuje skrótu. Aby uzyskać więcej informacji, zobacz [wstawki kodu C#](../../ide/visual-csharp-code-snippets.md).

- Obejmują wstawki podczas? — karta bezpośrednio po identyfikatora

   Gdy ta opcja jest zaznaczona, IntelliSense dodaje aliasów dla C# kodu fragmenty kodu do wykonania po liście **?** + **Kartę** zostanie naciśnięty po identyfikatora

### <a name="enter-key-behavior"></a>Zachowanie klawisza ENTER

- Nigdy nie należy dodawać nowy wiersz po naciśnięciu klawisza enter

   Określa, że nowy wiersz nigdy nie jest automatycznie dodawane po wybraniu elementu na liście uzupełniania i naciskając klawisz **Enter**.

- Tylko dodać nowy wiersz po naciśnięciu klawisza enter po zakończeniu wpisaniu całego słowa

   Określa, że jeśli wpisz wszystkich znaków dla wpisu na liście uzupełniania, a następnie naciśnij klawisz **Enter**, nowy wiersz jest automatycznie dodawane i kursor zostanie umieszczony w nowym wierszu.

   Na przykład jeśli wpiszesz `else` , a następnie naciśnij klawisz **Enter**, w edytorze pojawi się następujące:

   `else`

   `|`(Lokalizacja kursora)

   Jednak w przypadku wpisania tylko `el` , a następnie naciśnij klawisz **Enter**, w edytorze pojawi się następujące:

   `else|`(Lokalizacja kursora)

- Zawsze należy dodać nowy wiersz po naciśnięciu klawisza enter

   Określa, że w przypadku wpisania *żadnych* znaków dla pozycji w liście uzupełniania, a następnie naciśnij klawisz **Enter**, nowy wiersz jest automatycznie dodawane i kursor zostanie umieszczony w nowym wierszu.

## <a name="see-also"></a>Zobacz także

[Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)  
[Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)