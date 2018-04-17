---
title: 'Krok 3: Dodawanie czasomierza odliczania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15f398aa90ea4565fea5645abeb1b2570a7ffc29
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="step-3-add-a-countdown-timer"></a>Krok 3. Dodawanie czasomierza odliczania
W trzeciej części tego samouczka zostanie dodana czasomierza odliczania śledzić liczbę sekund, które pozostają dla przyjmującego testu zakończyć.  
  
> [!NOTE]
>  Ten temat jest częścią samouczek serii o podstawowych pojęciach kodowania. Omówienie samouczka, zobacz [samouczek 2: tworzenie upłynął matematyczne quizu](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-add-a-countdown-timer"></a>Aby dodać czasomierza odliczania  
  
1.  Dodaj zmienną liczbą całkowitą o nazwie **timeLeft**, podobnie jak w poprzedniej procedurze. Kod powinien wyglądać podobnie jak poniżej.  
  
     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]  
  
     Teraz należy metodę, która faktycznie liczby sekund, takich jak czasomierz, który wywołuje zdarzenie po ilość czasu, który określisz.  
  
2.  W oknie projektowania Przenieś `Timer` kontrolować z **składniki** kategorii przybornika do formularza.  
  
     Kontrolka jest wyświetlana w obszarze szarego w dolnej części okna projektu.  
  
3.  W formularzu, należy wybrać **czasomierz 1** ikona, który został właśnie dodany i ustaw jej **interwał** właściwości **1000**.  
  
     Ponieważ wartość interwału MS, wartość 1000 powoduje zdarzeń Tick uruchomienie w ciągu sekundy.  
  
4.  W formularzu kliknij dwukrotnie formant czasomierza lub wybierz ją, a następnie wybierz klawisz Enter.  
  
     Edytor kodu zostanie wyświetlony i metoda obsługi zdarzeń znaczników, który właśnie został dodany.  
  
5.  Dodaj następujące instrukcje, aby nowa metoda obsługi zdarzeń.  
  
     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]  
  
     W oparciu o zostały dodane, czasomierza sprawdza każdej sekundzie, czy czas wyczerpała się przez określenie czy **timeLeft** zmienna całkowitoliczbowa jest większa niż 0. Jeśli tak jest, czas nadal pozostaje. Czasomierz najpierw odejmuje 1 z timeLeft, a następnie aktualizuje **tekst** właściwość `timeLabel` formantu, aby pokazać przyjmującego kwizu pozostają liczbę sekund.  
  
     Jeśli nie zostanie nigdy nie, czasomierza zatrzymuje i zmienia tekst `timeLabel` kontrolować, tak aby pokazywał **up czasu!** Okno komunikatu ogłasza kwizu znajduje się nad, czy odpowiedź zostanie ujawniony — w takim przypadku przez dodanie addend1 i addend2. **Włączone** właściwość `startButton` formantu ma ustawioną wartość `true` tak, aby uruchomić przyjmującego kwizu innego testu.  
  
     Można tylko dodać `if else` instrukcja, która jest jak sprawdzić programy do podejmowania decyzji. `if else` Instrukcji wygląda podobnie do następującej.  
  
    > [!NOTE]
    >  Poniższy przykład jest tylko do celów ilustracyjnych — nie należy dodawać go do projektu.  
  
    ```vb  
    If (something that your program will check) Then  
        ' One or more statements that will run  
        ' if what the program checked is true.   
    Else  
        ' One or more statements that will run  
        ' if what the program checked is false.  
    End If  
    ```  
  
    ```csharp  
    if (something that your program will check)  
    {  
        // One or more statements that will run  
        // if what the program checked is true.   
    }  
    else  
    {  
        // One or more statements that will run  
        // if what the program checked is false.  
    }  
    ```  
  
     Należy dokładnie przejrzeć dodanego w instrukcji `else` blok odpowiedź problem dodawania.  
  
     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]  
  
     Instrukcja `addend1 + addend2` dodaje dwie zmienne wartości ze sobą. Pierwsza część (`sum.Value`) używa **wartość** właściwości sumy `NumericUpDown` formantu, aby wyświetlić poprawne odpowiedzi. Umożliwia tę samą właściwość później sprawdzić odpowiedzi dla testu.  
  
     Możliwości kwizu można łatwiej wprowadź numery przy użyciu `NumericUpDown` kontroli, dlatego korzystanie z jednej odpowiedzi na problemów matematycznych. Wszystkie potencjalne odpowiedzi są liczby całkowite z przedziału od 0 do 100. Pozostawić wartości domyślne **Minimum**, **maksymalna**, i **DecimalPlaces** właściwości, należy zapewnić, że możliwości kwizu nie wprowadź liczby dziesiętne, liczby, ujemne lub numery, które są zbyt duże. (Jeśli chcesz zezwolić kwizu możliwości wprowadzania 3,141, ale nie 3.1415, można ustawić **DecimalPlaces** właściwości 3.)  
  
6.  Dodaj trzy wiersze na końcu `StartTheQuiz()` metody, aby kod wygląda następująco.  
  
     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]  
  
     Teraz, gdy Twoje kwizu rozpoczyna się, **timeLeft** zmienna jest ustawiona na 30 i **tekst** właściwość `timeLabel` kontrola została ustawiona na 30 sekund. Następnie przy użyciu `Start()` metody `Timer` odliczania rozpoczyna się formantu. (Kwizu nie sprawdza odpowiedź jeszcze — która teraz.)  
  
7.  Zapisz programu, uruchom ją, a następnie wybierz **Start** przycisk w formularzu.  
  
     Czasomierz rozpoczyna zliczanie w dół. Gdy czas skończy zakończenia testu i pojawi się odpowiedź. Na poniższej ilustracji przedstawiono kwizu w toku.  
  
     ![Matematyczne testu w toku](../ide/media/express_addcountdown.png "Express_AddCountdown")  
Matematyczne testu w toku  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 4: Dodawanie metody CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2: tworzenia problemu losowego dodawania](../ide/step-2-create-a-random-addition-problem.md).