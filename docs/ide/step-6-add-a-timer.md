---
title: 'Krok 6: Dodawanie czasomierza | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: "21"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 530b57b0f8a39990d37dc8cd25ac4c7bacba5a6e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="step-6-add-a-timer"></a>Krok 6. Dodawanie czasomierza
Następnie dodaj **czasomierza** formantu do dopasowania gry. Czasomierz określoną liczbę milisekund oczekiwania, a następnie wyzwala zdarzenie, określany jako *znaczników*. Jest to przydatne dla rozpoczęcia czynności lub regularnego powtarzania czynności. W tym przypadku, będziesz używał czasomierza, aby umożliwić graczom wybór dwóch ikon, a jeśli ikony nie będą pasowały, ukryć te dwie ikony po krótkiej chwili.  
  
### <a name="to-add-a-timer"></a>Aby dodać czasomierz  
  
1.  Z przybornika projektanta formularzy systemu Windows, wybierz **czasomierza** (w **składniki** kategorii), a następnie wybierz klawisz ENTER lub kliknij dwukrotnie czasomierza, aby dodać kontrolkę czasomierza do formularza. Ikona czasomierza, nazywany **czasomierz 1**, powinien zostać wyświetlony w obszarze poniżej formularza, jak pokazano na poniższej ilustracji.  
  
     ![Czasomierz](../ide/media/express_timer.png "Express_Timer")  
Czasomierz  
  
    > [!NOTE]
    >  Jeśli przybornik jest pusty, należy wybrać Projektant formularzy, a nie kod związany z formularzem, przed otwarciem przybornika.  
  
2.  Wybierz **czasomierz 1** ikonę, aby wybrać czasomierza. W **właściwości** okna, przełącznika z wyświetlanie zdarzeń, aby wyświetlić właściwości. Następnie należy skonfigurować czasomierz **interwał** właściwości **750**, pozostawiając jego **włączone** ustawioną właściwość **False**. **Interwał** właściwości informuje, jak długo czekać między czasomierza *Takty*, lub gdy wyzwalane jest zdarzenie znaczników. Wartość 750 mówi czasomierzowi, aby czekał trzy czwarte sekundy (750 milisekund), zanim uruchomi zdarzenie Taktu. Będzie wywoływać `Start()` metodę, aby uruchomić czasomierza tylko wtedy, gdy odtwarzacz wybiera drugą etykietę.  
  
3.  Wybierz licznik kontrolować ikonę w Projektant formularzy systemu Windows, a następnie wybierz klawisz ENTER lub kliknij dwukrotnie czasomierz, aby dodać pustą **znaczników** obsługi zdarzeń. Zastąp kod następującym kodem lub ręcznie wprowadź następujący kod do programu obsługi zdarzeń.  
  
     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]  
  
     Program obsługi zdarzeń Tick wykonuje trzy czynności: najpierw pozwala sprawdzić, nie jest uruchomiony czasomierza, wywołując `Stop()` metody. Następnie używa dwie zmienne odwołujące `firstClicked` i `secondClicked`, ponownie ukryć ikony dwie etykiety, które wybrano odtwarzacza. Ponadto resetuje `firstClicked` i `secondClicked` odwoływać się do zmiennych do `null` języka Visual C# i `Nothing` w języku Visual Basic. Ten krok jest ważny, ponieważ w ten sposób program się resetuje. Teraz on jest nie rejestrowanie informacji o dowolnej `Label` formantów, a jego gotowe do odtwarzacza ponownie wybrać etykietę.  
  
    > [!NOTE]
    >  A `Timer` obiekt ma `Start()` metodę, która uruchamia czasomierz, a `Stop()` metodę, która go zatrzyma. Podczas ustawiania czasomierza **włączone** właściwości **True** w **właściwości** okna, uruchamia zaznaczenie natychmiast rozpoczyna się program. Ale wychodząc ustawioną **False**, nie uruchamia materacy aż do jego `Start()` metoda jest wywoływana. Zwykle czasomierza wyzwala jej zdarzenia znaczników wielokrotnie, przy użyciu **interwał** właściwości w celu określenia liczby milisekund oczekiwania między taktami. Można zauważyć, jak czasomierza `Stop()` metoda jest wywoływana wewnątrz zdarzenia znaczników. Który umieszcza czasomierza do *jeden tryb zrzut*, co oznacza, że w przypadku `Start()` metoda jest wywoływana, czeka na określony czas, wyzwala pojedyncze zdarzenie znaczników i zatrzymywany.  
  
4.  Aby zobaczyć nowe czasomierza w akcji, przejdź do edytora kodu i Dodaj następujący kod do góry i u dołu `label_Click()` metoda obsługi zdarzeń. (W przypadku dodawania `if` instrukcji u góry i trzy instrukcje do dołu; pozostałe metody pozostaje taki sam.)  
  
     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]  
  
     Kod w górnej części metoda sprawdza, czy czasomierz zostało uruchomione przez wartości **włączone** właściwości. Dzięki temu, jeśli odtwarzacz wybierze pierwszy i drugi `Label` kontrolek i uruchamia czasomierz, wybierając trzeci etykiety nie będzie wykonywać żadnych czynności.  
  
     Kod w dolnej części zestawy metody `secondClicked` zmiennej odwołania do śledzenia drugi `Label` formantu, czy wybrane odtwarzacza, a następnie ustawia kolor ikony tej etykiety na kolor czarny, aby go wyświetlić. Następnie uruchamia czasomierz w trybie jednego zadziałania, tak że czeka on 750 milisekund, a następnie uruchamia pojedyncze zdarzenie Taktu. Program obsługi zdarzeń Tick czasomierza ukrywa dwie ikony i resetuje `firstClicked` i `secondClicked` odwoływać się do zmiennych, formularz jest gotowy do odtwarzacza wybrać inną parę ikon.  
  
5.  Zapisz i uruchom program. Wybierz ikonę, stanie się widoczna.  
  
6.  Wybierz inną ikonę. Pojawi się ona na chwilę, a następnie obie ikony znikną. Powtórz to wiele razy. Formularz teraz śledzi pierwszą i drugą wybraną ikonę i używa czasomierza, aby wstrzymać przed zniknięciem ikon.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [kroku 7: Zachowaj widoczne pary](../ide/step-7-keep-pairs-visible.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5: Dodaj odwołania do etykiet](../ide/step-5-add-label-references.md).