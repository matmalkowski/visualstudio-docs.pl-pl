---
title: 'Samouczek 2: Tworzenie Quiz matematyczny | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4ec4c1bd1c01229ab0c8f32a78e2b7483a1efc06
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682445"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Samouczek 2: Utworzenie kwizu matematycznego z limitem czasu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [samouczek 2: Utwórz, Timed Math Quiz](https://docs.microsoft.com/visualstudio/ide/tutorial-2-create-a-timed-math-quiz).  
  
W tym samouczku tworzysz quiz, w którym osoba wypełniająca quiz musi rozwiązać cztery losowe problemy arytmetyczne w określonym czasie. Dowiesz się, jak:  
  
-   Wygeneruj liczby losowe przy użyciu `Random` klasy.  
  
-   Wyzwalanie zdarzenia w określonym czasie za pomocą **czasomierza** kontroli.  
  
-   Steruj przepływem wykonania programu za pomocą `if else` instrukcji.  
  
-   Wykonywać podstawowe operacje arytmetyczne w kodzie.  
  
 Gdy skończysz, quiz będzie wyglądał jak na poniższym obrazie, z wyjątkiem z różną liczbą.  
  
 ![Quiz matematyczny z czterema problemami](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
Quiz tworzony w ramach tego samouczka  
  
 Aby pobrać pełną wersję quizu, zobacz [przykładowy samouczek pełnej wersji quizu matematycznego](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
> [!NOTE]
>  W tym samouczku omówiono zarówno Visual C# i Visual Basic, więc Skoncentruj się na informacjach, które są specyficzne dla języka programowania, którego używasz.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Krok 1. Tworzenie projektu i dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Rozpocznij tworzenie projektu, zmieniając właściwości i dodając `Label` kontrolki.|  
|[Krok 2. Tworzenie losowego problemu dodawania](../ide/step-2-create-a-random-addition-problem.md)|Stwórz problem dodatku i użyj `Random` klasy w celu generowania liczb losowych.|  
|[Krok 3. Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md)|Dodawanie czasomierza odliczania, dzięki czemu może być synchronizowane quizu.|  
|[Krok 4. Dodawanie metody CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Dodaj metodę, aby sprawdzić, czy osoba wypełniająca quiz wprowadziła poprawną odpowiedź dla problemu.|  
|[Krok 5. Dodawanie procedur obsługi zdarzeń wprowadzania dla kontrolek NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Dodawanie obsługi zdarzeń, które ułatwiają zająć quiz.|  
|[Krok 6. Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md)|Dodawanie problemu odejmowania, który generuje liczby losowe, używa czasomierza i sprawdza, czy odpowiedzi są poprawne.|  
|[Krok 7. Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md)|Dodawanie problemów mnożenia i dzielenia, które generują liczby losowe, używają czasomierza i sprawdź, czy odpowiedzi są poprawne.|  
|[Krok 8. Dostosowywanie kwizu](../ide/step-8-customize-the-quiz.md)|Spróbuj innych funkcji, takich jak zmienianie kolorów i dodawanie wskazówki.|



