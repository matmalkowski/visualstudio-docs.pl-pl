---
title: 'Krok 6: Dodawanie problemu odejmowania | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: "25"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 35fc0fd7be5d060019521467851708d0c6677935
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6. Dodawanie problemu odejmowania
W szóstego części tego samouczka możesz Dodawanie problemu odejmowania i Dowiedz się, jak wykonywać następujące zadania:  
  
-   Przechowywanie wartości odejmowanie.  
  
-   Generowanie liczb losowych problemu (i upewnij się, że odpowiedź jest od 0 do 100).  
  
-   Metoda, która sprawdza odpowiedzi, dzięki czemu sprawdza nowe problemu odejmowania zbyt aktualizacji.  
  
-   Program obsługi zdarzeń Tick Twojej czasomierza należy zaktualizować tak, aby program obsługi zdarzeń wypełnia prawidłowa odpowiedź, kiedy skończy się czas.  
  
### <a name="to-add-a-subtraction-problem"></a>Aby dodać problemu odejmowania  
  
1.  Dodaj dwie zmienne całkowitą problemu odejmowania do formularza, między zmienne całkowitą problem dodawania i czasomierza. Kod powinien wyglądać następująco.  
  
     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]  
  
     Nazwy nowe zmienne całkowitą —**minuend** i **subtrahend**— nie są programowania warunki. Są one tradycyjnych nazwy arytmetyczne, liczba, która jest odejmowany (subtrahend) i numer, z którego ma zostać subtrahend odejmować (minuend). Różnica polega na minuend minus subtrahend. Można użyć innych nazw, ponieważ program nie wymaga określonej nazwy zmiennych, kontrolek, składników lub metody. Należy wykonać, reguł, takich jak nie uruchamiają nazwy z cyfr, ale zazwyczaj można użyć nazwy, takie jak x1, x2 x3 i x4. Jednak nazwy uniemożliwiają czytelność kodu i problemy z niemal do śledzenia. Aby zachować nazwy zmiennych unikatowy i przydatne, użyjesz tradycyjnych nazwy dla mnożenia (mnożnik x multiplicand = produkt) i dzielenia (dzielnik ÷ dzielna = iloraz) dalszej części tego samouczka.  
  
     Następnie będzie zmodyfikować `StartTheQuiz()` metodę w celu zapewnienia losowych wartości dla problemu odejmowania.  
  
2.  Dodaj następujący kod po komentarz "Wypełnij problemu odejmowania".  
  
     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]  
  
     Aby zapobiec odpowiedzi ujemnych problemu odejmowania, ten kod używa `Next()` metody `Random` inaczej nieco klasę z jak problem dodawania. Po nadaniu `Next()` wartości metody dwa wybiera liczbę losową, która jest większa lub równa wartości pierwszego i mniejsza niż drugi. Poniższy kod wybierze liczbę losową z zakresu od 1 do 100 i zapisuje je w zmiennej minuend.  
  
     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]  
  
     Możesz wywołać `Next()` metody `Random` klasy, które użytkownik o nazwie "Generator losowy" we wcześniejszej części tego samouczka na wiele sposobów. Metody, które można wywołać w więcej niż jeden sposób są określane jako przeciążony i IntelliSense można użyć, aby zapoznać się z nimi. Spójrz ponownie na elemencie tooltip okna IntelliSense dla `Next()` metody.  
  
     ![Etykietka narzędzia okna IntelliSense](../ide/media/express_overloads.png "Express_Overloads")  
Etykietka narzędzia okna IntelliSense  
  
     Pokazuje tooltip **(+ 2 overload(s))**, co oznacza, że można wywołać `Next()` metody są dwa inne sposoby. Przeciążenia zawierają różne liczby i typy argumentów, aby mogły działać inaczej od siebie nawzajem. Na przykład metoda może potrwać jeden argument, jeden z jego przeciążenia może stać się liczba całkowita i ciąg. Możesz wybrać poprawne przeciążenia oparte na co chcesz wykonania. Po dodaniu kod, aby `StartTheQuiz()` metody, więcej informacji jest wyświetlana w oknie Intellisense jak wprowadzasz `randomizer.Next(`. Wybierz polecenie klawiszy Strzałka w górę i Strzałka w dół aby przechodzić kolejno przez przeciążeń, jak przedstawiono na poniższej ilustracji.  
  
     ![Przeciążenie dla następnego &#40; &#41; metody w technologii IntelliSense](../ide/media/express_nextoverload.png "Express_NextOverload")  
Metoda przeciążenia metody Next() w IntelliSense  
  
     W takim przypadku chcesz wybrać ostatniego przeciążenia, ponieważ można określić wartości minimalną i maksymalną.  
  
3.  Modyfikowanie `CheckTheAnswer()` metodę sprawdzania, czy odpowiedź odejmowania poprawne.  
  
     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]  
  
     W środowisku Visual C#, `&&` jest `logical and` operatora. W języku Visual Basic, jest równoważne operator `AndAlso`. Operatory te określają "Jeśli suma addend1 i addend2 jest równa wartości sum NumericUpDown, a jeśli minuend minus subtrahend jest równa wartości różnicy NumericUpDown." `CheckTheAnswer()` Metoda zwraca `true` tylko wtedy, gdy odpowiedzi do dodawania i odejmowania problemów są poprawne.  
  
4.  Tak, aby wypełnił w prawidłowa odpowiedź, kiedy skończy się czas Zastąp następujący kod ostatniej części programu obsługi zdarzeń Tick czasomierza.  
  
     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]  
  
5.  Zapisz i uruchomić kod.  
  
     Program obejmuje problemu odejmowania, jak przedstawiono na poniższej ilustracji.  
  
     ![Matematyczne testu z problemu odejmowania](../ide/media/express_addsubtract.png "Express_AddSubtract")  
Matematyczne testu z problemu odejmowania  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [kroku 7: problemów dodać mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5: Dodaj wprowadź obsługi zdarzeń dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).