---
title: "Modyfikowanie stylu obiektów w programie Blend | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0133ced82f35a8daefeb3dcaaacd4822f5cad345
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="modify-the-style-of-objects-in-blend"></a>Modyfikowanie stylu obiektów w programie Blend
Najprostszym sposobem dostosowania obiektu jest można ustawić właściwości **właściwości** okienka.  
  
 Jeśli chcesz ponownie użyć ustawień lub grupy ustawień, utwórz zasób wielokrotnego użytku. Może to być *styl*, *szablonu*, lub coś prosty przykład niestandardowego koloru. Należy również wybrać formant są wyświetlane inaczej na podstawie jego stanu. Na przykład przycisk włącza zielony, gdy użytkownik kliknie przycisk.  
  
 **W tym temacie**:  
  
-   [Pędzle: Zmodyfikować wygląd obiektu](#Brushes)  
  
-   [Szablony i style: utworzyć spójny wygląd i zachowanie różnych formantów](#Styles)  
  
-   [Stany wizualne: Zmienianie wyglądu formantu na podstawie stanu](#Visual)  
  
-   [Zasoby: Tworzenie kolory, style i szablony i używać ich ponownie później](#Resources)  
  
##  <a name="Brushes"></a>Pędzle: Zmodyfikować wygląd obiektu  
 Jeśli chcesz zmienić jego wygląd, zastosuj pędzla do obiektu.  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Edytor pędzle](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).  
  
### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Malowanie identycznych obrazu lub wzorca na obiekt  
 Malowanie identycznych obrazu lub wzorca na obiekt przy użyciu *Kafelek pędzla*.  
  
 Aby utworzyć pędzla kafelka, Rozpocznij od utworzenia *obrazu pędzla*, *pędzla do rysowania*, lub *pędzla visual* zasobów.  
  
 Tworzenie pędzla obrazu przy użyciu obrazu. Na poniższych ilustracjach przedstawiono pędzla obrazu, pędzla obraz rozmieszczany i pędzla obrazu odwrócony.  
  
 ![](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png "81f84f56-906d-456b-8288-d77da1e01e31") ![](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png "d3782ca8-64da-47a4-a095-c6cdd0fa47a2") ![](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png "38ae3691-f3f1-4a1e-82ca-c7fa164bf56e")  
  
 Tworzenie pędzla Rysowanie za pomocą wektorowej, takich jak ścieżki lub kształtu. Na poniższych ilustracjach przedstawiono rysowania pędzla, rysowania pędzla rozmieszczany i rysowania pędzla odwrócony.  
  
 ![](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png "197666ac-ef57-4c5c-9779-669e991a00a5") ![](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png "ba09cda3-4cee-40ba-b3d4-edc032158bdc") ![](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png "15bf6021-620c-4490-9eae-086153d3f14f")  
  
 Tworzenie pędzla visual z formantu, takie jak przycisk. Na poniższych ilustracjach przedstawiono visual pędzla i pędzla visual wypełniania.  
  
 ![](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png "fb6c90e0-153c-48fe-b563-e601beac6227")![](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png "e261b99f-7d8f-4d91-bc84-19c7beccc255")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pędzle kafelka](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).  
  
##  <a name="Styles"></a>Szablony i style: utworzyć spójny wygląd i zachowanie różnych formantów  
 Można zaprojektować wygląd i zachowanie formantu jeden raz i dotyczą tego projektu innych kontrolek tak, aby nie trzeba zachować je oddzielnie.  
  
 **Należy użyć stylu?** : Jeśli chcesz ustawić właściwości domyślnej (na przykład kolor przycisku), użyj *styl*. Można zmodyfikować formantu, nawet po zastosowaniu stylu do niego.  
  
 **Należy użyć szablonu?** : Jeśli chcesz zmienić struktury formantu, użyj *szablonu*. Wyobraź sobie Konwertowanie grafiki lub logo do przycisku. Nie można zmodyfikować formantu, po zastosowaniu szablonu do niego.  
  
### <a name="create-a-template-or-style"></a>Tworzenie szablonu lub stylu  
 Ma dwa sposoby tworzenia szablonu. Dowolny obiekt można przekonwertować na kompozycję do formantu lub można utworzyć nowy szablon formant.  
  
 Aby przekonwertować szablon formantu dowolnego obiektu, wybierz obiekt, a następnie na **narzędzia** menu, wybierz **należy do formantu**.  
  
 Jeśli chcesz utworzyć nowy szablon formant, wybierz obiekt, w obszarze roboczym. Następnie w górnej części obszaru roboczego, wybierz przycisk stron nadrzędnych wybierz pozycję **Edytuj szablon**, a następnie wybierz pozycję **edytowania kopii** lub **Utwórz pusty**.  
  
 ![](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png "5ebdb33f-aad2-4c10-a328-5e8b04c56a36")  
  
 Aby utworzyć styl, wybierz obiekt, a następnie w **obiektu** menu, wybierz **Edytuj styl**, a następnie wybierz **edytowania kopii** lub **Utwórz pusty**.  
  
-   Wybierz **edytowania kopii** można uruchomić z domyślnym stylu lub szablonie formantu.  
  
-   Wybierz **Utwórz pusty** od samego początku.  
  
 **Edytuj bieżący** opcja jest dostępna tylko wtedy, gdy Edytuj stylu lub szablonie, który został już utworzony. Nie będzie on widoczny dla formantu, który jest nadal przy użyciu domyślnego szablonu systemu.  
  
 W **tworzenia zasobów stylu** okno dialogowe, można albo nazwę stylu lub szablonie, aby można jej użyć później, lub stylu lub szablonie można zastosować do wszystkich formantów tego typu.  
  
 ![](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png "4818ee6a-ce60-4b79-91c8-3b1871829eea")  
  
> [!NOTE]
>  Nie można utworzyć style lub szablonów dla każdego typu formantu. Jeśli ich nie obsługuje formantu, przycisk stron nadrzędnych nie pojawi się powyżej obszaru roboczego.  
>   
>  Aby powrócić do edytowania zakresu głównego dokumentu, kliknij przycisk **zwracać zasięg** ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3-ed98-4f20-aa66-a6f5b23eeb2b").  
>   
>  ![](../designers/media/4a5612e1-7a28-4587-b870-0fe7112ec2ad.png "4a5612e1-7a28-4587-b870-0fe7112ec2ad")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Tworzenie stylu](http://www.microsoft.com/showcase/details.aspx?uuid=9b8e86e2-8e90-4d61-81af-fa5b5afb3e95).  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [tworzenia szablonu formantu w Expression Blend](http://msdn.microsoft.com/expression/cc263912.aspx).  
  
### <a name="apply-a-style-or-template-to-a-control"></a>Stosowanie stylu lub szablonie do formantu  
 Kliknij prawym przyciskiem myszy obiekt w [oś czasu i obiekty](http://msdn.microsoft.com/en-us/135a5a5e-ec6d-4f38-8827-60e284cd5f57) panelu, wybierz polecenie **Edytuj szablon**, a następnie wybierz **zastosować zasobów**.  
  
 ![](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png "dc12debc-7711-47d9-84ce-10322a384397")  
  
### <a name="restore-the-default-style-or-template-of-a-control"></a>Przywracanie domyślnego stylu lub szablonie formantu  
 Wybierz kontrolkę i w [właściwości](http://msdn.microsoft.com/en-us/135a5a5e-ec6d-4f38-8827-60e284cd5f57) panelu, Znajdź **styl** lub **szablonu** właściwości. Następnie kliknij przycisk **zaawansowane opcje** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962-5d8a-480d-a837-e06b84c545bb"), a następnie kliknij przycisk **zresetować** menu skrótów.  
  
##  <a name="Visual"></a>Stany wizualne: Zmienianie wyglądu formantu na podstawie stanu  
 Formanty mogą mieć inny wygląd visual na podstawie interakcji użytkownika. Na przykład możesz wprowadzić przycisk włączyć zielony, gdy użytkownik kliknie go lub można uruchomić animacji. Skróć lub wydłużyć czas między stany wizualne przy użyciu przejścia.  
  
 ![](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png "a95c671a-5639-40b9-83db-1e6b214330d5")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [zarządzania stanem formantów WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).  
  
##  <a name="Resources"></a>Zasoby: Tworzenie kolory, style i szablony i używać ich ponownie później  
 Wszystko, co można przekształcić w projekcie do zasobu. Zasób jest tylko obiekt, który można użyć ponownie w różnych miejscach w aplikacji. Można na przykład utworzyć kolor jeden raz, stał się zasób, a następnie użyć koloru w kilku obiektach. Aby zmienić kolor wszystkich tych obiektów, można zmienić kolor zasobów.  
  
 ![](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png "89203705-cf66-46e0-b153-52a23cd744f7")![](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png "6bff8b19-3cd5-41a0-bbf9-ff65532d5aae")  
  
 **Obejrzyj krótki klip wideo:** ![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [krótki touch zasobów](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)