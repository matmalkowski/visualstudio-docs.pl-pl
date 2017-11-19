---
title: 'Krok 8: Dostosowywanie kwizu | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: "12"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 7a4481f9a13d6807abc42b938670a05bd0dda50b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="step-8-customize-the-quiz"></a>Krok 8: Dostosowywanie kwizu
W ostatniej części samouczka będziesz Poznaj sposoby Dostosowywanie kwizu i rozszerzają co już znasz. Na przykład zastanowić się, jak program tworzy losowe dzielenia problemów dla których odpowiedź nigdy nie jest ułamek. Aby dowiedzieć się więcej, należy włączyć `timeLabel` kontrolować różne kolory i przypisz przyjmującego kwizu wskazówkę.  
  
### <a name="to-customize-the-quiz"></a>Aby dostosować kwizu  
  
-   Kiedy tylko pięciu sekund pozostają w kwizu, Włącz **timeLabel** kontrolować przez ustawienie red jego **BackColor** właściwości (`timeLabel.BackColor = Color.Red;`). Resetuj kolor po umieszczeniu kwizu.  
  
-   Nadaj przyjmującego kwizu wskazówkę przez odtwarzanie dźwięku po wprowadzeniu do formantu NumericUpDown prawidłowa odpowiedź. (Należy napisać program obsługi zdarzeń dla każdego formantu `ValueChanged()` zdarzenie, które są generowane przy każdej zmianie kwizu przyjmującego wartość formantu.)  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby pobrać wersję ukończone kwizu, zobacz [przykładowy samouczek pełną kwizu matematyczne](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Aby przejść do następnego samouczek, zobacz [3 samouczek: tworzenie gier dopasowania](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [kroku 7: problemów dodać mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).