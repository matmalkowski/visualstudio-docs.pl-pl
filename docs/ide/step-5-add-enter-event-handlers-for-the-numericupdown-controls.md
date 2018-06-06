---
title: 'Krok 5: Dodawanie obsługi zdarzeń Enter dla formantów NumericUpDown'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e05d6cc201819d37e77587529ffd79a740003a10
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747922"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Krok 5: Dodawanie obsługi zdarzeń Enter dla formantów NumericUpDown
W piątym części tego samouczka zostanie dodana <xref:System.Windows.Forms.Control.Enter> procedury obsługi zdarzeń, aby wprowadzanie odpowiedzi na problemy kwizu łatwiejsza. Ten kod będzie wybrać i wyczyścić bieżącą wartość w każdym <xref:System.Windows.Forms.NumericUpDown> kontrolować natychmiast przyjmującego kwizu wybierze go i rozpoczyna wprowadź inną wartość.

> [!NOTE]
>  Ten temat jest częścią samouczek serii o podstawowych pojęciach kodowania. Omówienie samouczka, zobacz [samouczek 2: tworzenie kwizu matematycznego](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-the-default-behavior"></a>Aby sprawdzić zachowanie domyślne

1.  Uruchom program, a następnie uruchom kwizu.

     W **NumericUpDown** kontrolować problemu dodanie kursor miga obok **0** (zero).

2.  Wprowadź **3**i należy pamiętać, że formant zawiera **30**.

3.  Wprowadź **5**i zwróć uwagę, że **350** pojawia się, ale zmiany **100** po drugiej.

     Aby rozwiązać ten problem, pomyśl o tym, co dzieje. Należy wziąć pod uwagę dlaczego **0** nie zniknąć po wprowadzeniu **3** i dlaczego **350** zmieniony na **100** , ale nie natychmiast.

     To zachowanie może wydawać się nieodpowiednie, ale dobrym rozwiązaniem jest podany logika kodu. Po wybraniu **Start** przycisku, jego **włączone** właściwość jest ustawiona na **False**, i przycisku jest przyciemnione i niedostępne. Program zmienia bieżące zaznaczenie (fokus) do formantu, który ma dalej wartość TabIndex najniższy, która jest formantu NumericUpDown problem dodawania. Jeśli używasz **kartę** klucza, aby przejść do formantu NumericUpDown, automatycznie kursora na początku formantu, dlatego numery, które należy wprowadzić są wyświetlane od lewej strony, a nie z prawej strony. Po określeniu numeru jest wyższa niż wartość **MaximumValue** właściwość, która jest ustawiona na 100, numer wprowadzony zostanie zastąpiony wartością tej właściwości.

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Aby dodać obsługę zdarzeń Enter dla formantu NumericUpDown

1.  Wybierz pierwsze **NumericUpDown** formantu (o nazwie "sum") na formularzu, a następnie w **właściwości** okna dialogowego wybierz **zdarzenia** ikonę na pasku narzędzi.

     **Zdarzenia** karcie **właściwości** okno dialogowe wyświetla wszystkie zdarzenia, które mogą odpowiadać (obsłużyć) dla elementu wybranego w formularzu. Ponieważ wybrano formantu NumericUpDown wszystkie zdarzenia wymienione odnoszą się do niego.

2.  Wybierz **Enter** zdarzeń, wprowadź `answer_Enter`, a następnie wybierz pozycję **Enter** klucza.

     ![Okno dialogowe właściwości](../ide/media/express_answerenter.png)
**właściwości** — okno dialogowe

     Program obsługi zdarzeń Enter właśnie dodano sumy formantu NumericUpDown i nazwanego obsługi **answer_Enter**.

3.  W metodzie dla **answer_Enter** program obsługi zdarzeń, Dodaj następujący kod.

     [!code-vb[VbExpressTutorial3Step5_6#11](../ide/codesnippet/VisualBasic/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#11](../ide/codesnippet/CSharp/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.cs)]

     Ten kod może wyglądać złożonego, ale można go zrozumieć, jeśli przyjrzymy się krok po kroku. Najpierw sprawdź, w górnej części metody: `object sender` w języku C# lub `sender As System.Object` w języku Visual Basic. Ten parametr odwołuje się do obiektu, którego zdarzenie jest uruchamiane, nosi nazwę nadawcy. W takim przypadku obiekt nadawcy jest numericupdown — formant. Tak w pierwszym wierszu metody, należy określić dowolnego obiektu ogólnego, ale w szczególności numericupdown — formant nie jest nadawcy. (Każdego formantu NumericUpDown jest obiektem, ale nie każdy obiekt jest formantu NumericUpDown). Numericupdown — formant nosi nazwę **answerBox** w ramach tej metody, ponieważ będzie służyć do wszystkich formantów NumericUpDown w formularzu, nie tylko suma NumericUpDown kontroli. Ponieważ deklaruje zmienną answerBox w ramach tej metody, jej zakres ma zastosowanie tylko do tej metody. Innymi słowy zmienna może być używana tylko w ramach tej metody.

     Następnego wiersza sprawdza, czy answerBox został pomyślnie przekonwertowany (rzutowania) z obiektu do formantu NumericUpDown. Jeśli konwersja nie powiodła się, zmienna będzie mieć wartość `null` (C#) lub `Nothing` (Visual Basic). Trzeci wiersz pobiera długość odpowiedź, która jest wyświetlana w formancie NumericUpDown i czwartego wiersza Zaznacza bieżącą wartość kontrolki oparte na tej długości. Teraz gdy przyjmującego kwizu wybierze formantu, Visual Studio generuje to zdarzenie, co powoduje, że bieżącej odpowiedzi, należy wybrać. Jak przyjmującego kwizu zaczyna być wprowadź inną odpowiedź, poprzedniej odpowiedzi jest wyczyszczone i zastąpione nową odpowiedź.

4.  W **Projektant formularzy systemu Windows**, wybierz różnica **NumericUpDown** formantu.

5.  W **zdarzenia** strony **właściwości** okno dialogowe, przewiń w dół do **Enter** zdarzenia, wybierz strzałkę listy rozwijanej na końcu wiersza, a następnie wybierz `answer_Enter`obsługi zdarzeń, który właśnie został dodany.

6.  Powtórz poprzedni krok dla formantów NumericUpDown produktu i iloraz.

7.  Zapisz programu, a następnie uruchom go.

     Po wybraniu **NumericUpDown** kontroli, istniejąca wartość jest automatycznie wybierane i następnie wyczyszczone po uruchomieniu wprowadź inną wartość.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 6: Dodawanie problemu odejmowania](../ide/step-6-add-a-subtraction-problem.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4: Dodawanie metody CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).
