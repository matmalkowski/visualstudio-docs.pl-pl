---
title: Czas odpowiedzi strony w teście obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ba6a5b666777e692fe2c214f165c0bc1da7fee9d
ms.sourcegitcommit: 893c09d58562c378a4ba057bf2a06bde1c80df90
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/18/2018
ms.locfileid: "35676230"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Porady: wyświetlanie czasu odpowiedzi strony Web w czasie testu obciążenia za pomocą analizatora testów obciążenia

Czas potrzebny na każdej stronie sieci Web załadować jest znany jako *czas odpowiedzi*. Podczas tworzenia testu wydajności sieci Web, można ustawić docelowy czas odpowiedzi dla każdego żądania strony sieci Web w teście wydajności sieci Web.

Po uruchomieniu testu wydajności sieci Web przy dużym obciążeniu w teście obciążeniowym, możliwe będzie analizowanie następujących informacji dla każdej strony:

-   Średni czas odpowiedzi dla strony.

-   Procent iteracji testowych, które spełniają docelowy czas odpowiedzi dla strony.

-   Czasy reakcji stron sieci Web można analizować za pomocą widoku tabeli lub widoku wykresu w analizatorze testu obciążenia:

-   Analizowanie czasy reakcji stron sieci Web w widoku tabeli

-   Analizowanie czasy reakcji stron sieci Web w widoku wykresu

## <a name="view-response-time-data-in-a-table"></a>Dane czasu odpowiedzi widok tabeli

### <a name="to-view-response-time-data-in-a-table"></a>Aby wyświetlić dane czasu odpowiedzi w tabeli

1.  W analizatorze testu obciążenia wybierz **tabel** na pasku narzędzi, aby upewnić się, że wyświetlana jest siatka tabeli.

2.  W **tabeli** listy rozwijanej wybierz pozycję **stron**.

3.  Dane dla każdej strony są wyświetlane w siatce. Zazwyczaj są wyświetlane następujące kolumny.

    |Nagłówek kolumny|Opis|
    |-|-|
    |**Strona**|Nazwa strony sieci Web.|
    |**Scenariusz**|Nazwa scenariusza. Ważne, jeśli masz więcej niż jeden scenariusz w teście wydajności sieci Web.|
    |**Test**|Nazwa testu wydajności sieci Web. Ważne, jeśli masz więcej niż jeden test wydajności sieci Web w teście obciążenia.|
    |**Sieci**|Typ sieci.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
    |**Łączna liczba**|Całkowita liczba żądań, które zostały wprowadzone dla strony sieci Web. Jest to suma dla wszystkich iteracji w teście obciążeniowym.|
    |**Zapisz**|Średniego czasu odpowiedzi strony.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
    |**Min**|Czas odpowiedzi strony minimalnej.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
    |**Mediana**|Mediana czasu odpowiedzi strony na.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
    |**90%**|90. percentyla dla czasu odpowiedzi. To wskazuje, że 90% stron szybciej niż ta liczba wysłanych jako odpowiedzi i 10% stron odpowiedzi wolniej.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
    |**95%**|95. percentyl czasu odpowiedzi. To wskazuje, że 95% stron szybciej niż ta liczba wysłanych jako odpowiedzi i 5 procent stron odpowiedzi wolniej.|
    |**99%**|99. percentylu na czas odpowiedzi. Oznacza to, że 99% stron szybciej niż ta liczba wysłanych jako odpowiedzi, a 1% stron odpowiedzi wolniej.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
    |**Maksymalna**|Strona maksymalny czas odpowiedzi.<br /><br /> Te dane nie są zbierane domyślnie. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
    |**Odchylenie standardowe**|Domyślnie nie są zbierane dane odchylenia standardowego. Aby zbierać dane, w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł uruchomieniowy, aby zmienić. W **właściwości** oknie dla **przechowywanie informacji** wybierz **AllIndividualDetails**.|
    |**Czas strony**|Średni czas odpowiedzi dla wszystkich żądań, które zostały wprowadzone dla strony sieci Web.|
    |**Cel**|Cel dotyczący czasu strony. Jest to wartość stałą dla strony. **Uwaga:** cel dotyczący czasu strona jest wyświetlana tylko wtedy, gdy celem został zdefiniowany dla żądania w teście wydajności sieci Web.|
    |**% Osiągnięcia celu**|Procent żądań, które zostały wprowadzone na stronie sieci Web, że zostały spełnione cel dotyczący czasu odpowiedzi.|

 Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Dane czasu odpowiedzi widoku w postaci wykresu

Można również wyświetlić dane czasu odpowiedzi na wykresie, aby zobaczyć, jak zmienia się wraz z upływem czasu podczas testu obciążenia. Jest to szczególnie przydatne, jeśli Twoja wzorca obciążenia zwiększa się po uruchomieniu testów (na przykład, jeśli używasz krokowego wzorca obciążenia). Aby uzyskać więcej informacji, zobacz [Edytowanie wzorców obciążenia w celu modelu wirtualnego aktywności użytkownika](../test/edit-load-patterns-to-model-virtual-user-activities.md).

### <a name="to-view-response-time-data-in-a-graph"></a>Aby wyświetlić dane czasu odpowiedzi w formie wykresu

1.  W analizatorze testu obciążenia wybierz **wykresów** na pasku narzędzi, aby upewnić się, czy są wyświetlane na wykresie.

2.  W **liczniki** okna, rozwiń węzeł scenariusz, w którym interesuje Cię (na przykład `Scenario1`).

3.  Rozwiń węzeł testu wydajności sieci Web, w którym interesuje Cię.

4.  Rozwiń węzeł **stron**.

5.  Rozwiń węzeł strony, w którym interesuje Cię.

6.  Kliknij prawym przyciskiem myszy **% stron osiągnięcia celu** , a następnie wybierz **Pokaż licznik na wykresie**.

     Dane są dodawane do grafu.

7.  (Opcjonalnie) Powtórz poprzedni krok dla średni Czas strony, cel dotyczący czasu odpowiedzi strony, a łączna liczba stron.

    > [!NOTE]
    > Cel dotyczący czasu odpowiedzi strony jest stałe.

 Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia w widoku wykresy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Porady: uzyskiwanie dostępu do wyników testu obciążenia dla analizy](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)