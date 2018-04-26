---
title: Opcje, edytor tekstu, XAML, formatowanie
ms.date: 01/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 59b161c1f2dedd0b9c14f9949cfcc164f39b26ea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="options-text-editor-xaml-formatting"></a>Opcje, edytor tekstu, XAML, formatowanie
Użyj **formatowanie** strony właściwości, aby określić sposób formatowania elementów i atrybutów w dokumencie XAML. Aby otworzyć **opcje** okno dialogowe, kliknij przycisk **narzędzia** menu, a następnie kliknij przycisk **opcje**. Aby uzyskać dostęp do **formatowanie** właściwości rozwiń pozycję **Edytor tekstu**, **XAML**, **formatowanie** węzła.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).


## <a name="auto-formatting-events"></a>Automatyczne formatowanie zdarzeń
 Automatyczne formatowanie może wystąpić, gdy dowolne z następujących zdarzeń wykryciu.

-   Zakończenie tagu końcowego lub prostego.

-   Zakończeniu tagu początkowego.

-   Wklejanie ze Schowka.

-   Formatowanie polecenia klawiatury.

Można określić zdarzenia, które powodują automatyczne formatowanie.

|||
|-|-|
|**Po zakończeniu tagu końcowego lub prostego**|Automatyczne formatowanie występuje po zakończeniu wpisywania tagu końcowego lub prostego tagu. Prostych tagów nie ma atrybutów, na przykład `<Button />`.|
|**Po zakończeniu tagu początkowego**|Automatyczne formatowanie występuje po zakończeniu wpisywania tagu początkowego.|
|**Po wklejeniu ze Schowka**|Automatyczne formatowanie występuje podczas wklejania XAML ze Schowka do widoku XAML.|

## <a name="quotation-mark-style"></a>Styl znaku cudzysłowu
 To ustawienie wskazuje, czy wartości atrybutów są ujęte w cudzysłów pojedynczym lub podwójnym. Program formatujący automatycznie i automatycznego uzupełniania IntelliSense Użyj tego ustawienia.

 Po ustawieniu tej opcji tylko atrybuty później dodane przy użyciu narzędzia Projektant lub ręcznie w widoku XAML dotyczy problem.

|||
|-|-|
|**Podwójny cudzysłów (")**|Wartości atrybutów są ujęte w cudzysłów.<br /><br /> `<Button Name="button1">Hello</Button>`|
|**Pojedynczych cudzysłowów (')**|Wartości atrybutów są ujęte w apostrofy.<br /><br /> `<Button Name='button1'>Hello</Button>`|

## <a name="tag-wrapping"></a>Zawijanie taga
 Można podać długość wiersza zawijanie znacznika. Po włączeniu zawijanie tagów żadnych XAML dodane przy użyciu projektanta będzie odpowiednio zawijany.

|||
|-|-|
|**Zawijaj tagi przekraczające określoną długość**|Określa, czy wiersze są ujęte w wierszu długości określonej przez **długość**.|
|**długość**|Liczba znaków, które mogą zawierać wiersza. W razie potrzeby wiersze XAML może przekraczać długości określonej linii.|

## <a name="attribute-spacing"></a>Odstępy atrybutów
 Użyj tego ustawienia, aby kontrolować sposób rozmieszczenia atrybutów w dokumencie XAML

|||
|-|-|
|**Zachowaj newlines i spacji między atrybutami**|Nowe wiersze i spacji między atrybutami nie dotyczy automatyczne formatowanie.<br /><br /> `<Button Height="23"   Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Wstaw odstęp między atrybutami**|Atrybuty zajmują jeden wiersz z jednego miejsca oddzielanie atrybuty sąsiadujących ze sobą. Ustawienia zawijania tagów są stosowane.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|
|**Umieść każdy atrybut w osobnym wierszu**|Każdy atrybut zajmuje w osobnym wierszu. Jest to przydatne, gdy wiele atrybutów są obecne.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Pozycja pierwszego atrybutu w tym samym wierszu co tag początkowy**|Po zaznaczeniu tej opcji, zostanie wyświetlony pierwszy atrybut w tym samym wierszu co tag początkowy elementu.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|

## <a name="element-spacing"></a>Odstępy elementów
 Użyj tego ustawienia, aby kontrolować sposób rozmieszczenia elementów w dokumencie XAML

|||
|-|-|
|**Zachowaj nowe wiersze w zawartości**|Puste wiersze w zawartości elementu nie są usuwane.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|
|**Zwiń wiele puste wiersze w zawartości do jednej linii**|Puste wiersze w zawartości elementu są zwijane do jednego wiersza.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|
|**Usuń puste wiersze w zawartości**|Zostaną usunięte wszystkie puste wiersze w zawartości elementu.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`|

## <a name="miscellaneous-section-auto-insert"></a>Różne części, automatyczne wstawianie
 To ustawienie służy do kontrolowania, kiedy tagów i cudzysłowy są generowane automatycznie.

|||
|-|-|
|**Zamykanie tagów**|Określa, czy tagu zamykającego element jest generowany automatycznie podczas zamykania otwierający tag o większej niż znaku (>).|
|**Cudzysłowy atrybutu**|Określa, czy otaczającego cudzysłowy są generowane w przypadku wybrania wartości atrybutu z listy rozwijanej uzupełniania instrukcji.|
|**Klamrowe nawiasy zamykające do wyrażenia MarkupExtension**|Określa, czy rozszerzenie znacznika zamykającego nawiasu (}) jest generowana automatycznie po wpisaniu otwarcia nawiasy znak ({}).|
|**Oddzielać parametry wyrażeń MarkupExtension**|Określa, czy przecinkami są generowane po wpisaniu więcej niż jeden parametr w rozszerzeniu znaczników.|

## <a name="see-also"></a>Zobacz także

- [XAML w WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
