---
title: 'Krok 3: Przypisanie losowej ikony do każdej etykiety'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8aac613f4fe8a93ebd31127e26bcd92218b6300
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748247"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3: Przypisanie losowej ikony do każdej etykiety
Jeśli ikony w każdej grze są wyświetlane w tych samych komórkach, gra nie należy do szczególnie trudnych. Aby tego uniknąć, przypisać ikony losowo formantów etykiet w formularzu przy użyciu `AssignIconsToSquares()` metody.

## <a name="to-assign-a-random-icon-to-each-label"></a>Aby przypisać losową ikonę do każdej etykiety

1.  Przed dodaniem poniższego kodu, należy wziąć pod uwagę sposób działania metody. Brak nowych słów kluczowych: `foreach` języka Visual C# i `For Each` w języku Visual Basic. (Jeden z wierszy jest celowo zakomentowany, jest to wyjaśnione na końcu tej procedury.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

2.  Dodaj `AssignIconsToSquares()` metody, jak pokazano w poprzednim kroku. Umieść je poniżej kodzie dodanym w [krok 2: Dodawanie obiektu losowe i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Jak wspomniano wcześniej, coś jest nowe w Twojej `AssignIconsToSquares()` metody: `foreach` pętli języka Visual C# i `For Each` w języku Visual Basic. Można użyć `For Each` pętli w dowolnym momencie chcesz wykonać tę samą akcję wiele razy. W takim przypadku ma do wykonania tych samych instrukcji dla każdej etykiety na Twojej <xref:System.Windows.Forms.TableLayoutPanel>, zgodnie z objaśnieniem w następującym kodem. Pierwszy wiersz tworzy zmienną o nazwie `control` każdej kontrolki, co który przechowuje podczas, formantem instrukcje w pętli wykonać na nim.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    >  Używane są nazwy „iconLabel” (etykieta ikony) i „control” (formant), ponieważ są opisowe. Można zamiast nich użyć innych nazw, a kod zadziała dokładnie tak samo, o ile zmieni się nazwę w każdej instrukcji wewnątrz pętli.

     `AssignIconsToSquares()` Metoda iteruje każdego formantu etykiety w TableLayoutPanel i wykonuje te same instrukcje dla każdego z nich. Te instrukcje ściągnięcia losowej ikony z listy, który został dodany w [krok 2: Dodawanie obiektu losowe i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (Dlatego dwa każda z ikon uwzględnione na liście, więc byłoby parę ikony przypisane do losowe etykiety kontrolki.)

     Dokładniej przyjrzeć się kodu, który jest uruchamiany w `foreach` lub `For Each` pętli. Ten kod jest przedstawiony tutaj.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     Zamienia pierwszy wiersz **kontroli** zmiennej etykietę o nazwie **iconLabel**. Wiersz, który po `if` działał instrukcji, która sprawdza konwersji. Konwersja pracy, instrukcje w `if` Uruchom instrukcję. (Tak jak pamiętasz z poprzednich samouczków `if` używana jest instrukcja można oszacować warunku, niezależnie od użytkownika.) W pierwszym wierszu `if` instrukcja tworzy zmienną o nazwie **randomNumber** zawierający numery odnosi się do jednego z elementów na liście ikon. Aby to zrobić, używa <xref:System.Random.Next> metody <xref:System.Random> obiektu, który został utworzony wcześniej. `Next` Metoda zwraca liczbę losową. Ten wiersz używa również <xref:System.Collections.Generic.List%601.Count> właściwość **ikony** listy do określenia zakresu do wyboru liczbę losową. Następnego wiersza przypisuje jedną ikony elementów listy, aby <xref:System.Windows.Forms.Label.Text> właściwość etykiety. Zakomentowany wiersz jest objaśniony w dalszej części tego tematu. Ponadto w ostatnim wierszu `if` instrukcji usuwa z listy ikony, który został dodany do formularza.

     Należy pamiętać, że jeśli nie wiesz na pewno, co wykonuje jakaś część kodu, możesz umieścić wskaźnik myszy nad elementem kodu i przeczytać dymek z podpowiedzią. Możesz także przejrzeć każdy wiersz kodu, gdy program jest uruchomiony przy użyciu debugera Visual Studio. Zobacz [jak wykonać krok i. za pomocą debugera programu Visual Studio?](http://msdn.microsoft.com/vstudio/ee672313.aspx) lub [Nawigacja w kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md) Aby uzyskać więcej informacji.

3.  Aby zapełnić gier tablicy z ikonami, należy wywołać `AssignIconsToSquares()` metody zaraz po uruchomieniu programu. Jeśli używasz programu Visual C#, Dodaj instrukcję poniżej wywołanie `InitializeComponent()` metoda **Form1 *** Konstruktor*, więc formularza wywołuje metodę nowych ustawień się przed rozpoczęciem jest ona wyświetlana. Konstruktory są wywoływane podczas tworzenia nowego obiektu, takiego jak klasa lub struktura. Zobacz [konstruktory (C# programowania przewodnik)](http://msdn.microsoft.com/library/ace5hbzh.aspx) lub [Użyj konstruktory i destruktory](http://msdn.microsoft.com/library/2z08e49e.aspx) w języku Visual Basic, aby uzyskać więcej informacji.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     W języku Visual Basic, Dodaj `AssignIconsToSquares()` wywołanie metody `Form1_Load` metody tak, aby kod wygląda podobnie do następującej.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4.  Zapisz program i go uruchom. Powinien się wyświetlić formularz z losowymi ikonami przypisanymi do każdej etykiety.

5.  Zamknij program i uruchom go ponownie. Zauważ, że różne ikony są przypisywane do każdej etykiety, jak pokazano na poniższej ilustracji.

     ![Dopasowywanie gry z ikonami losowe](../ide/media/express_tut4step3.png) dopasowania gry losowej ikony

     Ikony są teraz widoczne, ponieważ nie zostały ukryte. Aby je ukryć odtwarzacza, należy ustawić każda etykieta **ForeColor** właściwości kolor jego **BackColor** właściwości.

    > [!TIP]
    >  Innym sposobem ukrywanie formantów, takich jak etykiety jest skonfigurowanie ich **Visible** właściwości **False**.

6.  Aby ukryć ikony, Zatrzymaj program i Usuń komentarz oznacza komentarze wiersza kodu wewnątrz `For Each` pętli.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7.  Na pasku menu wybierz **Zapisz wszystko** przycisk, aby zapisać program, a następnie ją uruchom. Wygląda, jakby ikony zniknęły — widać tylko niebieskie tło. Jednakże ikony są losowo przydzielane i nadal istnieją. Ponieważ ikony mają ten sam kolor, co tło, gracz ich nie widzi. Gdyby gracz mógł od razu zobaczyć wszystkie ikony, gra nie byłaby przesadnie trudna, czyż nie?

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 4: Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2: Dodawanie obiektu losowe i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
