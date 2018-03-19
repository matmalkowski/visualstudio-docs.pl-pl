---
title: "Emulowanie rzeczywistych wykorzystania witryny sieci Web, obciążenia testowania w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: b5df4fe7db024ea7d958494faf4f332fc1a30db5
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="emulate-expected-real-world-usage-of-a-web-site-or-application-in-a-load-test-using-a-test-mix-models"></a>Emulowanie oczekiwanego wykorzystania witryny sieci Web lub aplikacji w czasie testu obciążenia przy wykorzystaniu mieszanego modelu testu

Załaduj opcje modelowania umożliwia bardziej dokładnie przewidzieć oczekiwane wykorzystanie rzeczywistych witryny sieci Web lub aplikacji, która obciążenia testowania. Należy to zrobić, ponieważ test obciążenia, który nie jest oparty na modelu dokładne obciążenia mogą generować błędne wyniki.

## <a name="test-mix-model-enhancements"></a>Ulepszenia Model mieszanki testów

Za pomocą Kreatora modelu mieszanki testów lub edytorze testu obciążenia, można określić następujące typy testu mieszanego dla scenariusza testu obciążenia. Aby uzyskać więcej informacji, zobacz [zmiana Model testu mieszanego w scenariuszu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Można określić jedną z następujących opcji model testu mieszanego dla danego scenariusza testu obciążenia:

-   **Na podstawie całkowitej liczby testów:** Określa, który test wydajności lub jednostce sieci Web jest uruchamiany, gdy wirtualny użytkownik rozpoczyna iterację testu. Na końcu testu obciążenia liczba uruchomień poszczególnego testu Uruchom dopasowane dystrybucji przypisanych testu. Ten model testu mieszanego należy użyć, jeśli test mieszany oparty jest w procentach transakcji w dzienniku usług IIS lub w danych produkcyjnych. Aby uzyskać więcej informacji, zobacz [procent oparte na uruchomione testy](#BasedOnTestsStarted).

-   **Na podstawie liczby wirtualnych użytkowników:** Określa procent wirtualnych użytkowników, którzy uruchomią poszczególnego testu wydajności lub jednostce sieci Web. W dowolnym momencie w teście obciążenia liczba użytkowników korzystających z poszczególnego testu pasuje przypisanej dystrybucji. Ten model testu mieszanego należy użyć, gdy mieszanki testów oparty jest na procencie użytkowników korzystających z określonego testu. Aby uzyskać więcej informacji, zobacz [wartość procentową na podstawie wirtualnych użytkowników](#PercentageBasedonVirtualUsers).

-   **Oparty na tempie użytkownika:** w trakcie testu obciążenia każdego testu wydajności sieci Web lub testu jednostkowego jest uruchamiany określoną liczbę razy na użytkowników na godzinę. Ten model testu mieszanego należy używać wirtualnych użytkowników, aby uruchomić test na konkretnej stronie, wszędzie w teście obciążenia. Aby uzyskać więcej informacji, zobacz [Pacing testu mieszanego](#PacingTestMix).

    > [!TIP]
    > Kiedy należy wybrać **procent testu mieszanego** i gdy użytkownik wybierze **wartość procentową na podstawie wirtualnych użytkowników**? W przypadku niektórych testów w teście mieszanym ma czasu trwania dłużej niż inne testy, ważne jest różnica między te dwie opcje. W takim przypadku prawdopodobnie należy wybrać **wartość procentową na podstawie wirtualnych użytkowników**. Ten wybór pomaga uniknąć uruchomienie testu, w którym zwiększa prawdopodobieństwo, że zbyt wielu użytkowników będą uruchomione testy długi czas. Jednak jeśli wszystkie testy mają podobne okresów, bezpieczniejsze można **procent testu mieszanego**.

-   **Na podstawie numeru sekwencyjnego:** każdy wirtualny użytkownik uruchamia testy sieci Web wydajności lub jednostki w kolejności, że testy są zdefiniowane w scenariuszu. Wirtualny użytkownik kontynuuje, okrągło testów w następującej kolejności, aż do ukończenia testu obciążenia. Aby uzyskać więcej informacji, zobacz [kolejności](#SequentialOrder).

###  <a name="BasedOnTestsStarted"></a> Procent opartych na rozpoczętych testów
 Dla każdego z testów w zestawie można określić wartość procentową, która określa, jak często testu został wybrany jako następny test do uruchomienia. Na przykład można przypisać do trzech testach następujące wartości procentowe:

-   TestA (50%)

-   TestB (35%)

-   TestC (15%)

 Jeśli to ustawienie umożliwia Następny test, aby uruchomić opiera się na przypisane wartości procentowe. Możesz to zrobić bez biorąc pod uwagę liczbę wirtualnych użytkowników, którzy są aktualnie uruchomione każdego z testów.

###  <a name="PercentageBasedonVirtualUsers"></a> Procent opartych na wirtualnych użytkowników
 Ten model testu mieszanego Określa procent wirtualnych użytkowników, którzy uruchomią poszczególnego testu. Jeśli używasz ten model testu mieszanego Następny test, aby uruchomić opiera się nie tylko od przypisanej wartości procentowych, ale także na procent wirtualnych użytkowników, którzy są aktualnie uruchomione poszczególnego testu. W dowolnym momencie w teście obciążenia liczba użytkowników korzystających z poszczególnego testu pasuje dystrybucji przypisanych możliwie.

###  <a name="PacingTestMix"></a> Tempo mieszanki testów
 Jeśli określisz pacing mieszanki testów, należy ustawić szybkość wykonywania testów dla każdego wirtualnego użytkownika dla każdego z testów w teście mieszanym. Dla każdego z testów ta stawka jest wyrażona jako testy uruchamiane na wirtualnego użytkownika na godzinę. Na przykład można przypisać pacing się testu mieszanego do następujących testów:

-   TestA: 4 testy na użytkownika na godzinę

-   TestB: 2 testy na użytkownika na godzinę

-   TestC: 0,125 testy na użytkownika na godzinę

 Jeśli używasz pacing model mieszanki testów, aparat środowiska uruchomieniowego testu obciążenia gwarantuje rzeczywiste częstotliwość uruchamiania testów jest mniejsza lub równa określonej wartości. Jeśli testy są uruchamiane zbyt długo dla numeru przypisanego należy wykonać, jest zwracany błąd.

 **Wziąć pod uwagę czas między iteracje testu** ustawienie nie ma zastosowania, gdy używasz pacing testu mieszanego.

#### <a name="applying-distribution-to-pacing-delay"></a>Stosowanie rozkład do opóźnienia kroku
 Wartość **Zastosuj rozkład opóźnienia tempo** właściwość w scenariuszu testu obciążenia można ustawić na wartość true lub false:

-   **Wartość true,**: Scenariusz zastosuje opóźnienia typowej dystrybucji statystyczne określonym przez wartość w **testy na użytkownika na godzinę** kolumny w oknie dialogowym Edytowanie mieszanki testów. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa wirtualnego użytkownika uruchomienia testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Załóżmy na przykład, że masz **testy na użytkownika na godzinę** wartość edytowanie testu mieszanego okna dialogowego dla testu ustawioną 2 użytkowników na godzinę. Jeśli **Zastosuj rozkład opóźnienia tempo** właściwość jest ustawiona na **True**, typowe dystrybucji statystyczne jest stosowany do czasu oczekiwania między testy. Testy będą nadal działać 2 testy na godzinę, ale nie będzie zawsze 30 minut między nimi. Pierwszego testu może uruchomić po 4 minut, a drugi test po upływie 45 minut.

-   **FALSE**: testy zostaną uruchomione w określonym tempie, określony dla wartości w **testy na użytkownika na godzinę** kolumny w oknie dialogowym Edytowanie mieszanki testów. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa wirtualnego użytkownika uruchomienia testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Załóżmy na przykład, że masz **testy na użytkownika na godzinę** wartość edytowanie testu mieszanego okna dialogowego dla testu ustawioną 2 użytkowników na godzinę. Jeśli **Zastosuj rozkład opóźnienia tempo** właściwość jest ustawiona na **False**, zasadniczo nadajesz nie swobodę podczas uruchamiania testów. Test zostanie uruchomiony co 30 minut. Dzięki temu wykonanie 2 testy na godzinę.

 Aby uzyskać więcej informacji, zobacz [porady: dotyczą dystrybucji tempo opóźnienie przy użyciu Model testu mieszanego tempie użytkownika](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

###  <a name="SequentialOrder"></a> Kolejności
 Wybieranie oparty na test sekwencyjnych order — opcja powoduje, że każdego wirtualnego użytkownika Uruchom wszystkie testy w tym scenariuszu w kolejności, że testy zostały zdefiniowane.

## <a name="test-iterations-property"></a>Właściwość iteracji testu
 We właściwościach ustawień można określić wartość dla właściwości iteracjami testu. Ta wartość jest liczby iteracji testowych w teście obciążenia. Po rozpoczęciu określonej liczby iteracji testowych iteracji nie dodatkowy test zostanie uruchomiony niezależnie od ustawienia profilów obciążenia. Po zakończeniu liczba iteracji testu określony kończy się testu obciążenia. Aby uzyskać więcej informacji, zobacz [porady: Określanie liczby iteracji testowych w ustawieniach uruchamiania](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Testy rozpoczęcia i zakończenia
 Możesz wybrać testy do uruchomienia na początku i na końcu sesji testowania obciążenia każdego wirtualnego użytkownika. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa wirtualnego użytkownika uruchomienia testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

-   **Inicjowanie testu**. Ten test jest uruchamiany przez każdego wirtualnego użytkownika przed wykonaniem tych testów w teście mieszanym.

-   **Zakończ test**. Ten test jest uruchamiany po uruchomieniu wszystkich testów dla danego wirtualnego użytkownika.

 Należy pamiętać, następujące kwestie dotyczące test rozpoczęcia i zakończenia testu:

-   Można określić czas trwania testu obciążenia przez czas zamiast według liczby iteracji. W takim przypadku po zakończeniu testu obciążenia. czas trwania testu przerwania nie zostanie uruchomiona.

-   W przypadku test rozpoczęcia testu jednostkowego lub testu wydajności sieci Web, stan obiektu TestContext lub WebTestContext, po zakończeniu testu zainicjować jest zapisywany. Będzie następnie jest używany jako początkowy kontekst dla iteracji testów w teście mieszanym.

-   Nowi użytkownicy, zgodnie z definicją we właściwości scenariusza procent dla nowych użytkowników, zawsze wykonać test rozpoczęcia, co iteracji testu z test mieszany i test zakończenia.

## <a name="see-also"></a>Zobacz także

- [Edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa uruchamiania testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Edytowanie wzorców obciążenia w celu modelowania aktywności wirtualnych użytkowników](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Edytowanie mieszanki testów, aby określić, które testy do scenariusza testów obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)
- [Zmiana Model testu mieszanego w scenariuszu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)