---
title: 'Krok 7: Dodawanie problemów mnożenia i dzielenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 467bd4e021cd60d42043fb2b6e579b816930b6f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7. Dodawanie problemów mnożenia i dzielenia
W siódmego części tego samouczka będziesz Dodawanie problemów mnożenia i dzielenia, ale najpierw zastanowić, jak wprowadzić zmiany. Należy wziąć pod uwagę kroku początkowego, które obejmuje przechowywanie wartości.  
  
### <a name="to-add-multiplication-and-division-problems"></a>Aby dodać problemów mnożenia i dzielenia  
  
1.  Dodaj więcej zmiennych całkowitą w formularzu.  
  
     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]  
  
2.  Tak samo jak przed, zmodyfikuj `StartTheQuiz()` metodę, aby wypełnić liczb losowych problemów mnożenia i dzielenia.  
  
     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]  
  
3.  Modyfikowanie `CheckTheAnswer()` metodę, tak że sprawdza również problemów mnożenia i dzielenia.  
  
     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]  
  
     Nie można łatwo wprowadzić znak mnożenia (x) i znak dzielenia (÷) przy użyciu klawiatury, więc Visual C# i Visual Basic Zaakceptuj znak gwiazdki (*) mnożenia i znaku ukośnika (/) dla dzielenia.  
  
4.  Zmień ostatniej części programu obsługi zdarzeń Tick czasomierza tak, aby wypełnił w prawidłowa odpowiedź, kiedy skończy się czas.  
  
     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]  
  
5.  Zapisz i uruchom program.  
  
     Możliwości kwizu musi odpowiedzieć w czterech problemów do ukończenia testu, jak przedstawiono na poniższej ilustracji.  
  
     ![Matematyczne kwizu czterech problemów](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
Matematyczne kwizu czterech problemów  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 8: dostosowywanie kwizu](../ide/step-8-customize-the-quiz.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md).