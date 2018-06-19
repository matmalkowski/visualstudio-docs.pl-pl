---
title: 'Krok 8: Dostosowywanie kwizu'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c2f096415ccfbadfe66f18a373642cf6a5de86b
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32065250"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8: Dostosowywanie kwizu
W ostatniej części samouczka będziesz Poznaj sposoby Dostosowywanie kwizu i rozszerzają co już znasz. Na przykład zastanowić się, jak program tworzy losowe dzielenia problemów dla których odpowiedź nigdy nie jest ułamek. Aby dowiedzieć się więcej, należy włączyć `timeLabel` kontrolować różne kolory i przypisz przyjmującego kwizu wskazówkę.  

## <a name="to-customize-the-quiz"></a>Aby dostosować kwizu  

-   Kiedy tylko pięciu sekund pozostają w kwizu, Włącz **timeLabel** kontrolować przez ustawienie red jego **BackColor** właściwości (`timeLabel.BackColor = Color.Red;`). Resetuj kolor po umieszczeniu kwizu.  
  
-   Nadaj przyjmującego kwizu wskazówkę przez odtwarzanie dźwięku w momencie prawidłowa odpowiedź do <xref:System.Windows.Forms.NumericUpDown> formantu. (Należy napisać program obsługi zdarzeń dla każdego formantu <xref:System.Windows.Forms.NumericUpDown.ValueChanged> zdarzenie, które są generowane przy każdej zmianie kwizu przyjmującego wartość formantu.)  
  
## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby pobrać wersję ukończone kwizu, zobacz [przykładowy samouczek kwizu pełną matematyczne](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Aby przejść do następnego samouczek, zobacz [3 samouczek: tworzenie pasujący gier](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7: Dodawanie problemów mnożenia i dzielenia](../ide/step-7-add-multiplication-and-division-problems.md).
