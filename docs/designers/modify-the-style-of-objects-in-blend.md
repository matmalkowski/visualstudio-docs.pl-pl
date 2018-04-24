---
title: Modyfikowanie stylu obiektów w programie Blend
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd96bde626f70211e1698227a8f94df75e3bcb3c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="modify-the-style-of-objects-in-blend"></a>Modyfikowanie stylu obiektów w programie Blend

Najprostszym sposobem dostosowania obiektu jest można ustawić właściwości **właściwości** okienka.

Jeśli chcesz ponownie użyć ustawień lub grupy ustawień, utwórz zasób wielokrotnego użytku. Może to być *styl*, *szablonu*, lub coś prosty przykład niestandardowego koloru. Należy również wybrać formant są wyświetlane inaczej na podstawie jego stanu. Na przykład przycisk włącza zielony, gdy użytkownik kliknie przycisk.

## <a name="brushes-modify-the-appearance-of-an-object"></a>Pędzle: Zmodyfikować wygląd obiektu

Jeśli chcesz zmienić jego wygląd, zastosuj pędzla do obiektu.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Malowanie identycznych obrazu lub wzorca na obiekt

Malowanie identycznych obrazu lub wzorca na obiekt przy użyciu *Kafelek pędzla*.

Aby utworzyć pędzla kafelka, Rozpocznij od utworzenia *obrazu pędzla*, *pędzla do rysowania*, lub *pędzla visual* zasobów.

Tworzenie pędzla obrazu przy użyciu obrazu. Na poniższych ilustracjach przedstawiono pędzla obrazu, pędzla obraz rozmieszczany i pędzla obrazu odwrócony.

![Pędzel obrazu](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![Pędzel obraz sąsiadująco](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![Odwrócony pędzla obrazu](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

Tworzenie pędzla Rysowanie za pomocą wektorowej, takich jak ścieżki lub kształtu. Na poniższych ilustracjach przedstawiono rysowania pędzla, rysowania pędzla rozmieszczany i rysowania pędzla odwrócony.

![Pędzla do rysowania](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![Rysowanie pędzla sąsiadująco](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![Odwrócony pędzla do rysowania](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

Tworzenie pędzla visual z formantu, takie jak przycisk. Na poniższych ilustracjach przedstawiono visual pędzla i pędzla visual wypełniania.

![Pędzel Visual](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![Pędzel Visual sąsiadująco](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>Szablony i style: utworzyć spójny wygląd i zachowanie różnych formantów

Można zaprojektować wygląd i zachowanie formantu jeden raz i dotyczą tego projektu innych kontrolek tak, aby nie trzeba zachować je oddzielnie.

**Należy użyć stylu?** : Jeśli chcesz ustawić właściwości domyślnej (na przykład kolor przycisku), użyj *styl*. Można zmodyfikować formantu, nawet po zastosowaniu stylu do niego.

**Należy użyć szablonu?** : Jeśli chcesz zmienić struktury formantu, użyj *szablonu*. Wyobraź sobie Konwertowanie grafiki lub logo do przycisku. Nie można zmodyfikować formantu, po zastosowaniu szablonu do niego.

### <a name="create-a-template-or-style"></a>Tworzenie szablonu lub stylu

Dostępne są dwa sposoby tworzenia szablonu. Dowolny obiekt można przekonwertować na kompozycję do formantu lub można utworzyć nowy szablon formant.

Aby przekonwertować szablon formantu dowolnego obiektu, wybierz obiekt, a następnie na **narzędzia** menu, wybierz **należy do formantu**.

Jeśli chcesz utworzyć nowy szablon formant, wybierz obiekt, w obszarze roboczym. Następnie w górnej części obszaru roboczego, wybierz przycisk stron nadrzędnych wybierz pozycję **Edytuj szablon**, a następnie wybierz pozycję **edytowania kopii** lub **Utwórz pusty**.

![Edytuj szablon menu](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

Aby utworzyć styl, wybierz obiekt, a następnie w **obiektu** menu, wybierz **Edytuj styl**, a następnie wybierz **edytowania kopii** lub **Utwórz pusty**.

- Wybierz **edytowania kopii** można uruchomić z domyślnym stylu lub szablonie formantu.

- Wybierz **Utwórz pusty** od samego początku.

**Edytuj bieżący** opcja jest dostępna tylko wtedy, gdy Edytuj stylu lub szablonie, który został już utworzony. Nie będzie on widoczny dla formantu, który jest nadal przy użyciu domyślnego szablonu systemu.

W **tworzenia zasobów stylu** okno dialogowe, można albo nazwę stylu lub szablonie, aby można jej użyć później, lub stylu lub szablonie można zastosować do wszystkich formantów tego typu.

![Utwórz zasób stylu — okno dialogowe](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> Nie można utworzyć style lub szablonów dla każdego typu formantu. Jeśli ich nie obsługuje formantu, przycisk stron nadrzędnych nie pojawi się powyżej obszaru roboczego.
> Aby powrócić do edytowania zakresu głównego dokumentu, kliknij przycisk **zwracać zasięg** ![zwracać zakresu ikonę](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png).

### <a name="apply-a-style-or-template-to-a-control"></a>Stosowanie stylu lub szablonie do formantu

Kliknij prawym przyciskiem myszy obiekt w [oś czasu i obiekty](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-objects-and-timeline-panel) panelu, wybierz polecenie **Edytuj szablon**, a następnie wybierz **zastosować zasobów**.

![Zastosuj menu zasobów](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>Przywracanie domyślnego stylu lub szablonie formantu

Wybierz kontrolkę i w [właściwości](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-properties-panel) panelu, Znajdź **styl** lub **szablonu** właściwości. Wybierz **zaawansowane opcje**, a następnie kliknij przycisk **zresetować** menu skrótów.

## <a name="visual-states-change-the-appearance-of-a-control-based-on-its-state"></a>Stany wizualne: Zmienianie wyglądu formantu oparte na stanie

Formanty mogą mieć inny wygląd visual na podstawie interakcji użytkownika. Na przykład możesz wprowadzić przycisk włączyć zielony, gdy użytkownik kliknie go lub uruchomić animacji. Skróć lub wydłużyć czas między stany wizualne przy użyciu przejścia.

![Wskaźnik myszy na stan](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**Obejrzyj krótki klip wideo:** ![przycisk Odtwórz](../designers/media/bldadminconsoleinitialconfigicon.PNG) [zarządzania stanem formantów WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>Zasoby: Tworzenie kolory, style i szablony i używać ich ponownie później

Wszystko, co można przekształcić w projekcie do zasobu. Zasób jest tylko obiekt, który można użyć ponownie w różnych miejscach w aplikacji. Można na przykład utworzyć kolor jeden raz, stał się zasób, a następnie użyć koloru w kilku obiektach. Aby zmienić kolor wszystkich tych obiektów, można zmienić kolor zasobów.

![Konwertuj kolor na zasób przycisku](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![Utwórz zasób koloru — okno dialogowe](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)