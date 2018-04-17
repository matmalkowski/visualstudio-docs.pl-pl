---
title: 'Krok 2: Utworzenie problemu losowego dodawania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7212f5df1ef5be0033d17a4f7a57dba455e7022d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2. Utworzenie problemu losowego dodawania
W drugiej części tego samouczka należy kwizu trudne, dodając matematyczne problemów, które są oparte na liczb losowych. Możesz również utworzyć metodę o nazwie `StartTheQuiz()` i który wypełnia problemów i uruchamia czasomierza odliczania. W dalszej części tego samouczka możesz dodać odejmowania, mnożenia i dzielenia problemów.

> [!NOTE]
>  Ten temat jest częścią samouczek serii o podstawowych pojęciach kodowania. Omówienie samouczka, zobacz [samouczek 2: tworzenie upłynął matematyczne quizu](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-create-a-random-addition-problem"></a>Aby utworzyć problemu losowego dodawania

1.  W Projektancie formularza wybierania formy (Form1).

2.  Na pasku menu wybierz **widoku**, **kod**.

     Pliku Form1.CS lub Form1.vb pojawia się, w zależności od języka programowania, którego używasz, dzięki czemu można wyświetlić kodu formularza.

3.  Utwórz `Random` obiektów przez dodanie `new` instrukcji w górnej części kodu, podobnie do poniższego.

     [!code-csharp[VbExpressTutorial3Step2#1](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_1.cs)]
     [!code-vb[VbExpressTutorial3Step2#1](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_1.vb)]

     Dodano `Random` obiektu do formularza i o nazwie obiektu **Generator losowy**.

     `Random` nosi nazwę obiektu. Wiesz już prawdopodobnie ten wyraz przed, i dowiedzieć się więcej na temat to programowania w następnym samouczku. Teraz należy jednak pamiętać, że można używać `new` instrukcje tworzenia przycisków, etykiety, panele, OpenFileDialogs, ColorDialogs, SoundPlayers, Randoms, a nawet formularzy i te elementy są określane jako obiekty. Po uruchomieniu programu, formularz jest uruchomiona, i tworzy kod związany z nim `Random` obiektu i nadaje **Generator losowy**.

     Wkrótce będzie kompilacji metodę sprawdzania odpowiedzi, więc użytkownika testu musi używać zmiennych do przechowywania liczb losowych, generowany dla każdego problemu. Zobacz [zmienne](/dotnet/visual-basic/programming-guide/language-features/variables/index) lub [typów](/dotnet/csharp/programming-guide/types/index). Do prawidłowego używania zmiennych, należy zadeklarować, co oznacza, że ich nazwy i typy danych.

4.  Dodaj dwie zmienne całkowitą do formularza, a ich nazwy **addend1** i **addend2**.

    > [!NOTE]
    >  Zmienna typu Liczba całkowita jest określany jako int w języku C# lub liczbą całkowitą w języku Visual Basic. Tego typu zmienną liczbą dodatnią lub ujemną od -2147483648 do 2147483647 zapisuje i można przechowywać tylko liczby całkowite, nie miejsc dziesiętnych.

     Podobne składnia jest używana do dodawania zmienna typu Liczba całkowita, jak dodać `Random` obiektu, jak przedstawiono na poniższym kodem.

     [!code-csharp[VbExpressTutorial3Step2#2](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_2.cs)]
     [!code-vb[VbExpressTutorial3Step2#2](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_2.vb)]

5.  Dodaj metodę o nazwie `StartTheQuiz()` i który korzysta z `Random` obiektu `Next()` metody do wyświetlenia w etykietach liczb losowych. `StartTheQuiz()` zostanie ostatecznie Wypełnij wszystkie problemy i następnie uruchomić czasomierza, a więc Dodaj komentarz. Funkcja powinna wyglądać następująco.

     [!code-csharp[VbExpressTutorial3Step2#3](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_3.cs)]
     [!code-vb[VbExpressTutorial3Step2#3](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_3.vb)]

     Zwróć uwagę, że po wprowadzeniu kropkę (.) po **Generator losowy** w kodzie, otwiera okno IntelliSense i pokazuje wszystkie `Random` metody obiektu, które można wywołać. Na przykład IntelliSense wyświetla `Next()` metody, w następujący sposób.

     ![Next — metoda](../ide/media/express_randomwhite.png "Express_RandomWhite") Next — metoda

     Po wprowadzeniu kropkę po obiekt IntelliSense zawiera listę elementów członkowskich obiektu, takie jak właściwości, metod i zdarzeń.

    > [!NOTE]
    >  Jeśli używasz `Next()` metody z `Random` obiektu, na przykład podczas wywoływania `randomizer.Next(50)`, Pobierz liczbę losową, która jest mniejsza niż 50 (od 0 do 49). W tym przykładzie jest nazywany `randomizer.Next(51)`. 51 i 50 nie jest używany, aby dwie liczb losowych będzie sumują się do odpowiedzi, który jest z zakresu od 0 do 100. W przypadku przekazania 50 do `Next()` metody wybiera numer od 0 do 49, więc najwyższy możliwy odpowiedzi jest 98 nie 100. Po uruchomieniu dwóch pierwszych instrukcje w metodzie, każdej ze zmiennych dwóch całkowitą `addend1` i `addend2`, przytrzymaj liczbę losową z zakresu od 0 do 50. Ten zrzut ekranu przedstawia kod Visual C#, ale IntelliSense działa tak samo w języku Visual Basic.

     Przyjrzyjmy się bliżej te instrukcje.

     [!code-csharp[VbExpressTutorial3Step2#18](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_4.cs)]
     [!code-vb[VbExpressTutorial3Step2#18](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_4.vb)]

     Zestaw instrukcji **tekst** właściwości **plusLeftLabel** i **plusRightLabel** , dzięki czemu są one wyświetlane dwie liczb losowych. Należy użyć całkowitą `ToString()` metoda konwertuje na tekst. (W programowaniu ciągu oznacza, że tekst. Formantów etykiet wyświetlanie tylko tekst, a nie liczby.

6.  W oknie Projekt albo kliknij dwukrotnie **Start** przycisku, lub wybierz go, a następnie wybierz klawisz Enter.

     Gdy przyjmującego kwizu wybierze ten przycisk, kwizu powinna zaczynać się i właśnie dodano obsługi zdarzeń kliknięcia do implementacji tego zachowania.

7.  Dodaj następujące dwie instrukcje.

     [!code-csharp[VbExpressTutorial3Step2#4](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_5.cs)]
     [!code-vb[VbExpressTutorial3Step2#4](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_5.vb)]

     Pierwsza instrukcja wywołuje nowe `StartTheQuiz()` metody. Druga instrukcja ustawia **włączone** właściwość **startButton** formant **False** tak, aby przyjmującego testu nie można wybrać przycisk podczas testu.

8.  Zapisz kod, uruchom ją, a następnie wybierz **Start** przycisku.

     Problemu losowego dodawania pojawia się, jak przedstawiono na poniższej ilustracji.

     ![Problemu losowego dodawania](../ide/media/express_additionproblem.png "Express_AdditionProblem") problem dodawania losowe

     W następnym kroku samouczka zostanie dodana suma.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 3: Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1: Tworzenie projektu i dodawanie etykiet do formularza Your](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).