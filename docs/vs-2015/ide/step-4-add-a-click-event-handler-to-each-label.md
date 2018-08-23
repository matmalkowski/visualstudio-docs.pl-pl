---
title: 'Krok 4: Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 92b6e04ef903c1fa6cf7e94b04874e2d6048acd1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680507"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [krok 4: Dodawanie obsługi zdarzeń kliknij do każdej etykiety](https://docs.microsoft.com/visualstudio/ide/step-4-add-a-click-event-handler-to-each-label).  
  
Gra w dopasowywanie działa w następujący sposób:  
  
1.  Gdy gracz wybiera jeden z kwadratów z ukrytą ikoną, program pokazuje graczowi ikonę, zmieniając jej kolor na czarny.  
  
2.  Następnie gracz wybiera inną ukrytą ikonę.  
  
3.  Jeśli ikony pasują, pozostają widoczne. Jeśli tak nie jest, obie ikony są ukrywane ponownie.  
  
 Aby program umożliwiał pracę w ten sposób, dodaj program obsługi zdarzeń Kliknięcie, który zmienia kolor wybranej etykiety.  
  
### <a name="to-add-a-click-event-handler-to-each-label"></a>Aby dodać program obsługi zdarzeń Kliknięcie do każdej etykiety  
  
1.  Otwórz formularz w programie Windows Forms Designer. W oknie Eksploratora rozwiązań wybierz Form1.cs lub Form1.vb. Na pasku menu wybierz **widoku**, **projektanta**.  
  
2.  Wybierz pierwszy formant etykiety, aby go zaznaczyć. Następnie trzymaj wciśnięty klawisz CTRL, zaznaczając pozostałe etykiety. Pamiętaj, że każda etykieta jest zaznaczona.  
  
3.  Wybierz **zdarzenia** przycisk na pasku narzędzi w **właściwości** okna, aby wyświetlić **zdarzenia** strony w **właściwości** okna. Przewiń w dół do **kliknij** zdarzeń, a następnie wprowadź **label_Click** w polu, jak pokazano na poniższej ilustracji.  
  
     ![Okno właściwości pokazujące kliknij zdarzenie](../ide/media/express-labelclick.png "Express_labelClick")  
Okno Właściwości pokazujące zdarzenie Kliknij  
  
4.  Wybierz klawisz ENTER. IDE dodaje program obsługi zdarzeń na kliknięcie o nazwie `label_Click()` z kodem i przyczepia go do każdej etykiety w formularzu.  
  
5.  Wypełnij resztę kodu w następujący sposób:  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#4)]  
  
    > [!NOTE]
    >  Jeśli skopiujesz i wkleisz `label_Click()` blok kodu, a nie wprowadzasz kod ręcznie, upewnij się zastąpić istniejącą `label_Click()` kodu. W przeciwnym razie otrzymasz zduplikowany blok kodu.  
  
    > [!NOTE]
    >  Może rozpoznać `object sender` w górnej części programu obsługi zdarzeń jako ten sam używany w [samouczek 2: Utwórz, Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md) samouczka. Ponieważ podłączyłeś inne zdarzenie Kliknij formantu etykiety do metody obsługi pojedynczego zdarzenia, ta sama metoda jest wywoływana, niezależnie od tego, którą etykietę wybierze użytkownik. Metoda obsługi zdarzeń musi wiedzieć, którą etykietę wybrano, więc używa nazwy **nadawcy** Aby zidentyfikować formant etykiety. Pierwszy wiersz metody mówi programowi, że nie jest obiekt rodzajowy, ale konkretnie formant etykiety i że używa on nazwy **clickedLabel** dostęp do właściwości i metod etykiety.  
  
     Metoda ta najpierw sprawdza, czy **clickedLabel** został pomyślnie przekonwertowany (rzutowany) z obiektu na formant etykiety. Jeśli nie, ma wartość `null` (C#) lub `Nothing` (Visual Basic), a nie chcesz wykonać pozostałej części kodu w metodzie. Następnie metoda sprawdza kolor tekstu wybranej etykiety za pomocą etykiety **ForeColor** właściwości. Jeśli kolor tekstu etykiety jest czarny, oznacza to, że ikona jest już wybrana, a metoda jest wykonana. (Właśnie to `return` wykonuje instrukcja: mówi programowi, aby zatrzymał wykonywanie metody.) W przeciwnym razie ikona nie została wybrana, więc program zmienia kolor tekstu etykiety na czarny.  
  
6.  Na pasku menu wybierz **pliku**, **Zapisz wszystko** Aby zapisać postęp, a następnie na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** do uruchomienia program. Powinien zostać wyświetlony pusty formularz z niebieskim tłem. Wybierz którąś komórkę w formularzu, jedna z ikon powinna się stać widoczna. Kontynuuj wybieranie różnych miejsc w formularzu. Ikony powinny się pojawiać w miarę wybierania.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 5: Add Label References](../ide/step-5-add-label-references.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 3: przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md).



