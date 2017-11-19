---
title: 'Krok 1: Tworzenie projektu i dodawanie etykiet do formularza | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
caps.latest.revision: "16"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 55e0802f58be0a1ad3a060fce257554b36c01a52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Krok 1. Utworzenie projektu i dodawanie etykiet do formularza
Jako pierwsze kroki w opracowywaniu kwizu tworzenia projektu i dodawanie etykiet, przycisk i innych formantów do formularza. Można również ustawić właściwości dla każdego dodawanego formantu. Projekt będzie zawierać formularz, kontrolek i (później w samouczku) kodu. Przycisk uruchamiania testu, problemy kwizu Pokaż etykiety i innych kontrolek wyświetlić odpowiedzi kwizu i czasu, który pozostaje na zakończenie kwizu.  
  
> [!NOTE]
>  Ten temat jest częścią samouczek serii o podstawowych pojęciach kodowania. Omówienie samouczka, zobacz [samouczek 2: tworzenie upłynął matematyczne quizu](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-create-a-project-and-and-set-properties-for-a-form"></a>Aby utworzyć projekt i ustaw właściwości dla formularza  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W **zainstalowane szablony** albo wybierz **C#** lub **Visual Basic**.  
  
3.  Na liście szablonów, wybierz **aplikacji formularzy systemu Windows** szablonu, nadaj jej nazwę **quizu matematyczne**, a następnie wybierz pozycję **OK** przycisku.  
  
     Formularz o nazwie **pliku Form1.cs** lub **Form1.vb** pojawia się w zależności od języka programowania, który został wybrany.  
  
4.  Wybierz formularz, a następnie zmień jego **tekst** właściwości **quizu matematyczne**.  
  
     **Właściwości** okna zawiera właściwości formularza.  
  
5.  Zmień rozmiar formularza do 500 pikseli szerokości i wysokości 400 pikseli.  
  
     Możesz zmienić rozmiar formularz przez przeciągnięcie jego krawędzi, dopóki w lewym dolnym rogu zintegrowane środowisko programistyczne (IDE) pojawi się odpowiedni rozmiar. Alternatywnie, można zmienić wartości **rozmiar** właściwości.  
  
6.  Zmień wartość **FormBorderStyle** właściwości **Fixed3D**i ustaw **MaximizeBox** właściwości **False**.  
  
     Te wartości zapobiec możliwości kwizu zmianie rozmiaru formularza.  
  
### <a name="to-create-the-time-remaining-box"></a>Aby utworzyć pole pozostałego czasu  
  
1.  Dodaj **etykiety** kontroli z przybornika, a następnie ustaw wartość jego **(nazwa)** właściwości `timeLabel`.  
  
     Etykieta staną się pole w prawym górnym rogu, który pokazuje liczbę sekund, które pozostają w kwizu.  
  
2.  Zmień **AutoSize** właściwości **False** , dzięki czemu można zmienić rozmiar pola.  
  
3.  Zmień **BorderStyle** właściwości **FixedSingle** do rysowania linii wokół pola.  
  
4.  Ustaw **rozmiar** właściwości **200, 30**.  
  
5.  Przenieś etykiety do prawego górnego rogu formularza, gdy pojawi się niebieski separator wierszy.  
  
     Te wiersze ułatwiają wyrównywanie kontrolek w formularzu.  
  
6.  W **właściwości** okna, wybierz **tekst** właściwości, a następnie wybierz pozycję klawisza, wyczyść jej wartość.  
  
7.  Wybierz znak plus (+) obok pozycji **czcionki** właściwości, a następnie zmień wartość **rozmiar** właściwości **15.75**.  
  
     Kilka właściwości czcionki, można zmienić, jak przedstawiono na poniższym obrazie.  
  
     ![Okno właściwości przedstawiający rozmiar czcionki](../ide/media/express_setfontsize.png "Express_setFontSize")  
Rozmiar czcionki przedstawiający okno właściwości  
  
8.  Dodaj inny **etykiety** kontroli z przybornika, a następnie ustaw rozmiar czcionki **15.75**.  
  
9. Ustaw **tekst** właściwości **Pozostało**.  
  
10. Przenieś etykiety tak, aby go wyrównany na lewo od **timeLabel** etykiety.  
  
### <a name="to-add-controls-for-the-addition-problems"></a>Do dodawania formantów dodanie problemów  
  
1.  Dodaj **etykiety** kontroli z przybornika, a następnie ustaw jego **tekst** właściwości **?** (znak zapytania).  
  
2.  Ustaw **AutoSize** właściwości **False**.  
  
3.  Ustaw **rozmiar** właściwości **60, 50**.  
  
4.  Ustaw rozmiar czcionki **18**.  
  
5.  Ustaw **TextAlign** właściwości **MiddleCenter**.  
  
6.  Ustaw **lokalizacji** właściwości **50, 75** umieścić kontrolkę w formularzu.  
  
7.  Ustaw **(nazwa)** właściwości **plusLeftLabel**.  
  
8.  Wybierz **plusLeftLabel** etykiety, a następnie wybierz klawiszy Ctrl + C lub **kopiowania** na **Edytuj** menu.  
  
9. Wklej etykiety trzy razy, wybierając klawisze Ctrl + V lub **Wklej** na **Edytuj** menu.  
  
10. Rozmieść trzy nowe etykiety, dzięki czemu są one w wierszu z prawej strony **plusLeftLabel** etykiety.  
  
     Separator wierszy umożliwia rozmieść je i wiersz w górę.  
  
11. Ustaw wartość etykiety drugi **tekst** właściwości  **+**  (znak plus).  
  
12. Ustaw wartość etykiety trzeci **(nazwa)** właściwości **plusRightLabel**.  
  
13. Ustaw wartość etykiety czwarty **tekst** właściwości  **=**  (znak równości).  
  
14. Dodaj **NumericUpDown** sterowania z przybornika, skonfigurować jego rozmiar czcionki **18**i ustaw jego szerokość **100**.  
  
     Dowiesz się więcej na temat tego rodzaju kontroli później.  
  
15. Wiersz w górę **NumericUpDown** formantu o formantów etykiet dodanie problemu.  
  
16. Zmień wartość **(nazwa)** właściwość **NumericUpDown** formant **suma**.  
  
     Po utworzeniu pierwszego wiersza, jak przedstawiono na poniższym obrazie.  
  
     ![Pierwszy wiersz kwizu matematycznego](../ide/media/express_firstrow.png "Express_firstRow")  
Pierwszy wiersz kwizu matematycznego  
  
### <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Do dodawania formantów problemów odejmowania, mnożenia i dzielenia  
  
1.  Skopiuj wszystkie formanty pięć problem dodawania (cztery formantów etykiet i kontrolki NumericUpDown), a następnie wklej je.  
  
     Formularz zawiera pięć nowych elementów, które nadal są wybrane.  
  
2.  Przenieś wszystkie formanty w miejscu, aby były wyrównane poniżej dodawanie formantów.  
  
     Separator wierszy umożliwia zapewniają wystarczająco dużo odległość między dwa wiersze.  
  
3.  Zmień wartość **tekst** właściwości Etykieta drugi  **-**  (znak minus).  
  
4.  Nazwa z pierwszą etykietą znaku zapytania **minusLeftLabel**.  
  
5.  Drugi etykieta znaku zapytania nazwy **minusRightLabel**.  
  
6.  Nazwa **NumericUpDown** kontroli **różnica**.  
  
7.  Wklej formanty pięć dwa razy.  
  
8.  Aby trzeciego wiersza nazw pierwsza etykieta **timesLeftLabel**, zmienić etykietę drugi **tekst** właściwości **x** (znak mnożenia), nazwę etykiety trzeci **timesRightLabel**i nazwa formantu NumericUpDown **produktu**.  
  
9. Czwartego wiersza nazwy pierwsza etykieta **dividedLeftLabel**, zmienić etykietę drugi **tekst** właściwości **÷** trzeci etykieta nazwy (znak dzielenia)  **dividedRightLabel**i nazwa formantu NumericUpDown **iloraz**.  
  
    > [!NOTE]
    >  Można skopiować z tego samouczka × znak mnożenia i ÷ znak dzielenia i wklej je do formularza.  
  
### <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Aby dodać przycisk start i ustaw kolejność indeks kolejności dostępu  
  
1.  Dodaj **przycisk** kontroli z przybornika, a następnie ustaw jego **(nazwa)** właściwości **startButton**.  
  
2.  Ustaw **tekst** właściwości **Start kwizu**.  
  
3.  Ustaw rozmiar czcionki **14**.  
  
4.  Ustaw **AutoSize** właściwości **True**, co powoduje, że przycisk, aby automatycznie Dopasuj rozmiar do tekstu.  
  
5.  Centrum przycisk w dolnej części formularza.  
  
6.  Ustaw wartość **TabIndex** właściwość **startButton** formant **1**.  
  
    > [!NOTE]
    >  **TabIndex** właściwości ustawia kolejność kontroli, gdy przyjmującego kwizu wybierze klawisz Tab. Aby zobaczyć, jak to działa, otwórz żadnych — okno dialogowe (na przykład na pasku menu wybierz **pliku**, **Otwórz**), a następnie wybierz kilkakrotnie klawisz Tab. Obejrzyj, jak kursor przesuwa między formantami zawsze wybranie klawisz Tab. Podczas tworzenia formularza programisty decyzję o kolejności.  
  
7.  Ustaw wartość **TabIndex** właściwości formantu NumericUpDown Suma do **2**, formant różnica **3**, formantu produktu do **4**, a formant iloraz **5**.  
  
     Formularz powinien wyglądać podobnie do poniższej ilustracji.  
  
     ![Początkowa formularz kwizu matematycznego](../ide/media/express_formlaidout.png "Express_FormLaidOut")  
Wstępny formularz kwizu matematycznego  
  
8.  Aby sprawdzić, czy **TabIndex** właściwości działa jak oczekiwać, Zapisz i uruchomić program, wybierając klawisz F5 lub wybierając **debugowania**, **Rozpocznij debugowanie** na pasku menu a następnie wybierz kilkakrotnie klawisz Tab.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 2: tworzenia problemu losowego dodawania](../ide/step-2-create-a-random-addition-problem.md).  
  
-   Aby powrócić do temat, zobacz [samouczek 2: tworzenie upłynął matematyczne quizu](../ide/tutorial-2-create-a-timed-math-quiz.md).