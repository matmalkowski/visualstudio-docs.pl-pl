---
title: 'Krok 8: Dodanie metody sprawdzania, czy gracz wygrał'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 34b4e8085c3ff3de8037827769331eac83325ff8
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748013"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8: Dodanie metody sprawdzania, czy gracz wygrał
Utworzyłeś zabawną grę, ale wymaga ona jeszcze jednej rzeczy. Gry powinna kończyć podczas odtwarzacz wins, więc konieczne jest dodanie `CheckForWinner()` metody, aby sprawdzić, czy gracz wygrał.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Aby dodać metodę w celu sprawdzenia, czy gracz wygrał

1.  Dodaj `CheckForWinner()` metody do dolnej części kodu, poniżej `timer1_Tick()` program obsługi zdarzeń, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

     Metoda korzysta z innego `foreach` pętli języka Visual C# lub `For Each` pętli w języku Visual Basic, aby przejść do każdej etykiety w <xref:System.Windows.Forms.TableLayoutPanel>. Używa operatora równości (`==` języka Visual C# i `=` w języku Visual Basic) do sprawdzenia każda etykieta kolor ikony, aby sprawdzić, czy jest on zgodny tła. Jeśli kolory są zgodne, ikona pozostaje niewidoczna, a gracz nie dopasował wszystkich pozostałych ikon. W takim przypadku program używa `return` instrukcji, aby pominąć metody. Jeśli pętla pobiera za pośrednictwem wszystkich etykiet bez wykonywania `return` instrukcji, która oznacza wszystkie ikony w formularzu były zgodne. Program zawiera element MessageBox do gratulacji player na określenie pierwszeństwa, a następnie wywołuje formularza `Close()` metodę, aby zakończyć grę.

2.  Następnie mają tę etykietę <xref:System.Windows.Forms.Control.Click> nowe wywołań obsługi zdarzeń `CheckForWinner()` metody. Pamiętaj, że program sprawdza zwycięzcę natychmiast po pokazaniu drugiej ikony, którą wybierze gracz. Poszukaj wiersza których wartość drugiego ikona wybrany kolor, a następnie wywołać `CheckForWinner()` metody prawo po tym, jak pokazano w poniższym kodzie.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3.  Zapisz i uruchom program. Zagraj w grę i dopasuj wszystkie ikony. Gdy win, program wyświetla gratulacyjny **MessageBox** (jak pokazano na poniższej ilustracji), a następnie zamyka okno.

     ![Dopasowywanie gry z MessageBox](../ide/media/express_tut4step8.png)
**dopasowania gry** z **MessageBox**

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 9: próbowanie innych funkcji](../ide/step-9-try-other-features.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [kroku 7: zachowanie widoczności par](../ide/step-7-keep-pairs-visible.md).
