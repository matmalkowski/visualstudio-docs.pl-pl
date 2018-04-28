---
title: 'Krok 7: Zachowanie widoczności par'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 956a5b1df35708f5bbe04539a9871272d168ff58
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7: Zachowanie widoczności par
Gra działa dobrze, dopóki gracz wybiera tylko pary ikon, które nie są zgodne. Rozważmy jednak, co się powinno zdarzyć, gdy gracz wybierze pasującą parę. Zamiast wprowadzania ikony znikają przez włączenie czasomierza (przy użyciu <xref:System.Windows.Forms.Timer.Start> metody), gry powinien zresetowanie tak, aby go jest już rejestrowanie informacji o wszystkich etykiet za pomocą `firstClicked` i `secondClicked` odwoływać się do zmiennych, bez potrzeby resetowania kolory dwie etykiety, które zostały wybrane.  

## <a name="to-keep-pairs-visible"></a>Aby zachować widoczność par  

1.  Dodaj następujące `if` instrukcji `label_Click()` metoda obsługi zdarzeń, zbliża się koniec kodu powyżej instrukcji, gdzie uruchomić czasomierza. Przyjrzyj się kodowi podczas dodawania go do programu. Zastanów się, jak działa kod.  

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]  
  
     W pierwszym wierszu `if` instrukcji dodaną sprawdza, czy ikona w etykiecie pierwszy wybierze odtwarzacz jest taka sama jak ikona w drugim etykiety. W przypadku ikony są identyczne, program wykonuje trzy instrukcji między nawiasy klamrowe w języku C# lub trzy instrukcje `if` instrukcji w języku Visual Basic. Pierwsze dwie instrukcje resetowania `firstClicked` i `secondClicked` odwoływać się do zmiennych tak, aby ich nie będzie przechowywać informacje o dowolne etykiety. (Te dwa oświadczenia czasomierza może rozpoznać <xref:System.Windows.Forms.Timer.Tick> obsługi zdarzeń.) Trzecia instrukcja jest `return` instrukcja, która informuje program Pomiń pozostałą część instrukcje w metodzie bez ich wykonywania.  
  
     Jeśli Programowanie w Visual C#, można zauważyć, że niektóre kod używa pojedynczego znaku równości (`=`), podczas gdy inne instrukcje dwóch znaku równości (`==`). Należy wziąć pod uwagę dlaczego `=` jest używana w niektórych miejscach, ale `==` jest używana w innych miejscach.  

     To jest dobry przykład, który pokazuje różnicę. Przyjrzyjmy się staranne kod w nawiasach w `if` instrukcji.  

    ```vb  
    firstClicked.Text = secondClicked.Text  
    ```  

    ```csharp  
    firstClicked.Text == secondClicked.Text  
    ```  

     Pierwszą instrukcją w bloku kodu po następnie należy dokładnie przejrzeć `if` instrukcji.  

    ```vb  
    firstClicked = Nothing  
    ```  

    ```csharp  
    firstClicked = null;  
    ```  

     Pierwsza z tych dwóch instrukcji sprawdza, czy dwie ikony są takie same. Ponieważ dwie wartości są porównywane, program Visual C# używa `==` operator równości. Druga instrukcja faktycznie zmienia wartość (o nazwie *przypisania*), to ustawienie `firstClicked` odwołanie do zmiennej równa `null` je zresetować. Dlatego używa `=` operator przypisania zamiast tego. Visual C# używa `=` można ustawić wartości, i `==` do porównania. Używa języka Visual Basic `=` dla porównanie i przypisanie zmiennej.  
  
2.  Zapisz i uruchom program, a następnie zacznij wybierać ikony na formularzu. Jeśli wybierzesz parę, która nie pasuje, wyzwala się zdarzenie czasomierza Takt i obie ikony znikają. Jeśli wybierzesz parę pasującego nowe `if` wykonywania instrukcji i instrukcji return powoduje, że metoda pomijania kod, który uruchamia czasomierz, więc ikony pozostanie widoczny, jak pokazano na poniższej ilustracji.  
  
     ![Gry utworzone w tym samouczku](../ide/media/express_finishedgame.png "Express_FinishedGame")  
**Dopasowywanie gry** z parami widoczna ikona  
  
## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Dodawanie czasomierza](../ide/step-6-add-a-timer.md).
