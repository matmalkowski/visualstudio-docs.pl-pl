---
title: Konfigurowanie opóźnień Uruchom scenariusz dla obciążenia testowania w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 519efd059cbac4aca3ea281fe6c4ad042ee1ddea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Konfigurowanie opóźnień uruchamiania scenariuszy w testach obciążenia

Określ opóźnienie przed scenariusz rozpoczyna się w czasie testu obciążenia za pomocą edytora testu obciążenia i w oknie właściwości.

Na przykład możesz chcieć użyć **czas rozpoczęcia opóźnienie** właściwości, jeśli potrzebujesz jeden scenariusz, aby rozpocząć tworzenie elementów, które wykorzystuje inny scenariusz. Można opóźnić odbierającą scenariusza, aby włączyć tworzenie scenariusza, aby wypełnić niektóre dane.

Innym przykładem jest, że może być uruchamiany tylko w określonym czasie dnia scenariusz. Tak użytkownik chce scenariusza, aby symulować to opóźnienie.

## <a name="specifying-the-delay-start-time-of-a-scenario"></a>Godziny rozpoczęcia opóźnienie scenariusza

Można określić opóźnienie przed rozpoczęciem scenariusza w teście obciążenia za pomocą edytora testu obciążenia, zmieniając **czas rozpoczęcia opóźnienie** właściwości w oknie właściwości.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia i ich opisy, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

 Przykład wystąpienia, jeśli chcesz używać **czas rozpoczęcia opóźnienie** gdy właściwość jest potrzebny jeden scenariusz, aby rozpocząć tworzenie elementów, które wykorzystuje inny scenariusz. Można opóźnić odbierającą scenariusza, aby włączyć tworzenie scenariusza, aby wypełnić niektóre dane.

 Innym przykładem jest, że może mieć jeden scenariusz, który jest uruchamiany tylko w określonym czasie dnia. W związku z tym chcesz scenariusza, aby symulować to opóźnienie.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametry uruchomieniowe i ich opisy, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Aby określić czas rozpoczęcia opóźnienie dla scenariusza

1. Otwórz testu obciążenia.

     Zostanie wyświetlone edytora testu obciążenia. Zostanie wyświetlone drzewo testu obciążenia.

2. Obciążenia test drzew **scenariusze** folderu, wybierz węzeł scenariusz, dla którego chcesz określić godzinę rozpoczęcia opóźnienie.

3. Na **widoku** menu, wybierz opcję **okna właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie właściwości.

4. W polu tekstowym dla **czas rozpoczęcia opóźnienie** właściwości, wpisz wartość czasu, która wskazuje czas oczekiwania po testu obciążenia rozpoczyna się przed rozpoczęciem tego scenariusza, po uruchomieniu testu obciążenia.

    > [!NOTE]
    > Jeśli wartość **Wyłącz podczas rozgrzewania** właściwość dla tego scenariusza jest ustawiona na **wartość True,**, a następnie **opóźnienie czas rozpoczęcia** właściwości wartości godziny zostaną zastosowane po rozgrzewania okres. Można kontrolować, jakie scenariusze są objęte rozgrzewania przy użyciu **Wyłącz podczas rozgrzewania** właściwości scenariusza.

5. Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia przy użyciu nowej **czas rozpoczęcia opóźnienie** wartość.

## <a name="enabling-and-disabling-whether-a-scenario-runs-during-the-warm-up-period"></a>Włączanie i wyłączanie czy scenariusza działa w okresie rozgrzewania

**Wyłącz podczas rozgrzewania** właściwość jest ustawiona przy użyciu okna właściwości. Edytowanie właściwości scenariusza testów obciążenia jest ustawiana w edytorze testu obciążenia.

 **Wyłącz podczas rozgrzewania** właściwość jest używana w celu wskazania, czy scenariusza należy uruchomić lub nie działać w okresie rozgrzewania, który jest określony w **czas rozpoczęcia opóźnienie** właściwości. Aby uzyskać więcej informacji, zapoznaj się z poprzedniej procedury [określający czas rozpoczęcia opóźnienie scenariusza](../test/configure-scenario-start-delays.md#ConfiguringScenarioStartDelayHowTo).

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametry uruchomieniowe i ich opisy, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Aby włączyć lub wyłączyć okres rozgrzewania scenariusza

1. Otwórz testu obciążenia.

     **Edytora testu obciążenia** pojawi się. Zostanie wyświetlone drzewo testu obciążenia.

2. Obciążenia test drzew **scenariusze** folderu, wybierz węzeł scenariusz, który ma zostać określony agentów do użytku.

3. Na **widoku** menu, wybierz opcję **okna właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w oknie właściwości.

     W **Wyłącz podczas rozgrzewania** właściwości, wybierz opcję **True** lub **wartość False.**

4. Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia przy użyciu nowego **Wyłącz podczas rozgrzewania** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Konfigurowanie agentów testowych i testowanie kontrolerów testów obciążenia](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)