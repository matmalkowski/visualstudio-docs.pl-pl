---
title: Powiększanie wykresy wyników testu obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: a61d53e8dbdbbce9c5a09fc8f8cd180a8b312d2c
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750974"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Porady: powiększanie obszaru wykresu w wynikach testów obciążenia

Po zakończeniu testu obciążenia umożliwia paski powiększenia powiększanie i przewijanie do obszaru wykresu. Powiększając należy zbadać danych, który został wygenerowany podczas testu obciążenia szczegółowo bardziej precyzyjną.

> [!NOTE]
> Powiększ, jest dostępna tylko podczas analizowania wynik zakończonego testu obciążenia, gdy są obserwowania wyniki podczas testu.

 Formant powiększania jest widoczna tylko w analizatora testu obciążenia, podczas wyświetlania wyniku testu obciążenia w trybie powiększania. Po zakończeniu testu obciążenia lub testu obciążenia, który został wcześniej uruchomiony jest załadowany, w widoku wykresu ustanawiany jest tryb powiększenia. Możesz wyświetlić lub ukryć kontrolki powiększania na wykresach za pomocą Pokaż formantów Powiększenie na pasku narzędzi.

 Wartość powiększenia osi poziomej można dostosować do analizowania określonych okresach podczas testu obciążenia. Powiększenie Pionowa oś y można dostosować do analizowania zakresów określonych wartości liczników, które znajdują się na wykresie.

 Zarówno osi poziomej i kontrolki powiększania zakres wartości pionowej można dostosować za pomocą myszy. Formant osi poziomej również można dostosować za pomocą klawiszy Strzałka w lewo i w prawo. Za pomocą klawiszy strzałek, aby dopasować formantu powiększenia, można dostosować zakres windows interwał próbkowania 1 naraz. Za pomocą klawiszy SHIFT i Strzałka sprawia, że dostosowania 10 interwałami próbkowania.

 Aby dostosować formantu powiększenia za pomocą strzałki, najpierw ustaw fokus w formancie powiększenia za pomocą klawisza TAB. Po aktywowaniu suwaka po lewej stronie, klawiszy strzałek przeniesie początkową krawędzią okna powiększenia interwał 1, lewo lub w prawo. Gdy fokus jest ustawiony na suwaku center, możesz użyj klawiszy strzałek przewiń powiększenia okna lewego lub prawego 1 interwał próbkowania bez zmiany rozmiaru okna powiększenia. A na koniec zostanie przesunięty suwak po prawej stronie, rozszerzenia lub ograniczenia zakresu koniec okna powiększenia 1 interwał próbkowania.

 Aby przywrócić kontrolki powiększania poziomie i w pionie, aby wyświetlić pełną osi czasu i zakresów wartości, można użyć **powiększenie limit poziomy** opcji **powiększenie limit pionowy** opcji lub **Pomniejsz Zarówno** opcję w menu podręcznym na wykresie.

> [!TIP]
> Można użyć **zsynchronizować poziome powiększenie formanty** na pasku narzędzi na włączenie lub wyłączenie automatycznego powiększenia poziome synchronizacji. Przy synchronizacji w dowolnej powiększanie dotyczą zostanie wykres również być zastosowane do innych wykresy w widoku wykresu.

 ![Formant powiększania widoku wykresu](../test/media/ltest_zoomcontrol.png) Powiększenie widoku wykresu

 Na poprzedniej ilustracji System w obszarze wykresu testu ma została powiększona do badania problemów próg. Włączono naruszeń progu za pomocą **Pokaż naruszenia progowe na wykres** z **Opcje wykresu** listy rozwijanej na pasku narzędzi.

 Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="displaying-graphs"></a>Wyświetlanie wykresów
 Przed zmianą wyświetlania wykresu powiększanie lub pomniejszanie lub przewijania, wykonaj poniższą procedurę, aby wyświetlić wykresy.

### <a name="to-display-graphs"></a>Aby wyświetlić wykresy

1.  Uruchom test obciążeniowy, aż zostanie zakończony.

2.  Po zakończeniu testu obciążenia. Wybierz **tak** w oknie dialogowym z pytaniem o wyświetlaniu wyników z wyników testów obciążenia przechowywania.

     \- lub -

     Wyświetl szczegóły wcześniej uruchomionego testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [porady: dostęp do wyników testu obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

3.  Wybierz **wykresy** Jeśli wykresów nie są wyświetlane.

4.  Jeśli nie są wyświetlane paski powiększenia, wybierz **Pokaż kontrolek powiększenie**.

     Dwa paski powiększenia są dostępne dla każdego wykresu. Z lewej strony wykresu zostanie wyświetlony pasek powiększenia, kontrolujące skali pionowej. W obszarze wykresu zostanie wyświetlony pasek powiększenia, która kontroluje, skalowanie w poziomie.

     Każdy pasek powiększenia ma dwa uchwytów. Dojście jest prostokątny obszar na końcach pasku powiększenia.

## <a name="zooming-and-scrolling"></a>Powiększanie i przewijanie
 Jeśli masz wiele wykresy wyświetlane zachowania synchronizowane, dzięki czemu są one wyświetlane tę samą część uruchomienia testu obciążenia.

### <a name="to-synchronize-zooming-and-scrolling"></a>Aby zsynchronizować powiększania i przewijania

1.  Na analizatora testu obciążenia, wybierz **zsynchronizować poziome powiększenie formanty**.

     Po wybraniu przycisk Synchronizuj poziome powiększenie formantów powiększania i przewijania skali czasu wykresu poszczególnych również powiększa i przewija skali czasu z innymi wykresami.

2.  Ponownie wybierz zsynchronizować poziome powiększenie kontrolki.

     Przycisk Synchronizuj poziome powiększenie formantów nie jest zaznaczona, powiększania i przewijania skali czasu wykresu poszczególnych dotyczy tylko do tego wykresu.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Na powiększanie i przewijanie do obszaru wykresu

1.  Na pasku powiększenia wykresu przeciągnij uchwyt po lewej stronie z prawej strony.

     To powiększenie dalszej części tego uruchomienia testu. Podobnie przeciągnij uchwyt po prawej stronie w lewo powiększenie wcześniejszej części uruchomienia testu.

2.  Aby powiększyć konkretnego obszaru, przesuń zarówno dojść do środka wykresu.

     Bliższe dwa uchwyty są do każdego innego im bardziej powiększania do wyświetlenia krótszy, bardziej precyzyjną segmentów testu obciążenia.

     Wybierz w górnej części paska powiększenia, a następnie przeciągnij ją do przewiń do określonego punktu w teście obciążenia.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Aby powiększyć do obszaru wykresu, wybieranie i przeciągając

1.  Wybierz wykres z jednej strony obszar powiększenia.

2.  Przeciągnij wskaźnik myszy na końcu obszaru powiększenia.

3.  Zwolnij przycisk myszy.

     Zwiększa to obszar zdefiniowany przez wybranie i przeciągając.

 W poniższej procedurze opisano, jak szybko pomniejszyć bez konieczności dostosować punkty końcowe na pasku powiększenia.

### <a name="to-zoom-out"></a>Aby pomniejszyć

1.  Kliknij prawym przyciskiem myszy wykres powiększony w.

2.  W menu skrótów wybierz **powiększenie limit poziomy**.

     To zmniejsza pokazanie wykonywania cały czas trwania testu obciążenia.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Porady: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)