---
title: Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66addedc32c7023e774cd28f340f8216516c3fb7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio

Program Blend for Visual Studio ułatwia projektowanie opartych na języku XAML systemu Windows i aplikacji sieci Web. Zawiera środowisko tego samego projektu XAML podstawowe co program Visual Studio i dodaje wizualnych projektantów zaawansowanych zadań, takich jak animacji i zachowania. Porównanie między Blend i Visual Studio, zobacz [projektowania XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md).

Program Blend for Visual Studio jest składnikiem programu Visual Studio. Do zainstalowania programu Blend, w **Instalator programu Visual Studio** wybrać **rozwoju platformy uniwersalnej systemu Windows** lub **tworzenia klasycznych aplikacji .NET** obciążenia. Te obciążenia obejmują program Blend for Visual Studio składnika.

![Składniki obciążenia platformy uniwersalnej systemu Windows](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Składniki obciążenia tworzenia klasycznych aplikacji .NET](media/installer-dotnet-desktop.png)

Jeśli jesteś nowym użytkownikiem programu Blend for Visual Studio, Poświęć chwilę, aby zapoznać się z unikatowe funkcje obszaru roboczego. W tym temacie przejmuje krótki przewodnik.

> [!NOTE]
> Aby samouczek funkcje projektu udostępnionego, takie jak kompozycji, okno konspektu dokumentu i okno urządzenia, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="tour-of-the-tools-panel"></a>Samouczek panelu Narzędzia

Można użyć **narzędzia** panelu w programie Blend for Visual Studio do tworzenia i modyfikowania obiektów w aplikacji. Aby utworzyć obiekty wybierania narzędzia i rysowanie w obszarze roboczym przy użyciu myszy.

