---
title: 'Samouczek 2: Tworzenie quiz matematyczny'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b28afd645351577073eb7525cf4bed321afb09c0
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008398"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Samouczek 2: Tworzenie quiz matematyczny

W tym samouczku tworzysz quiz, w którym osoba wypełniająca quiz musi rozwiązać cztery losowe problemy arytmetyczne w określonym czasie. Dowiesz się, jak:

-   Wygeneruj liczby losowe przy użyciu <xref:System.Random> klasy.

-   Wyzwalanie zdarzenia w określonym czasie za pomocą <xref:System.Windows.Forms.Timer> kontroli.

-   Steruj przepływem wykonania programu za pomocą `if else` instrukcji.

-   Wykonywać podstawowe operacje arytmetyczne w kodzie.

Gdy skończysz, quiz będzie wyglądał jak na poniższym obrazie, z wyjątkiem z różną liczbą:

![Quiz matematyczny z czterema problemami](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Samouczek łącza

Aby pobrać pełną wersję quizu, zobacz [przykładowy samouczek quiz matematyczny pełną](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

> [!NOTE]
> W tym samouczku omówiono zarówno Visual C# i Visual Basic, więc Skoncentruj się na informacjach, które są specyficzne dla języka programowania, którego używasz.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1: Tworzenie projektu i dodawanie etykiet do formularza](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Rozpocznij tworzenie projektu, zmieniając właściwości i dodając `Label` kontrolki.|
|[Krok 2. Tworzenie losowego problemu dodawania](../ide/step-2-create-a-random-addition-problem.md)|Stwórz problem dodatku i użyj `Random` klasy w celu generowania liczb losowych.|
|[Krok 3. Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md)|Dodawanie czasomierza odliczania, dzięki czemu może być synchronizowane quizu.|
|[Krok 4. Dodawanie metody CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Dodaj metodę, aby sprawdzić, czy osoba wypełniająca quiz wprowadziła poprawną odpowiedź dla problemu.|
|[Krok 5: Dodawanie obsługi zdarzeń Enter dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Dodawanie obsługi zdarzeń, które ułatwiają zająć quiz.|
|[Krok 6. Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md)|Dodawanie problemu odejmowania, który generuje liczby losowe, używa czasomierza i sprawdza, czy odpowiedzi są poprawne.|
|[Krok 7. Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md)|Dodawanie problemów mnożenia i dzielenia, które generują liczby losowe, używają czasomierza i sprawdź, czy odpowiedzi są poprawne.|
|[Krok 8: Dostosowywanie kwizu](../ide/step-8-customize-the-quiz.md)|Spróbuj innych funkcji, takich jak zmienianie kolorów i dodawanie wskazówki.|
