---
title: Analizowanie naruszeń zasady progu w testach obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 882b2511c547837466f45578031c86e6b0df9d74
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36234988"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Analizowanie naruszeń zasady progu w testach obciążenia za pomocą analizatora testu obciążenia

Reguły progu są skojarzone z konkretnych licznikach wydajności i naruszeń wskazywać, że licznika wydajności przekroczony lub spadła poniżej ustaw wartość. Po uruchomieniu testu obciążenia może analizowanie naruszeń zasady progu skonfigurowane wcześniej.

Jeśli nastąpiło naruszenie, **naruszenia progu** hiperłącze pojawia się na **analizatora testu obciążenia** paska stanu i określa liczbę naruszeń, które wystąpiły. Możesz wybrać hiperłącze, aby wyświetlić tabelę naruszenia progu. Można również wyświetlić naruszenia progu w **liczniki** okna, a na wykresie.

## <a name="view-threshold-violations-in-the-table"></a>Naruszenia progu widoku tabeli

 Tabela naruszenia progu Wyświetla pierwszych 1000 naruszeń. Poniższa tabela zawiera następujące kolumny:

|Kolumny|Opis|Domyślnie widoczne|
|------------|-----------------|------------------------|
|Godzina|Czas podczas ładowania testów, w którym nastąpiło naruszenie zasad.|Tak|
|Komputer|Nazwa komputera w ramach testu, w którym wystąpiło naruszenie. **Uwaga:** jest to ważne podczas uruchamiania testów obciążenia na platformy.|Tak|
|Kategoria|Kategoria licznika wydajności, w którym wystąpiło naruszenie.|Tak|
|Licznik|Nazwa licznika wydajności, w którym wystąpiło naruszenie.|Tak|
|Wystąpienie|Wystąpienie licznika wydajności, w którym wystąpiło naruszenie.|Tak|
|Komunikat|Komunikat, który opisuje naruszenie progu. Na przykład **wartość 5 przekracza wartość progu stanu krytycznego 0**.|Tak|

> [!NOTE]
> Tabeli można sortować, klikając nagłówki kolumn.

 Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Naruszenia progu widoku w panelu liczników

 Możesz wyświetlić naruszenia progu w **liczniki** panelu w drzewie listę liczników wydajności podczas testu obciążenia. Ikony w **liczniki** panelu komunikacji naruszenia progu. Ikona będzie jedną z następujących czynności:

 Ikona będzie jedną z następujących czynności:

 ![Nie naruszenie progu](../test/media/icon_ltest_1.gif) Nie naruszenie progu.

 ![Naruszenie progu krytycznego wynoszącego w ostatnim interwale](../test/media/icon_ltest_2.gif) Naruszenie progu krytycznego podczas ostatniego interwału.

 ![Naruszenie progu krytycznego dla poprzedniego interwału](../test/media/icon_ltest_3.gif) Naruszenie progu krytycznego podczas poprzedniego interwału.

 ![Naruszenie progu ostrzegawczego w ostatnim interwale](../test/media/icon_ltest_4.gif) Naruszenie progu ostrzegawczego podczas ostatniego interwału.

 ![Naruszenie progu ostrzegawczego dla poprzedniego interwału](../test/media/icon_ltest_5.gif) Naruszenie progu ostrzegawczego podczas poprzedniego interwału.

 Opcjonalnie naruszenia progu można wyświetlić na wykresie również. Ikona próg pojawia się na wykresie obok punkt danych, w którym wystąpiło naruszenie progu.

 W drzewie licznika ikonę naruszenie progu są propagowane w węźle określonego licznika do węzła głównego. To powiadamia o naruszenie na licznika, który może nie być widoczne w drzewie ponieważ drzewa nie została rozszerzona.

 Aby uzyskać więcej informacji, zobacz [za pomocą panelu liczników w widoku wykresów i tabel widoku](../test/counters-panel-in-load-test-analyzer.md).

## <a name="view-threshold-violations-on-the-graph"></a>Naruszenia progu widoku na wykresie

 Naruszenia progu można wyświetlić na wykresie. Podobnie jak **liczniki** panelu ikony komunikacji naruszenia progowe na wykresie. Ikony są wyświetlane na wykresie obok punkt danych, w którym wystąpiło naruszenie progu. Jeśli występuje naruszenie progu w licznika, który nie jest wyświetlane na wykresie, można dodać go do wykresu przeciągając je z **liczniki** panelu do wykresu.

 Aby uzyskać więcej informacji, zobacz [z wynikami testów obciążenia analizowanie w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Zobacz także

- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)