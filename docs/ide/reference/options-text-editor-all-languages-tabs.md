---
title: Opcje, edytor tekstu, wszystkie języki, karty
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8487d90c41d4ab98ce3b8456a5347994188ebb31
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="options-text-editor-all-languages-tabs"></a>Opcje, edytor tekstu, wszystkie języki, karty
To okno dialogowe umożliwia zmianę domyślnego zachowania edytora kodu. Te ustawienia dotyczą również inne edytory oparte na kodzie edytora, takiego jak projektanta HTML widoku źródła. Aby wyświetlić te opcje, zaznacz **opcje** z **narzędzia** menu. W ramach **Edytor tekstu** rozwiń folder **wszystkie języki** podfolderu, a następnie wybierz pozycję **karty**.

> [!CAUTION]
> Ta strona Ustawia opcje domyślne dla wszystkich języków programowania. Należy pamiętać, że zresetowanie opcji w tym oknie dialogowym przywróci Opcje kart we wszystkich językach, niezależnie od opcji wybrano tutaj. Aby zmienić opcje edytora tekstowego dla tylko jednego języka, rozwiń podfolder dla tego języka i wybierz strony jej opcji.


 Jeśli nie wybrano różne ustawienia na stronach Opcje kart dla określonych języków programowania, a następnie komunikat "Ustawienia wcięć dla pojedynczych tekst formatów będących w konflikcie ze sobą", nie będą wyświetlane różniących się **Indenting**opcje; i zostanie wyświetlony komunikat "Ustawienia tabulacji dla pojedynczych tekst formatów będących w konflikcie ze sobą,", dla różniących się **kartę** opcje. Na przykład to przypomnienie jest wyświetlana, jeśli **inteligentne wcięcie** wybrano opcję dla programu Visual Basic, ale **zablokować wcięcia** jest zaznaczona w języku Visual C++.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).


## <a name="indenting"></a>Wcięcia
 Brak

 Po wybraniu nowych wierszy nie są przeznaczone. Punkt wstawiania znajduje się w pierwszej kolumnie znakiem nowego wiersza.

 Blok

 Po wybraniu nowych wierszy tworzone jest wcięcie automatycznie. Punkt wstawiania znajduje się w tym samym punkcie wyjścia w poprzednim wierszu.

 Inteligentne

 Po wybraniu nowe wiersze są pozycjonowane do kontekstu kodu na inny kod formatowania ustawienia i konwencje IntelliSense dla danego języka programowania. Ta opcja nie jest dostępny dla wszystkich języków programowania.

 Na przykład wiersze ujętą nawiasu otwierającego ({}) i zamykający nawias klamrowy (}) mogą być automatycznie wcięty dodatkowe tabulatora od położenia wyrównany nawiasów klamrowych.

## <a name="tabs"></a>Karty
 Rozmiar tabulatora

 Ustawia odległość w spacji między kartę zatrzymuje. Wartość domyślna to czterech spacji.

 Wcięcie

 Umożliwia ustawienie rozmiaru w funkcji miejsca do automatycznego wcięcia. Wartość domyślna to czterech spacji. Znaki tabulacji, znaków spacji lub obu zostanie wstawiony do wypełnienia określonego rozmiaru.

 Wstawiaj odstępy

 Po wybraniu wcięcie operacji insert tylko znaki spacji, nie znaki TABULACJI. Jeśli **wcięcie rozmiar** jest ustawiony na 5, na przykład, następnie pięć znaków spacji są wstawiane po naciśnięciu klawisza TAB lub **Zwiększ wcięcie** znajdującego się na **formatowanie** pasek narzędzi.

 Utrzymaj tabulacje

 Po wybraniu wcięcie operacji insert dowolną liczbę znaków TABULACJI jak to możliwe. Każdy znak TABULACJI wypełnia liczbę spacji określone w **Rozmiar tabulatora**. Jeśli **wcięcie rozmiar** nie jest wielokrotnością **Rozmiar tabulatora**, spacje są dodawane do wypełnienia różnicy.

## <a name="see-also"></a>Zobacz też

- [Opcje, Edytor tekstu, wszystkie języki](../../ide/reference/options-text-editor-all-languages.md)
- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)