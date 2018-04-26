---
title: Licznik i zestawów reguł Próg obciążenia testowania w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- load tests, thresholds
- counter sets
- load tests, performance
- load tests, counter sets
- load tests, threshold rules
ms.assetid: 9e14d955-f3a4-4717-bbfe-7f08cdda5678
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 13fcfac02761a8661195f6f888a9280b468e5de3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia

Testy obciążenia udostępniają zbiorów liczników o nazwie, które są przydatne podczas analizowania danych licznika wydajności. Zestawy liczników są zorganizowane według technologii i obejmują aplikacji, ASP.NET, .NET aplikacji, usług IIS i SQL. Podczas tworzenia testu obciążenia za pomocą **załadować Test Kreatora nowego**, Dodaj początkowego zestawu liczników. Te oferują zestaw zestawy wstępnie zdefiniowanych i ważnych liczników podczas testu obciążenia. Zarządzanie liczniki w **edytora testu obciążenia**.

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji o sposobie używania maszyny zdalnej w teście obciążenia sieci, zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

Zestawy liczników zostały opracowane na komputerach, można określić. Skojarzenie między zbiór liczników i komputer, który jest używany podczas testu obciążenia jest *mapy zestaw liczników*. Na przykład podczas testowania serwera sieci Web może mieć ASP.NET, usług IIS, a mapowanie zestawu liczników aplikacji .NET.

Domyślnie liczniki wydajności są zbierane na kontroler i agenty. Aby uzyskać więcej informacji, zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

