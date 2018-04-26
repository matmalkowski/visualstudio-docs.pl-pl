---
title: Tworzenie raportu wydajności testu obciążenia programu Visual Studio za pomocą programu Microsoft Word
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8d25e93c0c5fefeae2d7891d458373d81d5ff370
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Porady: ręczne tworzenie raportu wydajności testu obciążenia przy użyciu programu Microsoft Word

Można ręcznie utworzyć raportów testu obciążenia w programie Microsoft Word, kopiowanie i wklejanie danych z widoku podsumowania wyników testu obciążenia i widok wykresów. Do danych, które są prezentowane w widoku podsumowania i widoku wykresy jest stosowany format HTML, podczas ich kopiowania.

> [!TIP]
> Zwykły tekst można skopiować z widoku tabel i zrzuty ekranu w widoku szczegółów do programu Microsoft Word, ale nie została zastosowana w formacie HTML i będzie wymagać dodatkowego, formatowanie i edytowania.

> [!TIP]
> Można również tworzyć organizowane raporty programu Microsoft Excel automatycznie. Aby uzyskać więcej informacji, zobacz [porady: tworzenie obciążenia testu wydajności raportów za pomocą programu Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Kopiowanie danych Widok podsumowania

1.  W wynikach testów obciążenia Jeśli widok podsumowania nie jest aktualnie wyświetlany, kliknij przycisk **podsumowania** na pasku narzędzi.

2.  W widoku podsumowania, kliknij prawym przyciskiem myszy i wybierz **Zaznacz wszystko**.

3.  W widoku podsumowania, kliknij prawym przyciskiem myszy i wybierz **kopiowania**. Renderuje to do schowka dane widoku podsumowania w formacie HTML.

4.  W programie Microsoft Word wklej dane widok podsumowania w dowolnym miejscu.

5.  Można teraz modyfikować, formatować i usuwać aspekty kopiowanej zawartości zgodnie z własnymi potrzebami raportowania.

## <a name="copy-graph-view-data"></a>Kopiowanie danych widoku wykresu

1.  W wynikach testów obciążenia, widoku wykresu nie jest wyświetlany, jeśli **wykresy** na pasku narzędzi.

2.  (Opcjonalnie) Powiększ określonych wykresu, który chcesz skopiować do dokumentu programu Microsoft Word, jak pokazano na poniższej ilustracji. Aby uzyskać więcej informacji, zobacz [porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Formant powiększania widoku wykresu](../test/media/ltest_zoomcontrol.png "LTest_ZoomControl")

3.  Na wykresie, który ma zostać skopiowany do dokumentu programu Microsoft Word, kliknij prawym przyciskiem myszy i wybierz **kopiowania**.

4.  W programie Microsoft Word Wklej wykres i skojarzonej tabeli danych w dowolnym miejscu.

    > [!WARNING]
    > Nie można skopiować wykresu z pulpitu zdalnego i wkleić go do innej maszyny, ponieważ zostaną skopiowane jedynie informacje tabeli, która jest skojarzona z wykresem, a nie obraz wykresu. Obraz wykresu jest przechowywany w katalogu tymczasowym na maszynie, z której został skopiowany, a druga maszyna nie może wyłuskać tego katalogu.

## <a name="see-also"></a>Zobacz także

- [Raportowanie wyników testów obciążenia do potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md)
- [Porady: tworzenie raportów wydajności testu obciążenia za pomocą programu Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)