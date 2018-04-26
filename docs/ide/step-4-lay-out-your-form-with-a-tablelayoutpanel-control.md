---
title: Krok 4. Określenie układu formularza przy użyciu formantu TableLayoutPanel
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 983bbd00eb3ae24ef0b3c3ed932e469dbf138a2e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Krok 4. Określenie układu formularza przy użyciu formantu TableLayoutPanel
W tym kroku, możesz dodać `TableLayoutPanel` sterowania do formularza. TableLayoutPanel — pomaga prawidłowo wyrównywanie formantów w formularzu, który zostanie dodany później.  

 ![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersję wideo tego tematu, zobacz [samouczek 1: Tworzenie podglądu obrazów w języku Visual Basic - 2 wideo](http://go.microsoft.com/fwlink/?LinkId=205211) lub [samouczek 1: Tworzenie podglądu obrazów w języku C# — Wideo 2](http://go.microsoft.com/fwlink/?LinkId=205200). Tych klipów wideo korzysta z wcześniejszej wersji programu Visual Studio, dlatego są niewielkie różnice w niektórych poleceń menu i inne elementy interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.  

### <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Do określania układu formularza przy użyciu formantu TableLayoutPanel  

1.  Po lewej stronie środowiska IDE programu Visual Studio, zlokalizuj **przybornika** kartę. Wybierz **przybornika** zostanie wyświetlona karta i przybornika. (Lub na pasku menu wybierz **widoku**, **przybornika**.)  

2.  Wybierz symbol mały trójkąt obok **kontenery** grupy go otworzyć, jak pokazano na poniższej ilustracji.  

     ![Grupy kontenerów](../ide/media/express_toolbox.png "Express_Toolbox")  
Grupy kontenerów  

3.  Możesz dodać formanty, takie jak przyciski, pola wyboru i etykiet do formularza. Kliknij dwukrotnie `TableLayoutPanel` formant z przybornika. (Można także można przeciągnij formant z przybornika na formularzu). Gdy to zrobisz, dodaje IDE `TableLayoutPanel` sterowania do formularza, jak pokazano na poniższej ilustracji.  

     ![TableLayoutPanel — formant](../ide/media/express_formtablelayout.png "Express_FormTableLayout")  
TableLayoutPanel — formant  

    > [!NOTE]
    >  Po dodaniu użytkownika TableLayoutPanel, jeśli okno jest wyświetlane w formularzu z tytułem **zadania formantu TableLayoutPanel**, aby je zamknąć, a następnie wybierz dowolne miejsce w formularzu. Dowiesz się więcej na temat tego okna później w samouczku.  

     Zwróć uwagę, jak rozszerza tak, aby pokrywał formularza w przypadku jego karcie przybornika i zostanie zamknięte po wybraniu dowolnego miejsca poza programem. To funkcja autoukrywania IDE. Można włączyć ją lub wyłącz dla każdego systemu windows, wybierając ikonę pinezki w prawym górnym rogu okna, aby przełączyć autoukrywania i blokuje ją w miejscu. Ikonę pinezki wygląda następująco.  

     ![Ikonę pinezki](../ide/media/express_pushpintoolbox.png "Express_PushpinToolbox")  
Ikonę pinezki  

4.  Upewnij się, **TableLayoutPanel** jest zaznaczona, wybierając go. Można sprawdzić, jakie formant jest zaznaczony, analizując listy rozwijanej w górnej części **właściwości** okna, jak pokazano na poniższej ilustracji.  

     ![Okno właściwości formantu TableLayoutPanel przedstawiający](../ide/media/express_controlspropwin.png "Express_ControlsPropWin")  
Wyświetlanie okna właściwości formantu TableLayoutPanel  

5.  Wybierz **alfabetycznie** przycisk na pasku narzędzi w **właściwości** okna. Powoduje to, że lista właściwości w **właściwości** okno, aby wyświetlić w kolejności alfabetycznej, która ułatwi zlokalizować właściwości w tym samouczku.  

6.  Formant selektora jest listy rozwijanej w górnej części **właściwości** okna. W tym przykładzie będzie wyświetlana, że formant o nazwie `tableLayoutPanel1` jest zaznaczone. Można wybrać formantów, wybierając obszar Projektant formularzy systemu Windows lub przy użyciu selektora formantu. Teraz, gdy `TableLayoutPanel` jest zaznaczone, Znajdź **dokowania** właściwości i wybierz polecenie **dokowania**, powinien być ustawiony na **Brak**. Należy zauważyć, że strzałkę listy rozwijanej obok wartość. Wybierz strzałkę, a następnie wybierz **wypełnienia** (przycisk dużych w środku), jak pokazano na poniższej ilustracji.  

     ![Okno właściwości z wypełnieniem wybrane](../ide/media/express_docktable.png "Express_DockTable")  
Okno właściwości z wypełnieniem wybrane  

     *Dokowanie* w programie Visual Studio odwołuje się do, gdy okno jest dołączony do innego okna lub w środowisku IDE. Na przykład okna właściwości mogą być oddokowania komputera - oznacza to, odłączyć i swobodnego w programie Visual Studio — lub może być zadokowany przed **Eksploratora rozwiązań**.  

7.  Po ustawieniu TableLayoutPanel **dokowania** właściwości **wypełnienia**, panelu wypełnienia całego formularza. Jeśli rozmiar formularza ponownie, TableLayoutPanel pozostaje zadokowanych i zmienia rozmiar dopasuje.  

    > [!NOTE]
    >  Element TableLayoutPanel działa jak tabeli w programie Microsoft Word pakietu Office: istnieją wiersze i kolumny i pojedynczych komórek może obejmować wiele wierszy i kolumn. Każda komórka może zawierać jeden formant (takich jak przycisk, pole wyboru lub etykiety). Będą mieć Twoje TableLayoutPanel `PictureBox` kontroli obejmujące cały wiersz top `CheckBox` formantu w lewym dolnym komórkę i czterema `Button` formantów w prawym dolnym komórkę.  

8.  Obecnie TableLayoutPanel ma dwa wiersze rozmiar równości i dwie kolumny rozmiar równości. Należy zmienić ich rozmiar, więc w górnym wierszu i prawej kolumnie są znacznie większe. Projektant formularzy systemu Windows wybierz TableLayoutPanel. W prawym górnym rogu ma przycisku mały trójkąt czarny, która wygląda następująco.  

     ![Trójkąt](../ide/media/express_iconblacktriangle.gif "Express_IconBlackTriangle")  
Trójkąt  

     Ten przycisk oznacza, że kontrolka ma zadań, które ułatwiają automatycznie ustawienia swoich właściwości.  

9. Wybierz trójkąt, aby wyświetlić listę zadań kontroli, jak pokazano na poniższej ilustracji.  

     ![Zadania formantu TableLayoutPanel](../ide/media/express_tablepanel.png "Express_TablePanel")  
Zadania formantu TableLayoutPanel  

10. Wybierz **Edytuj wiersze i kolumny** zadanie, aby wyświetlić **Style kolumn i wierszy** okna. Wybierz **Column1**i ustaw jej rozmiar na 15 procent przez upewnić się **procent** przycisk jest zaznaczone i wprowadzanie `15` w **procent** pole. (To jest `NumericUpDown` formant, który będzie używany w samouczku nowsze.) Wybierz **Kolumna2** i równa 85%. Nie należy wybierać **OK** przycisku jeszcze, ponieważ okno zostanie zamknięte. (Ale jeśli chcesz, możesz uruchomić go za pomocą listy zadań).  

     ![Style kolumn i wierszy TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png "VS_TableLayoutPanel_Setup")  
Style kolumn i wierszy formantu TableLayoutPanel  

11. Z **Pokaż** listy rozwijanej w górnej części okna wybierz **wierszy**. Ustaw **Row1** 90 procent i **Row2** do 10 procent.  

12. Wybierz **OK** przycisku. Twoje TableLayoutPanel ma teraz dużych górny wiersz, wiersz dole małych kolumnę po lewej stronie małych i dużych prawej kolumnie. Można zmienić rozmiar wierszy i kolumn w TableLayoutPanel Wybieranie tableLayoutPanel1 w formularzu, a następnie przeciągając jego obramowania wierszy i kolumn.  

     ![Form1 o zmienionym rozmiarze TableLayoutPanel](../ide/media/vs_formafterlayoutpanel.png "VS_FormAfterLayoutPanel")  
Form1 o zmienionym rozmiarze TableLayoutPanel  

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  

-   Aby przejść do następnego kroku samouczka, zobacz [krok 5: dodawanie formantów do formularza Your](../ide/step-5-add-controls-to-your-form.md).  

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: właściwości zestawu formularza](../ide/step-3-set-your-form-properties.md).
