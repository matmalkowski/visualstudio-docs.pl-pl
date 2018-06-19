---
title: Zastosuj rozkład do opóźnienia kroku do testów obciążenia
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
ms.openlocfilehash: 268578638524ab4f5e5db605c3d394d28414547a
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448522"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Porady: Zastosuj rozkład do opóźnienia użytkownika tempie model testu mieszanego kroku

Po utworzeniu testu obciążenia za pomocą **załadować Test Kreatora nowego**, można zmienić właściwości tego scenariusza, aby spełnić potrzeby testowania i cele edytorze testu obciążenia.

**Zastosuj rozkład opóźnienia tempo** właściwości można ustawić za pomocą **właściwości** okna. Właściwości scenariusza testów obciążenia są modyfikowane za pomocą edytora testu obciążenia.

> [!NOTE]
> **Zastosuj rozkład opóźnienia tempo** właściwość ma zastosowanie tylko wtedy, gdy *załadować testu mieszanego* skonfigurowano oparty na tempie użytkownika. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa wirtualnego użytkownika uruchomienia testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Wartość **Zastosuj rozkład opóźnienia tempo** można ustawić na wartość true lub false:

- **Wartość true,**: scenariusz dotyczy statystyczne rozkład normalny opóźnień, które są określone przez wartość **testy na użytkownika na godzinę** kolumny w oknie dialogowym Edytowanie testu mieszanego. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa wirtualnego użytkownika uruchomienia testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Załóżmy na przykład, że masz **testy na użytkownika na godzinę** wartości w oknie dialogowym Edytowanie mieszanki testów w teście ustawioną dwóch użytkowników na godzinę. Jeśli **Zastosuj rozkład opóźnienia tempo** właściwość jest ustawiona na **True**, normalnej dystrybucji statystyczne jest stosowany do czasu oczekiwania między testy. Testy będą nadal działać dwóch testów na godzinę, ale nie będzie zawsze 30 minut opóźnienia między nimi. Pierwszego testu może uruchomić po czterech minut, a drugi test po upływie 45 minut.

- **FALSE**: Uruchom testy w tempie, określony dla wartości w **testy na użytkownika na godzinę** kolumny w **edytowanie mieszanki testów** okno dialogowe. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa wirtualnego użytkownika uruchomienia testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Załóżmy na przykład, że masz **testy na użytkownika na godzinę** wartość w **edytowanie mieszanki testów** okno dialogowe dla testu ustawioną dwóch użytkowników na godzinę. Jeśli **Zastosuj rozkład opóźnienia tempo** właściwość jest ustawiona na **False**, spowoduje nadanie nie swobodę podczas uruchamiania testów. Test zostanie uruchomiony co 30 minut. Dzięki temu wykonanie dwóch testów na godzinę.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Aby określić dystrybucji Zastosuj ustawienia właściwości tempo opóźnienie dla scenariusza

1. Otwórz testu obciążenia.

   **Edytora testu obciążenia** pojawi się. Zostanie wyświetlone drzewo testu obciążenia.

2. W **scenariusze** folderu drzewa testu obciążenia, wybierz węzeł scenariusz chcesz zastosować tempo dystrybucji.

3. Na **widoku** menu, wybierz opcję **okna właściwości**.

   Kategorie i właściwości scenariusza są wyświetlane w **właściwości** okna.

4. Wartości właściwości **Zastosuj rozkład opóźnienia tempo**, wybierz opcję **True** lub **False**.

5. Wybierz **pliku** > **zapisać**. Teraz możesz uruchomić test obciążenia z nowym **Zastosuj rozkład opóźnienia tempo** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)