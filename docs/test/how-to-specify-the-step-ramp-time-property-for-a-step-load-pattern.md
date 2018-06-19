---
title: Czas do zwiększenia kroku dla wzorca obciążenia krokowego obciążenia testowania w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 20eb70b6c3c6308e41599e65a4b00a3e4043e8d1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973607"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Porady: określanie właściwości czasu narastania kroku dla wzorca obciążenia krokowego

Po utworzeniu testu obciążenia z **załadować Test Kreatora nowego**, można użyć **edytorze testu obciążenia** Aby zmienić właściwości scenariuszy, aby spełnić potrzeby testowania i cele. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md).

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia i ich opisy, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

**Czas do zwiększenia kroku** właściwość jest ustawiona w oknie właściwości. Edytowanie właściwości scenariusza testów obciążenia w edytorze testu obciążenia.

**Czas do zwiększenia kroku** właściwość jest używana tylko z krokowego wzorca obciążenia. Aby uzyskać więcej informacji, zobacz [Edytowanie wzorców obciążenia w celu działania dotyczące modelu wirtualnego użytkownika](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Krokowego wzorca obciążenia jest używany do zwiększa obciążenie serwera lub serwerów uruchomień testów obciążenia, tak aby były widoczne, jak wydajność może być różna miarę wzrostu obciążenia użytkownika. Na przykład aby zobaczyć, jak serwer lub serwery Przeprowadź obciążenie użytkownikami, zwiększając 2000 użytkowników, możesz uruchomić test obciążenia 10 godzin przy użyciu wzorca obciążenia krokowego z następującymi właściwościami:

-   Początkowa liczba użytkowników: 100

-   Maksymalna liczba użytkowników: 2000

-   Czas trwania kroku (w sekundach): 1800

-   Czas (w sekundach) do zwiększenia kroku: 20

-   Liczba użytkowników krok: 100

Te ustawienia mają testu obciążenia uruchomione na 30 minut (1800 sekund) przy obciążeniach użytkownika 100, 200, 300 maksymalnie 2000 użytkowników.

> [!NOTE]
> **Czas do zwiększenia kroku** właściwość jest tylko jeden z tych właściwości, która nie jest dostępna do wyboru w Kreatorze nowego testu obciążenia.

**Czas do zwiększenia kroku** właściwości umożliwia się stopniowego zamiast bezpośredniego wzrostu od jednego kroku do następnego (na przykład od 100 do 200 użytkowników). W tym przykładzie obciążenie użytkownikami zostanie zwiększona od 100 do 200 użytkowników w okresie sekundę 20 (wzrost 5 użytkowników co sekundę).

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Aby edytować właściwości czasu narastania kroku dla wzorca obciążenia krokowego

1.  Otwórz testu obciążenia.

     **Edytora testu obciążenia** pojawi się. Zostanie wyświetlone drzewo testu obciążenia.

2.  Obciążenia test drzew **scenariusze** folder, otwórz węzeł scenariusza, aby określić narastania kroku czasu.

3.  Wybierz **krokowego wzorca obciążenia** węzła.

    > [!NOTE]
    > Wzorzec obciążenia dla scenariusza musi być krokowego wzorca obciążenia. Jeśli nie jest, wzorcu obciążenia jest wyświetlana typ wzorzec obciążenia, który jest aktualnie powiązany z tym scenariuszem. Aby uzyskać więcej informacji, zobacz [Edytowanie wzorców obciążenia w celu działania dotyczące modelu wirtualnego użytkownika](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4.  Na **widoku** menu, wybierz opcję **okna właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w oknie właściwości.

5.  Ustaw wartość **czas do zwiększenia kroku** właściwości wprowadzić liczbę dla sekund wykonywanej w każdym kroku w celu stopniowego dodawania użytkowników określonych przez **liczbę użytkowników** właściwości.

6.  Po zmianie właściwości, wybierz **zapisać** na **pliku** menu. Następnie możesz uruchomić test obciążenia przy użyciu nowego **czas do zwiększenia kroku** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)
- [Edytowanie wzorców obciążenia w celu modelowania aktywności wirtualnych użytkowników](../test/edit-load-patterns-to-model-virtual-user-activities.md)