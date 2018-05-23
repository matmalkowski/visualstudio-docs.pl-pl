---
title: Konfigurowanie iteracji testowych dla obciążenia testowania w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, sceanrios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 13d86d64d16fad085983fc45863fa81e88ea2ada
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Konfigurowanie iteracji testowych w scenariuszu testu obciążenia

Aby skonfigurować ustawienia iteracji testu, należy edytować scenariusza testu obciążenia za pomocą edytora testu obciążenia i w oknie właściwości. Domyślnie scenariusza testu obciążenia jest skonfigurowany bez określania maksymalnej liczby iteracji testu. Istnieje możliwość konfigurowania maksymalna liczba iteracji w scenariuszu i jak długo, aby wstrzymać między nimi.

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Określ maksymalnej liczby iteracji testu dla scenariusza

Można określić maksymalną liczbę razy ma testów do uruchomienia dla scenariusza za pomocą edytora testu obciążenia, aby zmienić **maksymalna liczba iteracji testu** właściwości w oknie właściwości.

**Maksymalna liczba iteracji testu** właściwość kontroluje maksymalną liczbę iteracji testu do uruchamiania dla tego scenariusza. Podobnie jak w przypadku **iteracje testu** parametrów uruchomieniowych właściwości w teście obciążenia, nie jest to maksymalna dla wszystkich użytkowników na wszystkich agentów na ustawienia użytkownika.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia i ich opisy, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

 W przypadku sekwencyjnych testu mieszanego iteracji jednego jest jeden przekazywania wszystkich testów w zestawie. Dla wszystkich innych mieszanki testów Każde wykonanie testu jest traktowana jako iteracji. Aby uzyskać więcej informacji, zobacz [o różnych kontroli](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

 Jeśli test obciążenia opartego na czas trwania testu obciążenia, a czas trwania wygasa przed zakończeniem liczby iteracji, zatrzyma się nadal testu. Jeśli test jest oparta na protokole iteracji i iteracjami testu są spełnione przed iteracji scenariusz, test zostanie zatrzymane. Czas trwania jest konfigurowana przy użyciu **Uruchom czas trwania** właściwości w oknie właściwości skojarzone z ustawień w teście obciążenia.

 Po spełnieniu liczby iteracji scenariusz scenariusza przestanie działać, ale innych scenariuszy aktywnej będzie kontynuował działanie.

> [!NOTE]
> Właściwość powiązane jest **Unique** właściwości źródła danych testu sieci Web, które przenosi sekwencyjnie przez dane, wiersz po wierszu, ale tylko jeden raz dla każdego rekordu. Aby uzyskać więcej informacji, zobacz [Dodawanie źródła danych do testu wydajności sieci web](../test/add-a-data-source-to-a-web-performance-test.md).

 **Maksymalna liczba iteracji testu** właściwość jest przydatna w różnych sytuacjach. Niektóre testerów obciążenia wolą należy przeprowadzić na podstawie iteracji test, podczas gdy inne obciążenia testerów wolą należy przeprowadzić test na podstawie czasu trwania.

 ![Określanie iteracji testowych w scenariuszu](../test/media/loadtest_prop.png "LoadTest_Prop")

### <a name="to-specify-the-maximum-test-iterations"></a>Aby określić maksymalnej liczby iteracji testu

1. Otwórz testu obciążenia.

2. Zostanie wyświetlone edytora testu obciążenia. Zostanie wyświetlone drzewo testu obciążenia.

3. Obciążenia test drzew **scenariusze** folderu, wybierz węzeł scenariusz, dla którego chcesz określić maksymalną liczbę iteracji testowych.

4. Na **widoku** menu, wybierz opcję **okna właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie właściwości.

5. W polu tekstowym dla **maksymalna liczba iteracji testu** właściwości, wpisz wartość, która wskazuje maksymalną liczbę testów do uruchomienia dla tego scenariusza, po uruchomieniu testu obciążenia.

    > [!NOTE]
    > Przy użyciu wartości 0 dla **maksymalna liczba iteracji testu** właściwość określa nie maksymalna liczba iteracji.

6. Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia przy użyciu nowej **maksymalna liczba iteracji testu** wartość.

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Określ czasów reakcji pomiędzy iteracjami testu dla scenariusza

**Wziąć pod uwagę czas między iteracje testu** właściwość jest ustawiona, używając okna właściwości podczas edytowania właściwości scenariusza testów obciążenia w edytorze testu obciążenia.

**Wziąć pod uwagę czas między iteracje testu** właściwość jest używana, aby określić liczbę sekund oczekiwania przed rozpoczęciem iteracji testu.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia i ich opisy, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>Aby określić czas namysłu pomiędzy iteracjami testu

1. Otwórz testu obciążenia.

     **Edytora testu obciążenia** pojawi się. Zostanie wyświetlone drzewo testu obciążenia.

2. Obciążenia test drzew **scenariusze** folderu, wybierz węzeł scenariusza, aby określić czas reakcji.

3. Na **widoku** menu, wybierz opcję **okna właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w oknie właściwości.

4. Wartości **wziąć pod uwagę czas między iteracje testu** właściwości, wprowadź liczbę reprezentującą liczbę sekund oczekiwania przed rozpoczęciem następnej iteracji testu.

5. Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia przy użyciu nowego **wziąć pod uwagę czas między iteracje testu** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Konfigurowanie agentów testowych i testowanie kontrolerów testów obciążenia](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)
- [Edytowanie czasów reakcji w celu symulowania opóźnienia człowieka witryny sieci Web](../test/edit-think-times-in-load-test-scenarios.md)