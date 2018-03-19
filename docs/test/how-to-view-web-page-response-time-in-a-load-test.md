---
title: "Czas odpowiedzi strony w teście obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 055bb9b9ae369cd6b62741f7d23295c34b7d1d32
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Porady: wyświetlanie czasu odpowiedzi strony Web w czasie testu obciążenia za pomocą analizatora testów obciążenia

Czas potrzebny na każdej stronie sieci Web załadować nosi nazwę *czas odpowiedzi*. Podczas tworzenia testu wydajności sieci Web, można ustawić czas odpowiedzi dla każdego żądania strony sieci Web w teście wydajności sieci Web.

Po uruchomieniu testu wydajności sieci Web mocno obciążony w teście obciążenia można analizować następujące informacje dotyczące każdej strony:

-   Średni czas odpowiedzi dla strony.

-   Procent iteracji testowych, które spełniają cel dotyczący czasu odpowiedzi dla strony.

-   Czas odpowiedzi strony sieci Web można analizować przy użyciu widoku tabeli lub widoku wykresu analizatora testu obciążenia:

-   Analizowanie czasu odpowiedzi strony sieci Web w widoku tabeli

-   Analizowanie czasu odpowiedzi strony sieci Web w widoku wykresu

## <a name="view-response-time-data-in-a-table"></a>Wyświetl dane czasu odpowiedzi w tabeli

### <a name="to-view-response-time-data-in-a-table"></a>Aby wyświetlić dane czasu odpowiedzi w tabeli

1.  W analizatorze testów obciążenia, wybierz **tabel** na pasku narzędzi, aby upewnić się, że jest wyświetlana siatka tabeli.

2.  W **tabeli** listy rozwijanej wybierz pozycję **stron**.

