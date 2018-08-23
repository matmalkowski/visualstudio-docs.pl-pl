---
title: 'Krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5484d98801eacfbf56984d923594d29ad7196fad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678130"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8. Dodanie metody sprawdzania, czy gracz wygrał
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał](https://docs.microsoft.com/visualstudio/ide/step-8-add-a-method-to-verify-whether-the-player-won).  
  
Utworzyłeś zabawną grę, ale wymaga ona jeszcze jednej rzeczy. Gra powinna się kończyć kiedy gracz wygrywa, więc trzeba dodać `CheckForWinner()` metodę, aby sprawdzić, czy gracz wygrał.  
  
### <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Aby dodać metodę w celu sprawdzenia, czy gracz wygrał  
  
1.  Dodaj `CheckForWinner()` metodę do dolnej części kodu, poniżej `timer1_Tick()` program obsługi zdarzeń, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[VbExpressTutorial4Step8#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial4Step8#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#10)]  
  
     Metoda używa innej `foreach` pętli w języku Visual C# lub `For Each` pętli w języku Visual Basic, aby przejść przez każdą etykietę w TableLayoutPanel. Używa operatora równości (`==` w języku Visual C# i `=` w języku Visual Basic) do sprawdzania kolor ikony każdej etykiety, aby sprawdzić, czy pasuje do tła. Jeśli kolory są zgodne, ikona pozostaje niewidoczna, a gracz nie dopasował wszystkich pozostałych ikon. W takim przypadku program używa `return` instrukcję, aby pominąć resztę metody. Jeśli pętla przechodzi przez wszystkie etykiety bez wykonywania `return` instrukcji, oznacza to, że wszystkie ikony w formularzu zostały dopasowane. Program pokazuje komunikat MessageBox, aby pogratulować graczowi wygranej, a następnie wywołuje formularza `Close()` metodę, aby zakończyć grę.  
  
2.  Następnie, Spowoduj Click etykiety program obsługi zdarzeń wywoływał nową `CheckForWinner()` metody. Pamiętaj, że program sprawdza zwycięzcę natychmiast po pokazaniu drugiej ikony, którą wybierze gracz. Wyszukaj wiersz, gdzie ustawiasz kolor drugiej wybranej ikony, a następnie wywołaj `CheckForWinner()` metoda zaraz po tym, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[VbExpressTutorial4Step8#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial4Step8#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#11)]  
  
3.  Zapisz i uruchom program. Zagraj w grę i dopasuj wszystkie ikony. Kiedy wygrasz, program wyświetli komunikat MessageBox z gratulacjami (jak pokazano na rysunku poniżej), a następnie zamknie okno.  
  
     ![Gra w dopasowywanie z MessageBox](../ide/media/express-tut4step8.png "Express_Tut4Step8")  
Gra w dopasowywanie z MessageBox  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 9: Wypróbuj inne funkcje](../ide/step-9-try-other-features.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [kroku 7: Keep Pairs Visible](../ide/step-7-keep-pairs-visible.md).



