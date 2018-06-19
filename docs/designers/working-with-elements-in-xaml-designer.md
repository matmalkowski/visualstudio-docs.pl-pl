---
title: Praca z elementami w Projektancie XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 676c8767691610349cc2eee4c09970318feda9f5
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34269193"
---
# <a name="working-with-elements-in-xaml-designer"></a>Praca z elementami w Projektancie XAML
Możesz dodawać elementy — formanty, układów i kształty — do aplikacji w języku XAML, kodu lub przy użyciu projektanta XAML. W tym temacie opisano sposób pracy z elementami w Projektancie XAML w programie Visual Studio lub program Blend for Visual Studio.

## <a name="adding-an-element-to-a-layout"></a>Dodawanie elementu układ
 *Układ* to proces zmiany rozmiaru i pozycjonowania elementów w interfejsie użytkownika. Położenie elementów wizualnych, możesz je umieścić w układzie [panelu](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx). A `Panel` ma właściwość podrzędne, która jest kolekcją z [FrameworkElement](http://msdn.microsoft.com/library/windows/apps/br208706.aspx) typów. Można użyć różnych `Panel` elementy podrzędne, takie jak [kanwy](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [Panel stosu](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx), i [siatki](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx), jako kontenery układów i to pozycjonowania i rozmieszczania elementów na stronie.

 Domyślnie `Grid` panel służy jako kontener układu najwyższego poziomu w ramach strony lub formularza. Można dodać panele układu, formantów i innych elementów w obrębie układ strony najwyższego poziomu.

#### <a name="to-add-an-element-to-a-layout"></a>Aby dodać element do układu

-   W Projektancie XAML wykonaj jedną z następujących czynności:

    -   Kliknij dwukrotnie element **przybornika** (lub wybierz element z przybornika i naciśnij klawisz Enter).

    -   Przeciągnij element na podstawie **przybornika** do obszaru roboczego.

    -   W **przybornika**, wybierz jedno z narzędzi do rysowania (na przykład [elipsy](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) lub [prostokąt](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx)), a następnie narysuj element w panelu active.

## <a name="changing-the-layering-order-of-elements"></a>Zmiana kolejności warstw elementów
 Gdy istnieją dwa elementy w obszarze roboczym w Projektancie XAML, jeden element pojawi się na początku drugiej w porządku Tworzenie warstw. W dolnej części listy elementów na tworzenie konspektu dokumentu okno jest elementem wierzch (z wyjątkiem kiedy **wyznacza indeks** ustawiono właściwości dla elementu). Po wstawieniu elementu do strony, formularza lub kontener układu elementu jest automatycznie umieszczane przed inne elementy w elemencie kontenera usługi active. Aby zmienić kolejność elementów, można użyć **kolejności** polecenia lub przeciągnij elementy drzewa obiektów okno konspektu dokumentu.

#### <a name="to-change-the-layering-order"></a>Aby zmienić kolejność Tworzenie warstw

-   Wykonaj jedną z następujących czynności:

    -   W **konspekt dokumentu** okna, przeciągnij elementy w górę lub w dół do utworzenia żądanego kolejność.

    -   Kliknij prawym przyciskiem myszy element w okno konspektu dokumentu lub obszar roboczy, dla którego chcesz zmienić kolejność, wskaż polecenie **kolejności**, a następnie kliknij jedną z następujących czynności:

        -   **Przełącz do przodu** można wyświetlić elementu aż do przodu kolejności.

        -   **Przenieś do przodu** można wyświetlić elementu przesyłania dalej o jeden poziom w kolejności.

        -   **Wyślij do tyłu** można wysłać elementu wstecz o jeden poziom w kolejności.

        -   **Wyślij do tyłu** do wysyłania elementu aż do tyłu kolejności.

     Zmień **wyznacza indeks** właściwości w **układu** sekcji w oknie właściwości. Nakładających się elementów **wyznacza indeks** właściwość ma wyższy priorytet niż kolejność elementów wyświetlany w oknie konspektu dokumentu. Element, który ma wyższy **wyznacza indeks** wartość znajduje się na wierzchu podczas nakładania się elementów.

## <a name="changing-the-alignment-of-an-element"></a>Zmiana wyrównania elementu
 Za pomocą poleceń menu lub przez przeciąganie elementów do linii wyrównania można wyrównać elementów w obszarze roboczym.

 A *snapline —* jest wizualnie pomaga wyrównanie elementu względem innych elementów w aplikacji.

#### <a name="to-align-two-or-more-elements-by-using-menu-commands"></a>Aby wyrównać co najmniej dwa elementy za pomocą poleceń menu

1.  Wybierz elementy, które chcesz wyrównać. Można wybrać więcej niż jeden element, przytrzymując klawisz Ctrl podczas zaznaczania elementów.

2.  Wybierz jedną z następujących właściwości w obszarze **HorizontalAlignment** w **układu** okna właściwości: **lewej**, **Center**, **Prawej**, lub **Stretch**.

3.  Wybierz jedną z następujących właściwości w obszarze **HorizontalAlignment** w **układu** okna właściwości: **górnej**, **Center**, **Dolnej**, lub **Stretch**.

#### <a name="to-align-two-or-more-elements-by-using-snaplines"></a>Aby wyrównać co najmniej dwa elementy za pomocą linii przyciągania

-   W Projektancie XAML w układzie, który zawiera co najmniej dwa elementy przeciągnij lub jednego z elementów zmiany rozmiaru, dzięki czemu krawędzi jest wyrównywana z innego elementu.

     Gdy wyrównania krawędzi, *granicy wyrównania* pojawia się, aby wskazać wyrównania. Granicy wyrównania jest linię kropkowaną czerwony. Wyrównanie granice są wyświetlane tylko wtedy, gdy **przyciąganie do linii wyrównania** jest włączona. Ilustracja obszaru roboczego, który pokazuje granicy wyrównania, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="changing-an-elements-margins"></a>Zmiana marginesy elementu
 Marginesy w Projektancie XAML określają ilość wolnego miejsca, która jest wokół elementu w obszarze roboczym. Na przykład marginesy Określ ilość miejsca między zewnętrznej krawędzi elementu i granice `Grid` panelu, który zawiera element. Marginesy również określić ilość miejsca między elementami, które są zawarte w `StackPanel`.

#### <a name="to-change-an-elements-margins-in-the-properties-window"></a>Aby zmienić marginesy elementu w oknie właściwości

1.  Wybierz element, którego chcesz zmienić marginesy.

2.  W obszarze **układu** w oknie Właściwości zmień wartość (w pikselach lub jednostki niezależnych od urządzenia, które są około 1/96 cala) dla każdego z **margines** właściwości (**górnej**, **Lewej**, **prawej**, lub **dolnej**).

#### <a name="to-change-an-elements-margins-in-the-artboard"></a>Aby zmienić marginesy elementu w obszarze roboczym

-   Aby zmienić marginesy elementu względem jego kontenera układu, kliknij przycisk *margines takich modułów* wyświetlanych wokół elementu w obszarze roboczym, gdy element jest zaznaczony i znajduje się w kontenerze układu. Ilustracja przedstawiająca margines takich modułów, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     Jeśli moduł definiowania układu kodu marginesu jest otwarty, w poziomie czy w pionie, że marża nie została ustawiona. Jeśli moduł definiowania układu kodu marginesu jest zamknięty, że marża jest ustawiona.

     Po otwarciu moduł definiowania układu kodu margines i przeciwną margines nie została ustawiona, przeciwną margines jest ustawiony na poprawną wartość w zależności od lokalizacji elementu w obszarze roboczym. Marginesy przeciwnej takich jak **lewej** i **prawej** marginesy co najmniej jedną właściwość ma zawsze wartość.

    > [!IMPORTANT]
    >  Elementy umieszczone wewnątrz niektóre kontenery układów, takich jak <xref:Windows.UI.Xaml.Controls.Canvas>, nie ma margines takich modułów. Elementy umieszczone wewnątrz <xref:Windows.UI.Xaml.Controls.StackPanel> ma margines modułu definiowania układu kodu w obu lewego i prawego marginesu lub marginesy górny i dolny, w zależności od orientację `StackPanel`.

## <a name="grouping-and-ungrouping-elements"></a>Grupowanie i rozgrupowywanie elementów
 Grupowanie co najmniej dwa elementy w Projektancie XAML tworzy nowy kontener układu i umieszcza tych elementów w tym kontenerze. Umieszczania co najmniej dwa elementy w kontenerze układu umożliwia łatwe wybierz, przenoszenie i przekształcenie grupy tak, jakby elementów w tej grupie był jeden element. Grupowanie jest również przydatny do identyfikowania elementów, które są powiązane ze sobą w sposób, takie jak przyciski wchodzące w skład elementu nawigacji. Gdy Rozgrupuj elementy, po prostu usuwasz kontener układu, który zawiera elementy.

#### <a name="to-group-elements-into-a-new-layout-container"></a>Elementy grupy do nowy kontener układu

1.  Wybierz elementy, które mają być grupowane. (Aby zaznaczyć wiele elementów, naciśnij i przytrzymaj klawisz Ctrl, a następnie kliknij je).

2.  Kliknij prawym przyciskiem myszy wybrane elementy, wskaż pozycję **grupy do**, a następnie kliknij typ kontenera układu, w którym mają znajdować się grupie.

    > [!TIP]
    >  W przypadku wybrania <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, lub <xref:Windows.UI.Xaml.Controls.ScrollViewer> do grupowania elementów, elementy są umieszczane w nowym <xref:Windows.UI.Xaml.Controls.Grid> panelu w <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, lub <xref:Windows.UI.Xaml.Controls.ScrollViewer>. Jeśli Rozgrupuj elementów w jeden z tych kontenery układów tylko <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, lub <xref:Windows.UI.Xaml.Controls.ScrollViewer> zostanie usunięty i <xref:Windows.UI.Xaml.Controls.Grid> pozostaje panelu. Aby usunąć `Grid` panelu, Rozgrupuj elementy ponownie.

#### <a name="to-ungroup-elements-and-delete-the-layout"></a>Rozgrupuj elementów i usuwania układu

-   Kliknij prawym przyciskiem myszy grupę, którą chcesz rozgrupować, a następnie kliknij przycisk **Rozgrupuj**.

 Możesz również elementy grupy lub rozgrupowywanie prawym przyciskiem myszy wybrane elementy w okno konspektu dokumentu, a następnie klikając polecenie **grupy do** lub **Rozgrupuj**.

## <a name="resetting-the-element-layout"></a>Resetowanie układu elementu
 Za pomocą poleceń zresetować układ, można przywrócić wartości domyślne dla właściwości układu określonego elementu. Za pomocą tego polecenia, można zresetować margines, wyrównanie, szerokości, wysokości i rozmiar elementu, pojedynczo lub zbiorczo.

#### <a name="to-reset-the-element-layout"></a>Aby zresetować układ elementu

-   Okno konspektu dokumentu lub obszar roboczy, kliknij prawym przyciskiem myszy element, wybierz **układu**, **zresetować** *PropertyName*, gdzie *PropertyName*jest właściwość, którą chcesz zresetować (lub wybierz **układu**, **zresetować wszystkie** do resetowania wszystkich właściwości układu elementu).

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