![Narzędzia panelu](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|||||
|-|-|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Narzędzia wyboru** wybierz obiekty i ścieżki.<br /><br /> Użyj **Zaznaczanie bezpośrednie** narzędzie do wybierania zagnieżdżone obiekty i segmentów ścieżki.|![Objaśnienie A](../designers/media/b5_label_a.png "b5_label_A")|**Narzędzia gradientu i pędzla**|
|![](../designers/media/b1_2.png "B1_2")|**Wyświetl narzędzia** Dopasuj widok obszaru roboczego, takich jak przesuwać i powiększać.|![Objaśnienie B](../designers/media/b5_label_b.png "b5_label_B")|**Ścieżka narzędzia**|
|![](../designers/media/b1_3.png "B1_3")|**Pędzel narzędzia** pracować z visual atrybutów obiektu, takie jak Przekształcanie Pędzel, malowanie obiektu lub wybierając atrybuty jednego obiektu, aby zastosować je do innego obiektu.|![C objaśnienia](../designers/media/b5_label_c.png "b5_label_C")|**Narzędzia kształtu**|
|![](../designers/media/b1_4.png "B1_4")|**Obiekt narzędzia** narysować najczęściej obiektów w obszarze roboczym, takich jak ścieżki, kształtów panele układu, tekst i kontrolek.|![D objaśnienia](../designers/media/b5_label_d.png "b5_label_D")|**Panele układu**|
|![](../designers/media/b1_5.png "B1_5")|**Narzędzia zasobów** dostępu **zasoby** panelu i pokazanie ostatnio używane zasobu z biblioteki.|![E objaśnienia](../designers/media/b5_label_e.png "b5_label_E")|**Kontrolki tekstu**|
|||![F objaśnienia](../designers/media/b5_label_f.png "b5_label_F")|**Formanty standardowe**|

**Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [narzędzi](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="tour-of-the-assets-panel"></a>Samouczek panelu Zasoby

Możesz znaleźć wszystkie formanty w **zasoby** panelu, podobnie jak **przybornika** w programie Visual Studio. Oprócz formantów, można znaleźć wszystko, co można dodać do kompozycję w **zasoby** panelu, w tym style, nośnik, zachowania i efektów.

![Panelu Zasoby](../designers/media/blend5_assets_panel.png "Blend5_Assets_panel")

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Pole wyszukiwania** wpisz **wyszukiwania** pole, aby zastosować filtr do listy zasobów.|
|![](../designers/media/b1_2.png "B1_2")|**Tryb siatki i tryb listy** przełączania się między **trybu siatki** widoku i **tryb listy** widok zasoby.|
|![](../designers/media/b1_3.png "B1_3")|**Kategorie zasoby** kliknij kategorię lub podkategorię, aby wyświetlić listę zasobów w tej kategorii.|
|![](../designers/media/b1_4.png "B1_4")|**Style** Pokaż wszystkie style, które znajdują się w słowniku zasobów.|
|![](../designers/media/b1_5.png "B1_5")|**Opis elementu** wyświetlić opis wybrane zasoby kategorię lub podkategorię.|

## <a name="tour-of-the-objects-and-timeline-panel"></a>Samouczek obiektów i oś czasu panelu

Organizowanie obiektów w kompozycję za pomocą tego panelu i, jeśli chcesz, aby animować je.

![Panel oś czasu i obiektów w trybie animacji](../designers/media/b5_object_timeline_animation.png "b5_object_timeline_animation")

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Widok obiektów** wyświetlanie drzewa wizualnego dokumentu. Użytkownik może przejść do szczegółów różne poziomy szczegółowości. Można również dodać warstwy do dalszego organizowanie obiektów w obszarze roboczym. W ten sposób można zablokować i ukrywać je jako grupa.|
|![](../designers/media/b1_2.png "B1_2")|**Wskaźnik trybu rekordu** Zobacz, czy rejestrowania zmian właściwości na osi czasu.|
|![](../designers/media/b1_3.png "B1_3")|**Selektor scenorysu** wyświetlić listę scenorys, które zostały utworzone.|
|![](../designers/media/b1_4.png "B1_4")|**Zamknij scenorysu** zamknąć bieżący scenorysu.|
|![](../designers/media/b1_5.png "B1_5")|**Opcje scenorysu** odwrotna duplikatów, Utwórz, Usuń, Zmień nazwę lub zamknąć scenorysu.|
|![](../designers/media/b1_6.png "B1_6")|**Formanty odtwarzania** Nawigacja w osi czasu. Można także przeciągnąć wskaźnik odtwarzania do nawigowania (lub *wyczyść*) osi czasu.|
|![](../designers/media/b1_7.png "B1_7")|**Zwraca zasięg** zakresu wyświetlić obiekty do poprzedniego obiektu głównego lub poprzednie zakresu. Można to zrobić tylko wtedy, gdy jest zmodyfikowanie stylu lub szablonie.|
|![](../designers/media/b1_8.png "B1_8")|**Zarejestruj kluczową** Zapisz migawkę właściwości obiektu wybranego w bieżącym punkcie w czasie.|
|![](../designers/media/b1_9.png "B1_9")|**Opcje przyciągania** Ustaw przyciąganie do osi czasu, rozdzielczość przyciągania i wyłącz przyciąganie do osi czasu.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Pokaż/Ukryj**, **Zablokuj/Odblokuj** Pokaż lub Ukryj widoczność i blokowanie opcji, aby wyświetlić obiekty.|
|![](../designers/media/b1_11.png "B1_11")|**Głowica położenie na osi czasu** Pokaż bieżący czas w milisekundach. Można również bezpośrednio wpisać wartości czasu w tym polu, aby przejść do określonego punktu w czasie. Dokładność zależy od rozdzielczości przystawki w **opcje przyciągania**.|
|![](../designers/media/b1_12.png "B1_12")|**Głowica** ustalić, jakie punktu w czasie animacji jest w. Przeciągając wskaźnik odtwarzania na osi czasu, można wyświetlić podgląd animacji.|
|![](../designers/media/b1_13.png "B1_13")|**Kluczowych ustawiony na osiach czasu** Zmień wartość właściwości w określonym punkcie w czasie.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Zmień kolejność obiektów** ustawić kolejność wyświetlania obiektów. Kliknij ten przycisk, aby Rozmieść obiekty w widoku struktury porządek osi (z przodu do tyłu) lub według kolejności znaczników (kolejności, w jakiej występują w **XAML** widoku).|
|![](../designers/media/b1_15.png "B1_15")|**Oś czasu powiększenia** ustawić rozdzielczość powiększenia osi czasu. Powiększanie pozwala bardziej szczegółowo edytować animację, a pomniejszenie przedstawia bardziej ogólny obraz zdarzeń w dłuższym okresie. Jeśli po powiększeniu nie można ustawić ramki kluczowej na żądanej pozycji w czasie, należy sprawdzić, czy ustawiono odpowiednio dużą rozdzielczość przyciągania.|
|![Objaśnienie 16](../designers/media/b5_label_16.png "b5_label_16")|**Oś czasu obszaru kompozycji** wyświetlanie osi czasu i przenosić kluczowych za ich pomocą ich menu skrótów.|

## <a name="tour-of-the-properties-panel"></a>Samouczek Panelu właściwości

Panel ten umożliwia wyświetlanie i modyfikowanie właściwości obiektu. Ponadto można ustawić bezpośrednio w obszarze roboczym. Jeśli to zrobisz, zmiany zostaną odzwierciedlone w **właściwości** panelu.

![Panel właściwości](../designers/media/blend5_properties_panel.png "Blend5_properties_panel")

**Kategorie** rozwijanie i zwijanie kategorie właściwości. Kliknij przycisk **rozwiń** ![ ] (../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") i **Zwiń** ![Zwiń] (../designers/media/b5_collapse_button.png "b5_collapse_button") aby pokazać lub ukryć szczegóły kategorii.

|||
|-|-|
|![](../designers/media/b1_1.png "B1_1")|**Nazwa i typ** wyświetlać ikony, nazwę i typ wybranego obiektu.|
|![](../designers/media/b1_2.png "B1_2")|**Rozmieść według** rozmieszczania właściwości w porządku alfabetycznym według nazwy, źródła lub kategorii.|
|![](../designers/media/b1_3.png "B1_3")|**Pędzel właściwości** visual właściwości pędzle, takie jak pędzla wypełnienia, obrysu pędzla i pędzla pierwszego planu.|
|![](../designers/media/b1_4.png "B1_4")|**Edytor kolor** pełnego koloru i pędzle gradientów.|
|![](../designers/media/b1_5.png "B1_5")|**Selektor kolorów** wybierz kolor.|
|![](../designers/media/b1_6.png "B1_6")|**Kolor mikroukłady** kolor początkowy, bieżący kolor i kolor ostatniego widoku|
|![](../designers/media/b1_7.png "B1_7")|**Kroplomierzy** Użyj kolor dowolny element na ekranie. **Kroplomierz kolor** jest dostępne, gdy **pędzla pełnego koloru** jest zaznaczone. **Kroplomierz gradientu** jest dostępne, gdy **pędzla gradientu** jest zaznaczone.|
|![](../designers/media/b1_8.png "B1_8")|**Właściwości i zdarzenia** właściwości lub wybierz zdarzenia dla wybranego elementu.|
|![](../designers/media/b1_9.png "B1_9")|**Pole wyszukiwania** wyszukiwać właściwości. Właściwości, które są wyświetlane, wpisując w filtru **wyszukiwania** pole.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Pędzel Edytor karty** służy do wybierania edytora pędzla. Możesz wybrać **nie pędzla**, **pędzla pełnego koloru**, **pędzla gradientu**, **Kafelek pędzla**, lub **pędzla zasobów**.|
|![](../designers/media/b1_11.png "B1_11")|**Kolor zasobów** dotyczą dokładne kolor inne właściwości. **Zasobów kolor** karta zawiera **zasobów lokalnych** i **zasobów systemowych**.|
|![](../designers/media/b1_12.png "B1_12")|**Przestrzeń kolorów RGB** zmodyfikować kolor przez dostosowanie wartości **R**, **G**, lub **B** edytory numer (czerwony, zielony, niebieski).|
|![](../designers/media/b1_13.png "B1_13")|**Kanał alfa** zmodyfikować wartości alfa za pomocą edytora numer obok **A**.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Konwertuj kolor na zasób** Konwertuj wybrany kolor na zasób koloru. Kolor zasoby są dostępne, gdy kliknij kartę Zasoby kolorów.|
|![](../designers/media/b1_15.png "B1_15")|**Wartość szesnastkowa** wyświetlić szesnastkowej wartości koloru wyświetlane.|
|![Objaśnienie 16](../designers/media/b5_label_16.png "b5_label_16")|**Suwak gradientu** jest wyświetlana tylko wtedy, gdy wybrano pędzla gradientu.|
|![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8")|**Pokaż zaawansowane właściwości** kategorii właściwości, które rzadko używane.|

**Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [panelu właściwości](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Zobacz także

- [Wstawianie kontrolek i modyfikowanie ich zachowania](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)
- [Animowanie obiektów](../designers/animate-objects-in-xaml-designer.md)
- [Rysowanie kształtów i ścieżek](../designers/draw-shapes-and-paths.md)
- [Projektowanie XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)