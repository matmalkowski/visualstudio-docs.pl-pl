---
title: Krok 4. Dodawanie metody CheckTheAnswer() | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e9aa6c85776606c45590521113c322f9709cd561
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628893"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4. Dodawanie metody CheckTheAnswer()
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [krok 4: Dodawanie metody CheckTheAnswer()](https://docs.microsoft.com/visualstudio/ide/step-4-add-the-checktheanswer-parens-method).  
  
W czwartej części tego samouczka będziesz pisać metodę `CheckTheAnswer()`, która określa, czy odpowiedzi na problemy matematyczne są poprawne. Ten temat jest częścią serii samouczków na temat podstawowych pojęć kodowania. Aby uzyskać omówienie samouczka, zobacz [samouczek 2: Utwórz, Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
> [!NOTE]
>  Jeśli piszesz w Visual Basic użyjesz `Function` słowa kluczowego zamiast zwykłego `Sub` — słowo kluczowe, ponieważ ta metoda zwraca wartość. Jest naprawdę proste: sub nie zwraca wartości, natomiast funkcja.  
  
### <a name="to-verify-whether-the-answers-are-correct"></a>Aby sprawdzić, czy odpowiedzi są poprawne  
  
1.  Dodaj `CheckTheAnswer()` metody.  
  
     Gdy ta metoda jest wywoływana, dodaje wartości addend1 i addend2 i porównuje wynik z wartością w sumie `NumericUpDown` kontroli. Jeśli wartości są równe, metoda zwraca wartość `true`. W przeciwnym razie metoda zwraca wartość `false`. Kod powinien wyglądać następująco.  
  
     [!code-csharp[VbExpressTutorial3Step4#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial3Step4#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#8)]  
  
     Następnie sprawdzisz odpowiedź, aktualizując kod w metodzie dla programu obsługi zdarzeń Tick timera wywołać nową `CheckTheAnswer()` metody.  
  
2.  Dodaj następujący kod do `if else` instrukcji.  
  
     [!code-csharp[VbExpressTutorial3Step4#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial3Step4#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#10)]  
  
     Jeśli odpowiedź jest poprawna, `CheckTheAnswer()` zwraca `true`. Program obsługi zdarzeń zatrzymuje timer, pokazuje komunikat z gratulacjami i następnie sprawia, że **Start** przycisk ponownie. W przeciwnym razie quiz trwa nadal.  
  
3.  Zapisz swój program, uruchom go, uruchom quiz i Podaj poprawną odpowiedź na problem dodawania.  
  
    > [!NOTE]
    >  Po wprowadzeniu swojej odpowiedzi, musisz wybrać wartość domyślną przed rozpoczęciem wprowadzania odpowiedzi lub musisz usunąć zero ręcznie. W dalszej części tego samouczka skorygujesz to zachowanie.  
  
     Jeśli podasz poprawną odpowiedź, zostanie otwarte okno komunikatu **Start** przycisk staje się dostępny, a timer się zatrzyma.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 5: Dodawanie wprowadź procedury obsługi zdarzeń dla formantów NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: Dodawanie czasomierza odliczania](../ide/step-3-add-a-countdown-timer.md).



