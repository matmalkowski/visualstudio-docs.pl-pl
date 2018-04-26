---
title: Zastosuj rozkład do opóźnienia kroku obciążenia testowania w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 25b22ff696fb12e4924587313cde8fe387900fe9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model"></a>Porady: stosowanie opóźnienia między rozpowszechnianiem a tempem podczas stosowania mieszanki testów z uwzględnieniem tempa użytkownika

Po utworzeniu testu obciążenia za pomocą nowego załadować Test kreatora służy edytorze testu obciążenia można zmienić właściwości tego scenariusza, aby spełnić potrzeby testowania i cele.

**Zastosuj rozkład opóźnienia tempo** właściwość jest ustawiona przy użyciu okna właściwości. Właściwości scenariusza testów obciążenia są modyfikowane za pomocą edytora testu obciążenia.

> [!NOTE]
> **Zastosuj rozkład opóźnienia tempo** właściwość ma zastosowanie tylko wtedy, gdy *załadować testu mieszanego* skonfigurowano oparty na tempie użytkownika. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa wirtualnego użytkownika uruchomienia testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Wartość **Zastosuj rozkład opóźnienia tempo** można ustawić na wartość true lub false:

-   **Wartość true,**: Scenariusz zastosuje statystyczne rozkład normalny opóźnień, które są określone przez wartość **testy na użytkownika na godzinę** kolumny w oknie dialogowym Edytowanie mieszanki testów. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa wirtualnego użytkownika uruchomienia testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Załóżmy na przykład, że masz **testy na użytkownika na godzinę** wartości w oknie dialogowym Edytowanie mieszanki testów w teście ustawioną dwóch użytkowników na godzinę. Jeśli **Zastosuj rozkład opóźnienia tempo** właściwość jest ustawiona na **True**, normalnej dystrybucji statystyczne jest stosowany do czasu oczekiwania między testy. Testy będą nadal działać dwóch testów na godzinę, ale nie będzie zawsze 30 minut opóźnienia między nimi. Pierwszego testu może uruchomić po czterech minut, a drugi test po upływie 45 minut.

-   **FALSE**: testy zostaną uruchomione w tempie, określony dla wartości w **testy na użytkownika na godzinę** kolumny w oknie dialogowym Edytowanie testu mieszanego. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa wirtualnego użytkownika uruchomienia testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Załóżmy na przykład, że masz **testy na użytkownika na godzinę** wartości w oknie dialogowym Edytowanie mieszanki testów w teście ustawioną dwóch użytkowników na godzinę. Jeśli **Zastosuj rozkład opóźnienia tempo** właściwość jest ustawiona na **False**, spowoduje nadanie nie swobodę podczas uruchamiania testów. Test zostanie uruchomiony co 30 minut. Dzięki temu wykonanie dwóch testów na godzinę.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Aby określić dystrybucji Zastosuj ustawienia właściwości tempo opóźnienie dla scenariusza

1.  Otwórz testu obciążenia.

     **Edytora testu obciążenia** pojawi się. Zostanie wyświetlone drzewo testu obciążenia.

2.  W **scenariusze** folderu drzewa testu obciążenia, wybierz węzeł scenariusz, dla którego chcesz określić agentów do użytku.

3.  Na **widoku** menu, wybierz opcję **okna właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w **właściwości** okna.

4.  Wartości właściwości **Zastosuj rozkład opóźnienia tempo**, wybierz opcję **True** lub **False**.

5.  Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia przy użyciu nowej **Zastosuj rozkład opóźnienia tempo** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)