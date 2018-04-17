---
title: 'Krok 8: Dodanie metody sprawdzania, czy gracz wygrał | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d14f386bfd22893aa18a5c5982a03314c2a31984
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8. Dodanie metody sprawdzania, czy gracz wygrał
Utworzyłeś zabawną grę, ale wymaga ona jeszcze jednej rzeczy. Gry powinna kończyć podczas odtwarzacz wins, więc konieczne jest dodanie `CheckForWinner()` metody, aby sprawdzić, czy gracz wygrał.  
  
### <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Aby dodać metodę w celu sprawdzenia, czy gracz wygrał  
  
1.  Dodaj `CheckForWinner()` metody do dolnej części kodu, poniżej `timer1_Tick()` program obsługi zdarzeń, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]  
  
     Metoda korzysta z innego `foreach` pętli języka Visual C# lub `For Each` pętli w języku Visual Basic, aby przejść do każdej etykiety w TableLayoutPanel. Używa operatora równości (`==` języka Visual C# i `=` w języku Visual Basic) do sprawdzenia każda etykieta kolor ikony, aby sprawdzić, czy jest on zgodny tła. Jeśli kolory są zgodne, ikona pozostaje niewidoczna, a gracz nie dopasował wszystkich pozostałych ikon. W takim przypadku program używa `return` instrukcji, aby pominąć metody. Jeśli pętla pobiera za pośrednictwem wszystkich etykiet bez wykonywania `return` instrukcji, która oznacza wszystkie ikony w formularzu były zgodne. Program zawiera element MessageBox do gratulacji player na określenie pierwszeństwa, a następnie wywołuje formularza `Close()` metodę, aby zakończyć grę.  
  
2.  Następnie mają kliknij etykietę nowe wywołań obsługi zdarzeń `CheckForWinner()` metody. Pamiętaj, że program sprawdza zwycięzcę natychmiast po pokazaniu drugiej ikony, którą wybierze gracz. Poszukaj wiersza których wartość drugiego ikona wybrany kolor, a następnie wywołać `CheckForWinner()` metody prawo po tym, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]  
  
3.  Zapisz i uruchom program. Zagraj w grę i dopasuj wszystkie ikony. Kiedy wygrasz, program wyświetli komunikat MessageBox z gratulacjami (jak pokazano na rysunku poniżej), a następnie zamknie okno.  
  
     ![Dopasowywanie gry z MessageBox](../ide/media/express_tut4step8.png "Express_Tut4Step8")  
Gra w dopasowywanie z MessageBox  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 9: spróbuj innych funkcji](../ide/step-9-try-other-features.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [kroku 7: Zachowaj widoczne pary](../ide/step-7-keep-pairs-visible.md).