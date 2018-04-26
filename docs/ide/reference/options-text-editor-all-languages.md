---
title: Opcje, edytor tekstu, wszystkie języki
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a887d31eded0f7f37e9ec5390a934c192836697
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="options-text-editor-all-languages"></a>Opcje, edytor tekstu, wszystkie języki
To okno dialogowe umożliwia zmianę domyślnego zachowania edytora kodu. Te ustawienia dotyczą również inne edytory oparte na kodzie edytora, takiego jak projektanta HTML widoku źródła. Aby otworzyć to okno dialogowe, wybierz **opcje** z **narzędzia** menu. W ramach **Edytor tekstu** folder, rozwiń węzeł **wszystkie języki** podfolder, a następnie wybierz **ogólne**.

> [!CAUTION]
> Ta strona Ustawia opcje domyślne dla wszystkich języków programowania. Należy pamiętać, że zresetowanie opcji w tym oknie dialogowym przywróci Opcje ogólne we wszystkich językach, niezależnie od opcji wybrano tutaj. Aby zmienić opcje edytora tekstowego dla tylko jednego języka, rozwiń podfolder dla tego języka i wybierz strony jej opcji.


 Wyszarzonymi polami wyboru jest wyświetlane, gdy wybrano opcję na stronach ogólnych opcji w przypadku niektórych języków programowania, ale nie do innych użytkowników.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).


## <a name="statement-completion"></a>Dokańczanie instrukcji
 Automatycznie lista składników

 Po wybraniu wyskakujących listy dostępne elementy członkowskie, właściwości lub metody wartości są wyświetlane przez funkcję IntelliSense podczas wpisywania tekstu w edytorze. Wybierz dowolny element na liście wyskakującego można umieścić element w kodzie. Wybranie tej opcji umożliwia **Ukryj zaawansowane członków** opcji.

 Ukryj zaawansowane elementy członkowskie

 Po wybraniu skraca listy uzupełniania instrukcji wyskakujących poprzez wyświetlenie tylko tych elementów, które są najczęściej używane. Inne elementy są filtrowane z listy.

 Informacje o parametrach

 Po wybraniu pełnej składni dla bieżącej deklaracji lub procedura jest wyświetlana w obszarze kursora w edytorze, biorąc pod uwagę jego dostępnych parametrów. Następny parametr, który można przypisać jest wyświetlane wytłuszczonym drukiem.

## <a name="settings"></a>Ustawienia
 Włącz pamięć wirtualna

 Po wybraniu tej opcji i **zawijanie** jest wyczyszczone, możesz kliknąć dowolnego miejsca za końcem wiersza w edytorze kodu i typu. Ta funkcja umożliwia umieść komentarzy w punkcie spójne obok kodu.

 Zawijanie tekstu

 Po wybraniu jakiejkolwiek jego części linii w poziomie wykracza poza obszar Edytor widoczny jest automatycznie wyświetlana w następnym wierszu. Wybranie tej opcji umożliwia **Pokaż zualne przy zawijaniu wierszy** opcji.

> [!NOTE]
> **Wirtualną przestrzeń** jest włączona funkcja wyłączony podczas **zawijanie** znajduje się na.


 Pokaż zualne przy zawijaniu wierszy

 Po wybraniu wskaźnika Strzałka powrotu jest wyświetlany, gdy długi wiersz jest zawijana wokół drugi wiersz.

 ![LineBreakSymbol — zrzut ekranu](../../ide/reference/media/linebreak.gif "linebreak")

 Usuń zaznaczenie tej opcji, jeśli nie chcesz wyświetlić te wskaźniki.

> [!NOTE]
> Te strzałki monitu nie są dodawane do kodu, a nie do drukowania. Są one jedynie do celów referencyjnych.


 Zastosowanie polecenia Wytnij lub Kopiuj do pustych wierszy, gdy nie ma żadnego zaznaczenia

 Ta opcja umożliwia ustawienie zachowania edytora po umieszczeniu kursora na pusty wiersz, wybierz nothing, a następnie skopiować lub Wytnij.

-   Gdy ta opcja jest zaznaczona, pusty wiersz jest kopiowany lub Wytnij. Jeśli następnie wkleić, jest wstawiany nowy, pusty wiersz.

-   Po wyłączeniu tej opcji polecenia Wytnij usuwa puste wiersze. Jednak dane w Schowku zostaną zachowane. W związku z tym Jeśli następnie użyć polecenia Wklej, jest wkleić zawartość ostatnio skopiowana do Schowka. Jeśli nic nie został skopiowany wcześniej, nic nie jest wkleić.

To ustawienie nie ma wpływu na kopiowania lub wycinania podczas wiersza nie jest pusty. Jeśli nic nie zostanie wybrane, cały wiersz jest kopiowany lub Wytnij. Jeśli następnie wkleić, są wklejane tekst cały wiersz i jego endline znaku.

> [!TIP]
> Aby wyświetlić wskaźniki spacje, tabulatory i końców linii i w związku z tym odróżnienia wiersze z wcięciami wiersze, które są całkowicie pusty, wybierz **zaawansowane** z **Edytuj** menu i wybierz polecenie **biały widoku Miejsce**.


## <a name="display"></a>Monitor
 Numery wiersza

 W przypadku wybrania, numer wiersza obok każdego wiersza kodu.

> [!NOTE]
> Tych numerów wierszy nie są dodawane do kodu, a nie do drukowania. Są one jedynie do celów referencyjnych.


 Włącz nawigację adresów URL jednym kliknięciem

 Po wybraniu kursor myszy zmienia postać dłoni jako przesuwa się nad adres URL w edytorze. Możesz kliknąć adres URL, aby wyświetlić stronę wskazanych w przeglądarce sieci Web.

 Pasek nawigacyjny

 Po wybraniu Wyświetla **pasek nawigacyjny** w górnej części edytora kodu. Jego listy rozwijanej **obiektów** i **członków** listy można wybrać określonego obiektu w kodzie, wybierz jedną z jej elementów członkowskich i przechodzi do deklaracji wybranego elementu członkowskiego w edytorze kodu.

## <a name="see-also"></a>Zobacz też

- [Opcje, Edytor tekstu, wszystkie języki, karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)