---
title: "Krok 5: Dodawanie odwołań do etykiet | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
caps.latest.revision: "20"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f353693fe407600b7ed009e611600a8b42c7713d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="step-5-add-label-references"></a>Krok 5. Dodawanie odwołań do etykiet
Program musi śledzić, które formanty etykiet wybiera gracz. W tej chwili program pokazuje wszystkie etykiety wybrane przez gracza. Ale zaraz to zmienimy. Po wybraniu pierwszej etykiety program powinien wyświetlać ikonę etykiety. Po wybraniu drugiej etykiety program powinien wyświetlić obie ikony przez krótki czas i potem ponownie je ukryć. Program będzie teraz zachować informacje o formantu etykiety, który jest wybierany najpierw i który jest wybierany sekundę przy użyciu *odwoływać się do zmiennych*.  
  
### <a name="to-add-label-references"></a>Aby dodać odwołania do etykiet  
  
1.  Dodaj odwołania do etykiet do formularza przy użyciu następującego kodu.  
  
     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]  
  
     Zmienne odwołujące się do tych wyglądać podobnie do instrukcji wcześniej używane do dodawania obiektów (takich jak `Timer` obiektów, `List` obiektów, a `Random` obiektów) do formularza. Jednak te instrukcje nie powodują dwóch formantów dodatkowych etykietę do wyświetlane w formularzu, ponieważ nie istnieje żadne `new` słowo kluczowe użyte w jednej z dwóch instrukcje. Bez `new` — słowo kluczowe, obiekt nie jest tworzony. Dlatego `firstClicked` i `secondClicked` są nazywane zmienne odwołujące się do: one tylko śledzić (lub dotyczą) `Label` obiektów.  
  
     Jeśli zmienna nie jest rejestrowanie informacji o obiekcie, ma ustawioną wartością zastrzeżoną specjalne: `null` języka Visual C# i `Nothing` w języku Visual Basic. Tak, po uruchomieniu programu zarówno `firstClicked` i `secondClicked` ustawiono `null` lub `Nothing`, co oznacza, że zmienne nie są rejestrowanie informacji o żadnych czynności.  
  
2.  Modyfikowanie programu obsługi zdarzeń kliknięcia do używania nowych `firstClicked` odwołanie do zmiennej. Usuń ostatnią instrukcją w `label_Click()` metoda obsługi zdarzeń (`clickedLabel.ForeColor = Color.Black;`) i zastąpić go ciągiem `if` instrukcji, która jest zgodna. (Pamiętaj, że to komentarz i całego `if` instrukcji.)  
  
     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]  
  
3.  Zapisz i uruchom program. Wybierz jeden z formantów etykiet, pojawi się jego ikona.  
  
4.  Wybierz następny formant etykiety i zauważ, że nic się nie dzieje. Program jest już rejestrowanie informacji o pierwszej etykietę, którą otwarto odtwarzacza, dlatego `firstClicked` nie jest równa `null` języka Visual C# lub `Nothing` w języku Visual Basic. Gdy Twoje `if` instrukcji kontroli `firstClicked` do określenia, czy jest równa `null` lub `Nothing`, stwierdzi, że nie jest i nie wykonać instrukcje w `if` instrukcji. Tak więc, tylko pierwsza wybrana ikona zmienia kolor na czarny, a inne ikony są niewidoczne, jak pokazano na poniższej ilustracji.  
  
     ![Dopasowywanie gry wyświetlanie ikon](../ide/media/express_tut4step5.png "Express_Tut4Step5")  
Gra w dopasowywanie pokazująca jedną ikonę  
  
     W następnym kroku samouczka będziesz rozwiązać problem, dodając **czasomierza** formantu.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 6: Dodawanie czasomierza](../ide/step-6-add-a-timer.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4: Dodaj kliknij program obsługi zdarzeń do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).