3.  Dane dla każdej strony są wyświetlane w siatce. Zazwyczaj są wyświetlane następujące kolumny.

    |||
    |-|-|
    |**Strona**|Nazwa strony sieci Web.|
    |**Scenariusz**|Nazwa scenariusza. Ważne, jeśli masz więcej niż jednego scenariusza w teście wydajności sieci Web.|
    |**Test**|Nazwa testu wydajności sieci Web. Ważne, jeśli masz więcej niż jeden test wydajności sieci Web w teście obciążenia sieci.|
    |**Sieci**|Typ sieci.<br /><br /> Domyślnie te dane nie są zbierane. Do zbierania tych danych w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł ustawień, aby zmienić. W **właściwości** okna, aby uzyskać **magazynowania szczegółów chronometrażu** właściwości, wybierz opcję **AllIndividualDetails**.|
    |**Całkowita liczba**|Całkowita liczba żądań, które zostały wprowadzone na stronie sieci Web. Jest to suma dla wszystkich iteracji w teście obciążenia.|
    |**Zapisz**|Czas odpowiedzi strony.<br /><br /> Domyślnie te dane nie są zbierane. Do zbierania tych danych w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł ustawień, aby zmienić. W **właściwości** okna, aby uzyskać **magazynowania szczegółów chronometrażu** właściwości, wybierz opcję **AllIndividualDetails**.|
    |**Min**|Czas odpowiedzi strony minimalnej.<br /><br /> Domyślnie te dane nie są zbierane. Do zbierania tych danych w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł ustawień, aby zmienić. W **właściwości** okna, aby uzyskać **magazynowania szczegółów chronometrażu** właściwości, wybierz opcję **AllIndividualDetails**.|
    |**Mediana**|Czas odpowiedzi strony środkowej.<br /><br /> Domyślnie te dane nie są zbierane. Do zbierania tych danych w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł ustawień, aby zmienić. W **właściwości** okna, aby uzyskać **magazynowania szczegółów chronometrażu** właściwości, wybierz opcję **AllIndividualDetails**.|
    |**90%**|90-procentowy czas odpowiedzi. To wskazuje, że 90% stron szybciej niż ta liczba odpowiedzi i 10% stron odpowiedział wolniej.<br /><br /> Domyślnie te dane nie są zbierane. Do zbierania tych danych w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł ustawień, aby zmienić. W **właściwości** okna, aby uzyskać **magazynowania szczegółów chronometrażu** właściwości, wybierz opcję **AllIndividualDetails**.|
    |**95%**|95. percentyl czas odpowiedzi. To wskazuje, że 95% stron szybciej niż ta liczba odpowiedzi i 5% stron odpowiedział wolniej.|
    |**99%**|99-ty percentyl czas odpowiedzi. To wskazuje, że 99% stron szybciej niż ta liczba odpowiedzi i 1% stron odpowiedział wolniej.<br /><br /> Domyślnie te dane nie są zbierane. Do zbierania tych danych w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł ustawień, aby zmienić. W **właściwości** okna, aby uzyskać **magazynowania szczegółów chronometrażu** właściwości, wybierz opcję **AllIndividualDetails**.|
    |**Max**|Strona maksymalny czas odpowiedzi.<br /><br /> Domyślnie te dane nie są zbierane. Do zbierania tych danych w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł ustawień, aby zmienić. W **właściwości** okna, aby uzyskać **magazynowania szczegółów chronometrażu** właściwości, wybierz opcję **AllIndividualDetails**.|
    |**Odchylenie standardowe**|Domyślnie dane odchylenie standardowe nie są zbierane. Do zbierania tych danych w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz węzeł ustawień, aby zmienić. W **właściwości** okna, aby uzyskać **magazynowania szczegółów chronometrażu** właściwości, wybierz opcję **AllIndividualDetails**.|
    |**Czas strony**|Średni czas odpowiedzi dla wszystkich żądań, które zostały wprowadzone na stronie sieci Web.|
    |**Cel**|Cel dotyczący czasu strony. Jest to wartość stałą dla strony. **Uwaga:** cel dotyczący czasu strona jest wyświetlana tylko wtedy, gdy cel został zdefiniowany dla żądania w teście wydajności sieci Web.|
    |**Celem spotkania %**|Procent żądań, które zostały dokonane spełnieniu czasu odpowiedzi strony sieci Web.|

 Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Wyświetl dane czasu odpowiedzi na wykresie

Można również wyświetlić dane czasu odpowiedzi na wykresie, aby zobaczyć, jak zmieniają się w czasie testu obciążenia. Jest to szczególnie przydatne, jeśli z wzorca obciążenia zwiększa podczas działania testu (na przykład, jeśli używasz krokowego wzorca obciążenia). Aby uzyskać więcej informacji, zobacz [Edytowanie wzorców obciążenia w celu działania dotyczące modelu wirtualnego użytkownika](../test/edit-load-patterns-to-model-virtual-user-activities.md).

### <a name="to-view-response-time-data-in-a-graph"></a>Aby wyświetlić dane czasu odpowiedzi na wykresie

1.  W analizatorze testów obciążenia, wybierz **wykresy** na pasku narzędzi, aby upewnić się, że jest wyświetlany wykres.

2.  W **liczniki** okna, rozwiń węzeł scenariusz, w której jesteś zainteresowany (na przykład `Scenario1`).

3.  Rozwiń węzeł testu wydajności sieci Web, w której jesteś zainteresowany.

4.  Rozwiń węzeł **stron**.

5.  Rozwiń węzeł strony, w której jesteś zainteresowany.

6.  Kliknij prawym przyciskiem myszy **% celem spotkania stron** , a następnie wybierz **Pokaż licznik na wykresie**.

     Dane są dodawane do wykresu.

7.  (Opcjonalnie) Powtórz poprzedni krok dla średni Czas strony, czas odpowiedzi strony i całkowita liczba stron.

    > [!NOTE]
    > Czas odpowiedzi strony jest stały.

 Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Porady: dostęp do analizy wyników testu obciążenia](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)