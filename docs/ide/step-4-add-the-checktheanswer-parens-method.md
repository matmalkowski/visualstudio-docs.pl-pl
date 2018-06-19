---
title: 'Krok 4: Dodawanie metody CheckTheAnswer()'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ff11913b854ede1c20c0670b89c4ea2f50fd326e
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32064522"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4: Dodawanie metody CheckTheAnswer()
W czwartym części tego samouczka przedstawiono tworzenie metody, `CheckTheAnswer()`, który określa, czy odpowiedzi na problemy matematyczne są poprawne. Ten temat jest częścią samouczek serii o podstawowych pojęciach kodowania. Omówienie samouczka, zobacz [samouczek 2: tworzenie kwizu matematycznego](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
> [!NOTE]
>  Jeśli w poniższym w języku Visual Basic, użyjesz `Function` słowa kluczowego zamiast standardowego `Sub` — słowo kluczowe, ponieważ ta metoda zwraca wartość. Jest naprawdę proste: metodę sub nie zwraca wartości, ale nie funkcja.  

## <a name="to-verify-whether-the-answers-are-correct"></a>Aby sprawdzić, czy odpowiedzi są poprawne  

1.  Dodaj `CheckTheAnswer()` metody.  
  
     Gdy ta metoda jest wywoływana, dodaje wartości addend1 i addend2 i porównuje ją z wartością sumy <xref:System.Windows.Forms.NumericUpDown> formantu. Jeśli wartości są równe, metoda zwraca wartość `true`. W przeciwnym razie metoda zwraca wartość `false`. Kod powinien wyglądać podobnie jak poniżej.  
  
     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]  
  
     Następnie będzie Sprawdź odpowiedź, aktualizując kod w metodzie dla czasomierza <xref:System.Windows.Forms.Timer.Tick> obsługi zdarzeń do wywołania nowe `CheckTheAnswer()` metody.  
  
2.  Dodaj następujący kod do `if else` instrukcji.  

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]  

     Jeśli odpowiedź jest poprawna, `CheckTheAnswer()` zwraca `true`. Program obsługi zdarzeń zatrzymuje czasomierza, zawiera komunikat gratulacyjny i powoduje wyświetlenie **Start** przycisk ponownie dostępna. W przeciwnym razie kwizu będzie kontynuowana.  

3.  Zapisz programu, uruchom go uruchomić testu i Podaj poprawną odpowiedź na problem dodawania.  

    > [!NOTE]
    >  Po wprowadzeniu odpowiedzi, musisz wybrać wartość domyślną przed rozpoczęciem wprowadzania odpowiedzi lub zero trzeba usunąć ręcznie. W dalszej części tego samouczka będziesz rozwiązać ten problem.  

     Podając poprawną odpowiedź, zostanie otwarte okno komunikatu, **Start** przycisk jest dostępny, i zatrzymuje czasomierza.  

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 5: Dodaj wprowadź obsługi zdarzeń dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md).
