---
title: 'Krok 1: Tworzenie projektu i Dodawanie tabeli do formularza | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
caps.latest.revision: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: dc8def9bb088275cef9f15e4e643d6811feab462
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Krok 1. Utworzenie projektu i dodawanie tabeli do formularza
Pierwszym krokiem w tworzeniu gry w dopasowanie jest stworzenie projektu i dodanie tabeli do formularza. Tabela ułatwia wyrównywanie ikon w uporządkowaną siatkę 4x4. Można również ustawić kilka właściwości, aby poprawić wygląd planszy gry.  
  
### <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Aby utworzyć projekt i dodać tabelę do formularza  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Jeśli nie używasz programu Visual Studio Express, musisz najpierw wybrać język programowania. Z **zainstalowane szablony** albo wybierz **Visual C#** lub **Visual Basic**.  
  
3.  Na liście szablony projektów, wybierz **aplikacji Windows Forms**, nazwij projekt **MatchingGame**, a następnie wybierz pozycję **OK** przycisku.  
  
4.  W **właściwości** okna, ustaw następujące właściwości formularza.  
  
    1.  Zmień formularza **tekst** właściwość z **Form1** do **dopasowania gry**. Ten tekst jest wyświetlany w górnej części okna gry.  
  
    2.  Ustaw rozmiar formularza na 550 pikseli szerokości i 550 pikseli wysokości. Można to zrobić przez ustawienie **rozmiar** właściwości **550, 550**, lub przeciągając rogu formularza, aż zostanie wyświetlony odpowiedni rozmiar w prawym dolnym rogu (środowisko rozwoju zintegrowane IDE).  
  
5.  Wyświetlanie Przybornika, wybierając **przybornika** karcie po lewej stronie IDE.  
  
6.  Przeciągnij `TableLayoutPanel` kontrolować z **kontenery** kategorii w przyborniku, a następnie ustaw następujące właściwości dla niego.  
  
    1.  Ustaw **BackColor** właściwości **CornflowerBlue**. Aby to zrobić, otwórz **BackColor** okno dialogowe, wybierając strzałkę listy rozwijanej obok pola **BackColor** właściwości w **właściwości** okna.  Następnie wybierz pozycję **Web** karcie **BackColor** okno dialogowe, aby wyświetlić listę nazw dostępnych kolorów.  
  
        > [!NOTE]
        >  Kolory nie są w kolejności alfabetycznej, a CornflowerBlue jest w dolnej części listy.  
  
    2.  Ustaw **dokowania** właściwości **wypełnienia** wybierając przycisk listy rozwijanej obok właściwości i wybierając pozycję dużych środkowego przycisku. Tabela się rozszerza i obejmuje cały formularz.  
  
    3.  Ustaw **CellBorderStyle** właściwości **wstawki**. Zapewnia to wizualne granice pomiędzy poszczególnymi komórkami na planszy.  
  
    4.  Kliknij przycisk trójkąta w prawym górnym rogu formantu TableLayoutPanel, aby wyświetlić jego menu zadań.  
  
    5.  W menu zadania wybierz **Dodaj wiersz** dwa razy, aby dodać dwa więcej wierszy, a następnie wybierz **Dodaj kolumnę** dwa razy, aby dodać dwie kolumny.  
  
    6.  W menu zadania wybierz **Edytuj wiersze i kolumny** otworzyć **Style kolumn i wierszy** okna. Wybieranie każdej kolumny, **procent** przycisk opcji, a następnie ustaw szerokość każdej kolumny na 25 procent łączna szerokość. Następnie wybierz **wierszy** z listy rozwijanej pola w górnej części okna, a wartość 25 procent wysokość każdego wiersza. Gdy wszystko będzie gotowe, wybierz pozycję **OK** przycisku.  
  
     TableLayoutPanel powinien być teraz siatką 4 x 4, o szesnastu kwadratowych komórkach równej wielkości. Te wiersze i kolumny są tam, gdzie później pojawią się obrazy ikon.  
  
