---
title: Krok 7. Dodawanie problemów mnożenia i dzielenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 83c85dfdca66e9df3634f84795042b331bf3f760
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682855"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7. Dodawanie problemów mnożenia i dzielenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [kroku 7: problemów dodawać mnożenia i dzielenia](https://docs.microsoft.com/visualstudio/ide/step-7-add-multiplication-and-division-problems).  
  
W siódmej części tego samouczka będziesz dodawać problemy mnożenia i dzielenia, ale najpierw zastanów się, jak dokonać tej zmiany. Należy wziąć pod uwagę etap początkowy, który obejmuje zapisanie wartości.  
  
### <a name="to-add-multiplication-and-division-problems"></a>Aby dodać problemy mnożenia i dzielenia  
  
1.  Dodaj cztery więcej zmiennych całkowitych do formularza.  
  
     [!code-csharp[VbExpressTutorial3Step7#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial3Step7#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#15)]  
  
2.  Jak poprzednio, zmodyfikuj `StartTheQuiz()` metodę, aby wprowadzić liczby losowe dla problemów mnożenia i dzielenia.  
  
     [!code-csharp[VbExpressTutorial3Step7#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial3Step7#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#16)]  
  
3.  Modyfikowanie `CheckTheAnswer()` metodę, tak aby sprawdzała również problemy mnożenia i dzielenia.  
  
     [!code-csharp[VbExpressTutorial3Step7#17](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#17)]
     [!code-vb[VbExpressTutorial3Step7#17](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#17)]  
  
     Nie można łatwo wprowadzić znak mnożenia (x) i znak dzielenia (÷) za pomocą klawiatury, więc Visual C# i Visual Basic Zaakceptuj znak gwiazdki (*) dla mnożenia i znak kreski ukośnej (/) dla działu.  
  
4.  Zmień ostatnią część programu obsługi zdarzeń Tick timera, tak aby wypełnił poprawną odpowiedź, gdy skończy się czas.  
  
     [!code-csharp[VbExpressTutorial3Step7#23](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#23)]
     [!code-vb[VbExpressTutorial3Step7#23](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#23)]  
  
5.  Zapisz i uruchom program.  
  
     Quizu muszą rozwiązać cztery problemy, aby zakończyć quiz, jak pokazano na następującym rysunku.  
  
     ![Quiz matematyczny z czterema problemami](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
Quiz matematyczny z czterema problemami  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 8: dostosowywanie kwizu](../ide/step-8-customize-the-quiz.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md).



