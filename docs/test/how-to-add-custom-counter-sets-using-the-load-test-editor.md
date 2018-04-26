---
title: Dodawanie zestawów liczników niestandardowych dla obciążenia testowania w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: bd58cc29368ed66d3dd8c35fa4bdf3c87aa6a747
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Porady: dodawanie zestawów liczników niestandardowych za pomocą edytora testu obciążenia

Podczas tworzenia testu obciążenia z wykorzystaniem **załadować Test Kreatora nowego**, Dodaj początkowego zestawu liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego.

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji na temat używania maszyny zdalnej w teście obciążenia sieci, zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

Zarządzanie liczniki w **edytora testu obciążenia**. Zestawy liczników, które już są dodawane do testu są widoczne w **ustawia licznik** węzła testu obciążenia. Po utworzeniu Testu obciążenia, można dodać do niego nowe niestandardowe zbiory liczników.

![Niestandardowy zestaw liczników](../test/media/loadtestcustomcounter.png "LoadTestCustomCounter")

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Aby dodać niestandardowy zbiór liczników do Testu obciążenia

1.  Otwórz testu obciążenia.

2.  Rozwiń węzeł **zbiorów liczników** węzła. Wszystkie zbiory liczników, które zostały dodane do testu obciążeniowego są widoczne.

3.  Kliknij prawym przyciskiem myszy **zbiorów liczników** a następnie wybierz węzeł **dodać zestaw liczników niestandardowych**.

    > [!NOTE]
    > Zbiór liczników podano nazwę domyślną, takich jak **Custom1**. Nazwę można zmienić przy użyciu **właściwości** okna. Naciśnij klawisz F4, aby wyświetlić **właściwości** okna.

4.  Aby dodać liczniki do Twojej liczników niestandardowych ustawić, kliknij prawym przyciskiem myszy nowy zestaw liczników, a następnie wybierz pozycję **Dodaj liczniki**. Aby uzyskać więcej informacji o sposobie dodawania liczników, zobacz [porady: Dodawanie liczników do zestawów liczników](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Istnieje także możliwość dodania niestandardowego zbioru liczników, klikając prawym przyciskiem myszy istniejący zbiór liczników, wybierając kopię i wklejając ją do węzła zbiory liczników. Dodatkowe liczniki, które są kopiowane, ale nie są potrzebne, mogą zostać usunięte. Można zmienić nazwę nowego zestawu przy użyciu liczników **właściwości** okna.

## <a name="see-also"></a>Zobacz także

- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)