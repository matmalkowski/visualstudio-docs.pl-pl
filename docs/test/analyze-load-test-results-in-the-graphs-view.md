---
title: Analizowanie wyników testów obciążenia w widoku wykresu analizatora testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graph.view
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, graphs in Load Test Viewer
- Load Test Viewer, graphs
- load tests, results graphs
- load tests, using graphs
- load test results, graphs
ms.assetid: 4a919cd8-541c-40ee-be3b-352fabc56140
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9aca0c3c17c64ccbc90550305e8f9673de388d98
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36234465"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Analizowanie wyników testów obciążenia w widoku wykresu analizatora testu obciążenia

Wyniki testu obciążenia są wyświetlane jako dane w kilku różnych okienek.

Aby wyświetlić wyniki testów jako wykresy, wybierz **wykresy** na **testu obciążenia** paska narzędzi. Każdy wykres poszczególnych są wyświetlane w panelu nazwy wykresu wyświetlany u góry na liście rozwijanej. Aby wyświetlić innego wykresu, w panelu, wybierz nazwę innego wykresu, z listy.

Maksymalnie cztery wykres panele mogą być wyświetlane w czasie. Można przełączać się między układów różnych panelu przy użyciu **Układ panelu** przycisku paska narzędzi.

Podano kilka wbudowanych wykresy. Można użyć wbudowanej wykresy, ponieważ jest lub dostosować je. Ponadto można tworzyć własne wykresy. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) i [porady: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md).

## <a name="built-in-graphs"></a>Wykresy wbudowane

W poniższej tabeli przedstawiono wbudowane wykresy, które są dostępne do analizowania wyników testów obciążenia.

|Nazwa wykresu|Opis|
|----------------|-----------------|
|Kluczowych wskaźników|Liczniki, które opisują podstawowe aspektów testowanie wydajności, takie jak czas ładowania, przepływności i odpowiedzi użytkownika.|
|Czas odpowiedzi testu|Dane dotyczące ilości czasu testy wykonać, aby uruchomić.|
|Czas odpowiedzi strony|Średni czas odpowiedzi dla stron sieci Web, które są dostępne podczas testu obciążenia.|
|System w ramach testu|Informacje o komputerach, na których aplikacja testowane działa. Dotyczy to również dane dotyczące użycia pamięci, procesora, dysku fizycznego, procesów.<br /><br /> Domyślnie są zbierane tylko liczniki dostępna pamięć (MB) i czasu procesora.|
|Kontroler i agenty|Informacje o komputerach, na których Uruchamianie testów obciążenia. Dotyczy to również dane dotyczące użycia pamięci, procesora, dysku fizycznego, procesów.<br /><br /> Domyślnie tylko dostępna pamięć (MB) i są zbierane przez liczniki czas procesora.|
|Czas odpowiedzi transakcji|Średni czas odpowiedzi transakcji występujących podczas testu obciążenia.|

 W czasie wykonywania i po wykonaniu testu, można wyświetlić różnych liczniki na wykresie.

> [!NOTE]
> Tylko liczniki wydajności czasu odpowiedzi można dodać do wykresu czasu odpowiedzi wygenerowanej automatycznie.

 Informacje o liczniku wyświetla zarówno na wykresie, jak i w legendzie poniżej wykresy. Możesz również powiększać w sekcji wykresu. Aby uzyskać więcej informacji, zobacz [porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>Liczniki wyświetlane na wykresach

 Wykres wyświetlania *liczniki*. Liczniki odwoływać się do danych użytkownika zebranych podczas testu obciążenia, takich jak testów na czas testu drugi lub średnia. Aby uzyskać więcej informacji na temat liczników, zobacz [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

 Legenda liczniki, które są wyświetlane na wykresach zawiera kilka kolumn przydatne dane dotyczące uruchomienia testu obciążenia. Aby wyłączyć funkcję wyświetlania wszystkich danych na wykresie, wyczyść pole wyboru w wierszu w legendzie.

 Legenda zawiera następujące kolumny:

|Licznik|Nazwa licznika|
|-------------|-----------------------------|
|Wystąpienie|Nazwa wystąpienia licznika.|
|Kategoria|Nazwa kategorii licznika.|
|Komputer|Nazwa komputera, do którego są zbierane licznika.|
|Kolor|Kolor linii na wykresie.|
|Zakres|Wskazuje liczbę, która jest reprezentowana przez 100 na wykresie dla tego licznika. Na przykład dla zakresu, w których górna wartość wynosi 10 000, 100 etykiety w górnej części wykresu reprezentuje 10 000.|
|Min|Wskazuje wartość minimalną dla licznika (w milisekundach).|
|Maksymalna|Wskazuje wartość maksymalną dla licznika (w milisekundach).|
|Śr.|Wskazuje średnia wartość licznika w milisekundach.|
|ostatni|Pokazuje wartość licznika podczas ostatniego interwału próbkowania w milisekundach.|

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone — tematy|
|-----------|-----------------------|
|**Dostosowywanie wykresów za pomocą legendy:** widoku wykresu legendy Wyświetla informacje dla każdego licznika wydajności, który jest skojarzony z wykresu. Legenda służy do usuwania liczników wydajności, zaznacz liczników wydajności na wykresie i Dostosuj opcje kreślenia.|-   [Analizowanie testów obciążenia za pomocą legendy wykresu](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Wyświetlanie liczników na wykresach:** można dodać różne rodzaje danych do testu obciążenia powoduje wykres przez umieszczenie liczniki na wykresie.|-   [Porady: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Powiększ na wykresach:** po zakończeniu testu obciążenia umożliwia paski powiększenia powiększanie i przewijanie do obszaru wykresu. Powiększając należy zbadać danych, który został wygenerowany podczas testu obciążenia szczegółowo bardziej precyzyjną.|-   [Porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Wykresy kafelkowe:** można rozmieścić wykresy wyników testu obciążenia w jednym z kilku wzorców. Można podzielić maksymalnie cztery wykresy.||
|**Modyfikowanie wyglądu wykresów liczników wydajności na wykresach:** kreślenia opcje linii dla liczników wydajności na wykresach można zmienić. W tym styl linii. Ponadto można określić, czy chcesz automatycznie lub ręcznie określ zakres, który ma być używany do kreślenia licznika wydajności.|-   [Porady: Określ opcje dla liczników sporządzających wykresy kreślenia](../test/how-to-specify-plot-options-for-graphing-counters.md)|
|**Tworzenie wykresów niestandardowych:** można projektować wykresy zawierające szczegółowe informacje na temat wyników testu obciążenia. Projektowanie wykres niestandardowe, określając liczniki testu obciążenia, które służy do wyświetlenia wykresu.|-   [Porady: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Eksportuj dane liczników wydajności na wykresie:** można wyeksportować dane wykresu do programu Microsoft Excel za pomocą **Eksportuj dane wykresu do programu Excel** znajdującego się na **analizatora testu obciążenia** narzędzi podczas w **wykresy** widoku.||

## <a name="related-tasks"></a>Zadania powiązane

 [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

 [Porady: dostęp do wyników testu obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md)

 [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Zobacz także

- [Porady: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Porady: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)