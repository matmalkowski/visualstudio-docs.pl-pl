---
title: "Krok 3: Przypisanie losowej ikony do każdej etykiety | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
caps.latest.revision: "31"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f0e594e3ef4d0b08dcd957250f7645d40f6533e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3. Przypisanie losowej ikony do każdej etykiety
Jeśli ikony w każdej grze są wyświetlane w tych samych komórkach, gra nie należy do szczególnie trudnych. Aby tego uniknąć, przypisać ikony losowo formantów etykiet w formularzu przy użyciu `AssignIconsToSquares()` metody.  
  
### <a name="to-assign-a-random-icon-to-each-label"></a>Aby przypisać losową ikonę do każdej etykiety  
  
1.  Przed dodaniem poniższego kodu, należy wziąć pod uwagę sposób działania metody. Brak nowych słów kluczowych: `foreach` języka Visual C# i `For Each` w języku Visual Basic. (Jeden z wierszy jest celowo zakomentowany, jest to wyjaśnione na końcu tej procedury.)  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]  
  
2.  Dodaj `AssignIconsToSquares()` metody, jak pokazano w poprzednim kroku. Umieść je poniżej kodzie dodanym w [krok 2: Dodawanie obiektu losowego i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
     Jak wspomniano wcześniej, coś jest nowe w Twojej `AssignIconsToSquares()` metody: `foreach` pętli języka Visual C# i `For Each` w języku Visual Basic. Można użyć `For Each` pętli w dowolnym momencie chcesz wykonać tę samą akcję wiele razy. W tym przypadku chcesz wykonać te same instrukcje dla każdej etykiety w TableLayoutPanel, jak zostało wyjaśnione przez następujący kod. Pierwszy wiersz tworzy zmienną o nazwie `control` każdej kontrolki, co który przechowuje podczas, formantem instrukcje w pętli wykonać na nim.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]  
  
    > [!NOTE]
    >  Używane są nazwy „iconLabel” (etykieta ikony) i „control” (formant), ponieważ są opisowe. Można zamiast nich użyć innych nazw, a kod zadziała dokładnie tak samo, o ile zmieni się nazwę w każdej instrukcji wewnątrz pętli.  
  
     `AssignIconsToSquares()` Metoda iteruje każdego formantu etykiety w TableLayoutPanel i wykonuje te same instrukcje dla każdego z nich. Te instrukcje ściągnięcia losowej ikony z listy, który został dodany w [krok 2: Dodawanie obiektu losowego i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (Dlatego dołączono dwie z każdej ikony na liście, aby istniała para ikon przypisanych do losowych formantów etykiet.)  
  
     Dokładniej przyjrzeć się kodu, który jest uruchamiany w `foreach` lub `For Each` pętli. Ten kod jest przedstawiony tutaj.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]  
  
     Zamienia pierwszy wiersz `control` zmiennej etykietę o nazwie `iconLabel`. Wiersz, który po `if` działał instrukcji, która sprawdza konwersji. Konwersja pracy, instrukcje w `if` Uruchom instrukcję. (Tak jak pamiętasz z poprzednich samouczków `if` używana jest instrukcja można oszacować warunku, niezależnie od użytkownika.) W pierwszym wierszu `if` instrukcja tworzy zmienną o nazwie `randomNumber` zawierający numery odnosi się do jednego z elementów na liście ikon. Aby to zrobić, używa `Next` metody `Random` obiektu, który został utworzony wcześniej. `Next` Metoda zwraca liczbę losową. Ten wiersz używa również `Count` właściwość `icons` listy do określenia zakresu do wyboru liczbę losową. Następnego wiersza przypisuje jedną ikony elementów listy, aby `Text` właściwość etykiety. Zakomentowany wiersz jest objaśniony w dalszej części tego tematu. Ponadto w ostatnim wierszu `if` instrukcji usuwa z listy ikony, który został dodany do formularza.  
  
     Należy pamiętać, że jeśli nie wiesz na pewno, co wykonuje jakaś część kodu, możesz umieścić wskaźnik myszy nad elementem kodu i przeczytać dymek z podpowiedzią. Możesz także przejrzeć każdy wiersz kodu, gdy program jest uruchomiony przy użyciu debugera Visual Studio. Zobacz [jak czy I: kroku z debugera programu Visual Studio?](http://msdn.microsoft.com/vstudio/ee672313.aspx) lub [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md) Aby uzyskać więcej informacji.  
  
3.  Aby zapełnić gier tablicy z ikonami, należy wywołać `AssignIconsToSquares()` metody zaraz po uruchomieniu programu. Jeśli używasz programu Visual C#, Dodaj instrukcję poniżej wywołanie `InitializeComponent()` metody w `Form1` *Konstruktor*, więc formularza wywołuje metodę nowych ustawień się przed rozpoczęciem jest ona wyświetlana. Konstruktory są wywoływane podczas tworzenia nowego obiektu, takiego jak klasa lub struktura. Zobacz [konstruktory (C# przewodnik programowania w języku)](http://msdn.microsoft.com/library/ace5hbzh.aspx) lub [przy użyciu konstruktory i destruktory](http://msdn.microsoft.com/library/2z08e49e.aspx) w języku Visual Basic, aby uzyskać więcej informacji.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]  
  
     W języku Visual Basic, Dodaj `AssignIconsToSquares()` wywołanie metody `Form1_Load` metody tak, aby kod wygląda podobnie do następującej.  
  
    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AssignIconsToSquares()  
    End Sub  
    ```  
  
4.  Zapisz program i go uruchom. Powinien się wyświetlić formularz z losowymi ikonami przypisanymi do każdej etykiety.  
  
5.  Zamknij program i uruchom go ponownie. Zauważ, że różne ikony są przypisywane do każdej etykiety, jak pokazano na poniższej ilustracji.  
  
     ![Dopasowywanie gry z ikonami losowe](../ide/media/express_tut4step3.png "Express_Tut4Step3")  
Gra w dopasowywanie z losowymi ikonami  
  
     Ikony są teraz widoczne, ponieważ nie zostały ukryte. Aby je ukryć odtwarzacza, należy ustawić każda etykieta `Forecolor` właściwości kolor jego `BackColor` właściwości.  
  
    > [!TIP]
    >  Innym sposobem ukrywanie formantów, takich jak etykiety jest skonfigurowanie ich **Visible** właściwości `False`.  
  
6.  Aby ukryć ikony, Zatrzymaj program i Usuń komentarz oznacza komentarze wiersza kodu wewnątrz `For Each` pętli.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]  
  
7.  Na pasku menu wybierz **Zapisz wszystko** przycisk, aby zapisać program, a następnie ją uruchom. Wygląda, jakby ikony zniknęły — widać tylko niebieskie tło. Jednakże ikony są losowo przydzielane i nadal istnieją. Ponieważ ikony mają ten sam kolor, co tło, gracz ich nie widzi. Gdyby gracz mógł od razu zobaczyć wszystkie ikony, gra nie byłaby przesadnie trudna, czyż nie?  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 4: Dodaj kliknij program obsługi zdarzeń do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2: Dodawanie obiektu losowego i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).