7.  Należy się upewnić, że TableLayoutPanel jest zaznaczony w edytorze formularza. Aby to sprawdzić, powinien zostać wyświetlony **tableLayoutPanel1** w górnej części **właściwości** okna. Jeśli nie jest wybrana, wybierz TableLayoutPanel w formularzu lub go za pomocą kontrolki rozwijanej na górze **właściwości** okna.  
  
     Gdy TableLayoutPanel jest zaznaczony, otwórz przybornika i dodać **etykiety** formantu (znajdujące się w **formanty standardowe** kategorii) do lewej górnej komórki TableLayoutPanel. `Label` Kontroli powinny teraz być zaznaczone w IDE. Ustaw dla niego następujące właściwości.  
  
    1.  Upewnij się, że etykiety **BackColor** właściwość jest ustawiona na **CornflowerBlue**.  
  
    2.  Ustaw **AutoSize** właściwości **False**.  
  
    3.  Ustaw **dokowania** właściwości **wypełnienia**.  
  
    4.  Ustaw **TextAlign** właściwości **MiddleCenter** wybierając przycisk listy rozwijanej obok właściwości, a następnie wybierając środkowego przycisku. Gwarantuje to, że ikona pojawia się w środku komórki.  
  
    5.  Wybierz **czcionki** właściwości. Przycisk wielokropka (...) powinny być wyświetlane.  
  
    6.  Wybierz przycisk wielokropka i ustaw **czcionki** do wartości **Webdings**, **styl czcionki** do **Bold**i **rozmiar** do **72**.  
  
    7.  Ustaw **tekst** właściwość etykiety litera **c**.  
  
         Lewa górna komórka w TableLayoutPanel powinna teraz zawierać czarne pole wyśrodkowane na niebieskim tle.  
  
        > [!NOTE]
        >  Czcionka Webdings to czcionka ikon, która jest dostarczana z systemem operacyjnym Windows. W grze w dopasowywanie, gracz musi dopasować pary ikon, więc ta czcionka jest używana do wyświetlania dopasowywanych ikon. Zamiast wprowadzania **c** w **tekst** właściwości, spróbuj wprowadzić innego litery, aby zobaczyć, jakie ikony są wyświetlane. Znak wykrzyknika to pająk, wielkie N to oko, a przecinek to papryczka chili.  
  
8.  Wybierz formant etykiety i skopiuj go do następnej komórki w TableLayoutPanel. (Wybierz klawiszy Ctrl + C lub na pasku menu **Edytuj**, **kopiowania**.) Następnie wklej go. (Wybierz klawiszy Ctrl + V lub na pasku menu **Edytuj**, **Wklej**.) W drugiej komórce TableLayoutPanel pojawi się kopia pierwszej etykiety. Wklej ją ponownie, w trzeciej komórce pojawi się kolejna etykieta. Zachowaj wklejanie `Label` kontrolki, dopóki wszystkie komórki są wypełnione.  
  
    > [!NOTE]
    >  Jeśli wkleisz zbyt wiele razy, IDE doda nowy wiersz do TableLayoutPanel, aby zrobić miejsce na dodanie nowego formantu etykiety. Można cofnąć tę operację. Aby usunąć nowych komórek, wybierz klawiszy Ctrl + Z lub na pasku menu **Edytuj**, **Cofnij**.  
  
     Teraz formularz jest rozmieszczony. Powinien wyglądać tak, jak na poniższej ilustracji:  
  
     ![Początkowa dopasowania formularz gry](../ide/media/express_tut4step1.png "Express_Tut4Step1")  
Początkowy formularz gry w dopasowywanie  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 2: Dodawanie obiektu losowego i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
-   Aby powrócić do temat, zobacz [3 samouczek: tworzenie gier dopasowania](../ide/tutorial-3-create-a-matching-game.md).