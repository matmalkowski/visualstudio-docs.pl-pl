---
title: Określanie agentów testowych do użycia w scenariuszach testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: a4aacbd31516e6a3e55f1b543a3cc8f49ea6ce4d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31968498"
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Porady: określanie agentów testowych stosowanych w scenariuszach testów obciążenia

Po utworzeniu testu obciążenia za pomocą **załadować Test Kreatora nowego**, można użyć **edytorze testu obciążenia** Aby zmienić właściwości scenariuszy, aby spełnić potrzeby testowania i cele.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia i ich opisy, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

Agenci są określone za pomocą edytora testu obciążenia, aby zmienić **agentów** właściwości w oknie właściwości.

Można określić agenci, którzy mają scenariusz do użycia, jeśli używasz kontrolerów i agentów do uruchomienia obciążenia testowania zdalnie. Na przykład można określić konkretny zestaw agentów, aby zachować spójność podczas analizowania trendów wydajności. Ponadto agentów mogą być rozproszone geograficznie, tak, aby koligacja istnieje między które skrypty zakres ich działania i w którym znajduje się agent.

> [!TIP]
> Zamiast fizycznie umieszczanie agenta w lokacji zdalnej, inną opcją jest użycie emulacji sieci emulować wolną sieć. Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md) i [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Aby uzyskać więcej informacji, zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

Jest to kolejny powód, że niektóre, ale nie wszystkich agentów może być oprogramowania na nich zainstalowany, które jest wymagane dla danego scenariusza.

Można kontrolować wybór agenta dla danego testu przy użyciu ról w ustawieniach testu. Aby uzyskać więcej informacji, zobacz [zbieranie diagnostycznych informacji za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md).

Jeżeli maszynie agenta testowego ma więcej niż 75 procent wykorzystania procesora CPU lub ma mniej niż 10 procent dostępnej pamięci fizycznej dodać więcej agentów do testów obciążenia, aby upewnić się, że komputer agenta nie zostanie wąskich gardeł w teście obciążenia sieci.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Aby określić agentów na potrzeby scenariusza

1.  Otwórz testu obciążenia.

     Zostanie wyświetlone edytora testu obciążenia. Zostanie wyświetlone drzewo testu obciążenia.

2.  Obciążenia test drzew **scenariusze** folderu, wybierz węzeł scenariusz, dla którego chcesz określić agentów do użytku.

3.  Na **widoku** menu, wybierz opcję **okna właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie właściwości.

4.  W polu tekstowym dla **agentów** właściwości, wpisz listę agentów, na których scenariusz może zostać uruchomiony.

     Agenci muszą być oddzielone przecinkami, na przykład "**Agent3 Agent1, Agent2,**". Niewypełnienie tej właściwości oznacza, że scenariusz powinien wykorzystywać wszystkich dostępnych agentów.

    > [!NOTE]
    > **Agentów** właściwość jest ignorowana dla przebiegów lokalnych. Dla przebiegów zdalnych, jeśli żadna z agentów określone w **agentów** istnieje, nie zostaną uruchomione testy w scenariuszu.

5.  Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia przy użyciu nowej **agentów** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)