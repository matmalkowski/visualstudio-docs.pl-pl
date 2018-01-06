---
title: 'Samouczek 2: Utworzenie kwizu matematycznego | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
caps.latest.revision: "17"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 049bae0ee8665a17836ba0add5c442680e0a609d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Samouczek 2: Utworzenie kwizu matematycznego z limitem czasu
W tym samouczku zostanie utworzony testu, w którym przyjmującego kwizu musi odpowiedzieć cztery losowe problemów arytmetyczne w określonym czasie. Dowiesz się, jak:  
  
-   Generowanie liczb losowych przy użyciu `Random` klasy.  
  
-   Wyzwalanie zdarzenia o określonej godzinie przy użyciu **czasomierza** formantu.  
  
-   Sterowanie przepływem programu przy użyciu `if else` instrukcje.  
  
-   Wykonywanie podstawowych operacji arytmetycznych w kodzie.  
  
 Po zakończeniu testu z będzie wyglądać poniższej ilustracji, z wyjątkiem z różną.  
  
 ![Matematyczne kwizu czterech problemów](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
Kwizu utworzonego w ramach tego samouczka  
  
 Aby pobrać wersję ukończone kwizu, zobacz [przykładowy samouczek pełną kwizu matematyczne](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
> [!NOTE]
>  Ten samouczek obejmuje zarówno Visual C# i Visual Basic, więc skupić się na informacje, które są specyficzne dla języka programowania, którego używasz.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Krok 1. Tworzenie projektu i dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Rozpocznij od tworzenia projektu, zmiana właściwości i dodawanie `Label` kontrolki.|  
|[Krok 2. Tworzenie losowego problemu dodawania](../ide/step-2-create-a-random-addition-problem.md)|Utwórz problem dodawania i użyj `Random` klasy dla generatora liczb losowych.|  
|[Krok 3. Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md)|Dodawanie czasomierza odliczania, dzięki czemu kwizu może upłynął.|  
|[Krok 4. Dodawanie metody CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Dodaj metodę sprawdzania, czy przyjmującego kwizu wprowadzono poprawną odpowiedź problem.|  
|[Krok 5. Dodawanie procedur obsługi zdarzeń wprowadzania dla kontrolek NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Dodawanie obsługi zdarzeń, ułatwiające zająć użytkownika testu.|  
|[Krok 6. Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md)|Dodawanie problemu odejmowania, który generuje liczb losowych, używa czasomierza i sprawdza, czy są poprawne odpowiedzi.|  
|[Krok 7. Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md)|Dodawanie problemów mnożenia i dzielenia, które generatora liczb losowych, użyj czasomierza i sprawdź, czy poprawne odpowiedzi.|  
|[Krok 8. Dostosowywanie kwizu](../ide/step-8-customize-the-quiz.md)|Spróbuj inne funkcje, takie jak zmiana kolorów i dodawanie wskazówkę.|