Należy dodać do listy komputerów, na którym mają być zbierane liczniki serwerów w ramach testu. Następnie wszelkie dane systemowe są zbierane i monitorowane w czasie testu obciążenia.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-----------|-----------------------|
|**Zarządzanie zbiorami liczników podczas testu obciążenia:** po utworzeniu testu obciążenia można edytować zestaw liczników w edytorze testu obciążenia. Zarządzanie zbiorami liczników obejmuje wybranie zestaw komputerów, z których chcesz zbierać dane dotyczące wydajności i przypisywanie zestaw zbiorów liczników, które mają być zbierane z każdego komputera. Możesz zarządzać liczniki w edytorze testu obciążenia.|-   [Porady: Zarządzanie zbiorami liczników](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Dodaj ustawia licznik do testów obciążenia:** podczas tworzenia testu obciążenia przy użyciu nowego załadować Test kreatora, Dodaj początkowego zestawu liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego. Po utworzeniu testu obciążenia, można dodać nowe liczniki do istniejących zestawów liczników za pomocą edytora testu obciążenia.|-   [Porady: Dodawanie liczników do zestawów liczników](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Porady: Dodawanie zbiorów liczników niestandardowych](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Określ reguły progu za pomocą liczników podczas testu obciążenia:** reguły progu jest regułę, która jest ustawiona na poszczególnych licznika do monitorowania użycia zasobów systemowych podczas testu obciążenia. Definicje zestaw liczników zawiera reguły progu wstępnie zdefiniowanych wiele liczników wydajności. Reguły progu w testach obciążenia porównaj wartość licznika wydajności z wartością stałą lub inną wartość licznika wydajności.|-   [Porady: Dodawanie reguły progu](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Przypisać przyjazne nazwy komputerów, aby licznik, który ustawia są mapowane:** można dodać tagów, które umożliwiają zastosowanie łatwą do rozpoznania nazwę do komputera. Znaczniki są wyświetlane w **mapowaniach zbioru liczników** węzła drzewa w edytorze testu obciążenia. Większe znaczenie, znaczniki są wyświetlane w raportach programu Excel, które pomagają zidentyfikować jaką rolę uczestników komputer ma w teście obciążenia, na przykład "Serwer1 sieci Web w lab2" lub "Serwer2 SQL w pakiecie office Phoenix".<br /><br /> Aby uzyskać więcej informacji, zobacz [raportowanie wyników testów obciążenia do potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md).|-   [Porady: Dodawanie tagów do licznik mapowania zestawów](../test/how-to-add-computer-tags-to-counter-set-mappings-using-the-load-test-editor.md)|

## <a name="use-counter-sets"></a>Użyj zbiorów liczników

Narzędzia testowania obciążenia zbierać i wykres dane dotyczące wydajności przy użyciu liczników w czasie. Dane liczników zbieranych odstępach czasu określonych przez użytkownika podczas testu obciążenia. Aby uzyskać więcej informacji, zobacz [porady: określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Liczniki można wyświetlać w czasie wykonywania, lub można je wyświetlić po testu obciążenia za pomocą *analizatora testu obciążenia*.

Licznik dane są zbierane na serwerze i na dowolnym komputerze, gdy test jest uruchamiany. Jeśli w zestaw komputerów agenta, na której uruchamiać testy, liczniki są również zbierać na tych komputerach.

Istnieją trzy kategorie licznika: wartości procentowych, liczby i średnie. Przykłady to użycie Procesora (%), liczby blokady programu SQL Server i usługi IIS żądań na sekundę.

![Zestawy liczników testu obciążenia](../test/media/loadtestcountersets.png "LoadTestCounterSets")

Dane wydajności dotyczące poszczególnych żądań HTTP został zgłoszony przez komputer z uruchomioną testu. na przykład komputer agenta. Dla żądania może monitorować dane, takie jak Średni czas do pierwszego bajtu, czas odpowiedzi i liczba żądań na sekundę.

Aby ułatwić zbierania danych wydajności na serwerze sieci Web, Visual Studio Enterprise zawiera zestawy wstępnie zdefiniowane, nazwany liczników, oparte na technologii do użycia w testach obciążenia. Te zestawy są przydatne podczas analizowania serwerze, na którym uruchomiono usługi IIS, platformy ASP.NET lub programu SQL Server. Nie podano w domyślny zbiór liczników liczniki można dodać za pomocą edytora testu obciążenia. Należy dodać komputery lub serwery w ramach testu do testów obciążenia, aby upewnić się, że można monitorować wykorzystanie zasobów na tych komputerach. Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie zbiorami liczników](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

Wyniki analizy uruchomień obciążenia często wymaga znajomości specyficznego dla domeny określonego obszaru, aby wiedzieć, jakie dane należy zebrać, gdzie należy reguły progu zestawu i jak sprawdzić, kiedy miary odzwierciedla konkretnego problemu z aplikacją. Aby uzyskać więcej informacji, zobacz [o reguły progu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md#SpecifyingCounterSetsThresholdRulesAboutThresholdRules).

### <a name="performance-counter-sampling-interval-considerations"></a>Zagadnienia dotyczące interwał próbkowania licznika wydajności

Wybierz odpowiednią **częstotliwość próbkowania** właściwości w teście obciążenia Uruchom ustawienia oparte na długość testu obciążenia. Mniejszą częstotliwość próbkowania, np. domyślna wartość pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. Dłużej testów obciążenia zwiększenie częstotliwość próbkowania powoduje zmniejszenie ilości zbieranych danych. Aby uzyskać więcej informacji, zobacz [porady: określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Poniżej przedstawiono wskazówki dotyczące częstotliwości próbkowania.

|Czas trwania testu obciążenia|Częstotliwość próbkowania zalecane|
|------------------------|-----------------------------|
|\< 1 godzina|5 sekund|
|Liczba godzin korzystania z 1−8|15 sekund|
|Liczba godzin korzystania z 8−24|30 sekund|
|> 24 godziny|60 sekund|

## <a name="store-performance-data"></a>Przechowywanie danych wydajności

Podczas testu obciążenia, dane licznika wydajności są zbierane i przechowywane w *repozytorium wyników testów obciążenia*. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyników testów obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>Informacje o regułach próg

A *reguły progu* jest regułę, która jest ustawiona na poszczególnych licznika do monitorowania użycia zasobów systemowych podczas testu obciążenia. Definicje zestaw liczników zawiera reguły progu wstępnie zdefiniowanych wiele liczników wydajności. Aby uzyskać więcej informacji, zobacz [przy użyciu zestawów liczników, aby ułatwić analizowanie danych licznika wydajności w testach obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Reguły progu i poziomy

Po utworzeniu reguły progu w testach obciążenia można wybrać między dwa typy zasad:

Porównanie stałej&mdash;porównanie wartości licznika wydajności z wartością stałą.

Porównanie liczniki&mdash;porównanie wartości licznika wydajności z inną wartość licznika wydajności.

Podczas tworzenia reguły progu, można również ustawić poziomy reguły. Poziomy są progu ostrzeżenia i progu krytycznego. Po wyświetleniu uruchomienia testu obciążenia naruszenia progu poziomu ostrzeżenia są oznaczone symbolem żółty i naruszeń progu krytycznego poziomu są wskazywane przez czerwony symbol.

## <a name="the-alert-if-over-property"></a>Alert, jeśli za pośrednictwem właściwości

Ustaw **alertu Jeśli nad** właściwości **True** do wskazywania powyżej wartości progowej problem. Na przykład, jeśli reguły progu jest ustawiona na **% czasu procesora**, i chcesz otrzymywać alerty, jeśli wartość jest większa niż 90, użyj **porównanie stałej** typ reguły, ustaw **progu krytycznego Wartość** 90 i zestawu **alertu Jeśli nad** do **True**.

Ustaw **alertu Jeśli nad** właściwości **False** do wskazywania poniżej wartości progowej problem. Na przykład, jeśli reguły progu jest ustawiona na **żądań na sekundę**, i chcesz otrzymywać alerty, jeśli wartość jest poniżej 50, użyj **porównanie stałej** typ reguły, ustaw **krytyczna wartość progowa** 50, jak i zestawu **alertu Jeśli nad** do **False**.

## <a name="see-also"></a>Zobacz także

- [Porady: Dodawanie reguły progu](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)