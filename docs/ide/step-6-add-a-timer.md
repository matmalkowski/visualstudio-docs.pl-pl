---
title: 'Krok 6: Dodawanie czasomierza'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aac60356eb484b0da81502e713a864a9b8261ccf
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="step-6-add-a-timer"></a>Krok 6: Dodawanie czasomierza
Następnie dodaj <xref:System.Windows.Forms.Timer> formantu do dopasowania gry. Czasomierz określoną liczbę milisekund oczekiwania, a następnie wyzwala zdarzenie, określany jako *znaczników*. Jest to przydatne dla rozpoczęcia czynności lub regularnego powtarzania czynności. W tym przypadku, będziesz używał czasomierza, aby umożliwić graczom wybór dwóch ikon, a jeśli ikony nie będą pasowały, ukryć te dwie ikony po krótkiej chwili.  
  
## <a name="to-add-a-timer"></a>Aby dodać czasomierz  
  
1.  Z przybornika w **Projektant formularzy systemu Windows**, wybierz **czasomierza** (w **składniki** kategorii), a następnie wybierz **Enter** klucza, lub Kliknij dwukrotnie czasomierza, aby dodać kontrolkę czasomierza do formularza. Ikona czasomierza, nazywany **czasomierz 1**, powinien zostać wyświetlony w obszarze poniżej formularza, jak pokazano na poniższej ilustracji.  
  
     ![Czasomierz](../ide/media/express_timer.png "Express_Timer")  
**Timer**  
  
    > [!NOTE]
    >  Jeśli przybornik jest pusty, należy wybrać Projektant formularzy, a nie kod związany z formularzem, przed otwarciem przybornika.  
  
2.  Wybierz **czasomierz 1** ikonę, aby wybrać czasomierza. W **właściwości** okna, przełącznika z wyświetlanie zdarzeń, aby wyświetlić właściwości. Następnie należy skonfigurować czasomierz **interwał** właściwości **750**, pozostawiając jego **włączone** ustawioną właściwość **False**. **Interwał** właściwości informuje, jak długo czekać między czasomierza *Takty*, lub gdy wyzwala jego <xref:System.Windows.Forms.Timer.Tick> zdarzeń. Wartość 750 mówi czasomierzowi, aby czekał trzy czwarte sekundy (750 milisekund), zanim uruchomi zdarzenie Taktu. Będzie wywoływać <xref:System.Windows.Forms.Timer.Start> metodę, aby uruchomić czasomierza tylko wtedy, gdy odtwarzacz wybiera drugą etykietę.  
  
3.  Wybierz licznik ikonę kontroli w **Projektant formularzy systemu Windows** , a następnie wybierz **Enter** klucza, lub kliknij dwukrotnie czasomierz, aby dodać pusty program obsługi zdarzeń znaczników. Zastąp kod następującym kodem lub ręcznie wprowadź następujący kod do programu obsługi zdarzeń.  
  
     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]  
  
     Program obsługi zdarzeń Tick wykonuje trzy czynności: najpierw pozwala sprawdzić, nie jest uruchomiony czasomierza, wywołując <xref:System.Windows.Forms.Timer.Stop> metody. Następnie używa dwie zmienne odwołujące `firstClicked` i `secondClicked`, ponownie ukryć ikony dwie etykiety, które wybrano odtwarzacza. Ponadto resetuje `firstClicked` i `secondClicked` odwoływać się do zmiennych do `null` języka Visual C# i `Nothing` w języku Visual Basic. Ten krok jest ważny, ponieważ w ten sposób program się resetuje. Teraz on jest nie rejestrowanie informacji o dowolnej <xref:System.Windows.Forms.Label> formantów, a jego gotowe do odtwarzacza ponownie wybrać etykietę.  
  
    > [!NOTE]
    >  Obiekt czasomierza ma `Start()` metodę, która uruchamia czasomierz, a `Stop()` metodę, która go zatrzyma. Podczas ustawiania czasomierza **włączone** właściwości **True** w **właściwości** okna, uruchamia zaznaczenie natychmiast rozpoczyna się program. Ale wychodząc ustawioną **False**, nie uruchamia materacy aż do jego `Start()` metoda jest wywoływana. Zwykle czasomierza wyzwala jej zdarzenia znaczników wielokrotnie, przy użyciu **interwał** właściwości w celu określenia liczby milisekund oczekiwania między taktami. Można zauważyć, jak czasomierza `Stop()` metoda jest wywoływana wewnątrz zdarzenia znaczników. Który umieszcza czasomierza do *jeden tryb zrzut*, co oznacza, że w przypadku `Start()` metoda jest wywoływana, czeka na określony czas, wyzwala pojedyncze zdarzenie znaczników i zatrzymywany.  
  
4.  Aby zobaczyć nowe czasomierza w akcji, przejdź do edytora kodu i Dodaj następujący kod do góry i u dołu `label_Click()` metoda obsługi zdarzeń. (W przypadku dodawania `if` instrukcji u góry i trzy instrukcje do dołu; pozostałe metody pozostaje taki sam.)  

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]  

     Kod w górnej części metoda sprawdza, czy czasomierz zostało uruchomione przez wartości **włączone** właściwości. Dzięki temu, jeśli odtwarzacz wybierze pierwszy i drugi etykiety kontrolki i uruchamia czasomierz, wybieranie trzeci etykiety nie będzie wykonywać żadnych czynności.  
  
     Kod w dolnej części zestawy metody `secondClicked` zmiennej odwołania do śledzenia drugiego formantu etykiety, czy wybrane odtwarzacza, a następnie ustawia kolor ikony tej etykiety na kolor czarny, aby go wyświetlić. Następnie uruchamia czasomierz w trybie jednego zadziałania, tak że czeka on 750 milisekund, a następnie uruchamia pojedyncze zdarzenie Taktu. Program obsługi zdarzeń Tick czasomierza ukrywa dwie ikony i resetuje `firstClicked` i `secondClicked` odwoływać się do zmiennych, formularz jest gotowy do odtwarzacza wybrać inną parę ikon.  
  
5.  Zapisz i uruchom program. Wybierz ikonę, stanie się widoczna.  

6.  Wybierz inną ikonę. Pojawi się ona na chwilę, a następnie obie ikony znikną. Powtórz to wiele razy. Formularz teraz śledzi pierwszą i drugą wybraną ikonę i używa czasomierza, aby wstrzymać przed zniknięciem ikon.  

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [kroku 7: zachowanie widoczności par](../ide/step-7-keep-pairs-visible.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5: Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md).
