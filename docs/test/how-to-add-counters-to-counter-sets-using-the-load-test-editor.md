---
title: Dodawanie liczników do zestawów liczników dla obciążenia testowania w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 871ba69d088e58ac1d662f254c72c406c79f86fd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31967888"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Porady: dodawanie liczników do zestawów liczników za pomocą edytora testu obciążenia

Podczas tworzenia testu obciążenia z wykorzystaniem **Kreator testu obciążenia**, Dodaj początkowego zestawu liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji o sposobie używania maszyny zdalnej w teście obciążenia sieci, zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).


 Zarządzanie liczniki w **edytora testu obciążenia**. Zestawy liczników, które już są dodawane do testu są widoczne w **ustawia licznik** węzła testu obciążenia. Po utworzeniu testu obciążenia, można dodać nowe liczniki do istniejących zestawów liczników.

## <a name="to-add-counters-to-a-counter-set"></a>Aby dodać liczniki do zestawu liczników

1.  Otwórz testu obciążenia.

2.  Rozwiń węzeł **zbiorów liczników** węzła. Wszystkie zbiory liczników, które zostały dodane do testu obciążeniowego są widoczne.

    > [!NOTE]
    > Drzewo hierarchia test obciążenia zawiera także **parametrów uruchomieniowych** węzła. Ten węzeł zawiera **mapowaniach zbioru liczników** węzła, który zawiera wszystkie komputery i zbiory liczników, które są mapowane na tych komputerach.

3.  Kliknij prawym przyciskiem myszy istniejący zestaw liczników, a następnie wybierz pozycję **Dodaj liczniki**.

     **Wybierz liczniki wydajności** zostanie wyświetlone okno dialogowe.

4.  W **komputera** rozwijane kombi wpisz nazwę komputera, aby mapować do. Alternatywnie wybierz jeden z komputerów na liście rozwijanej.

    > [!NOTE]
    > Ponieważ zbiorów liczników muszą być zamapowane na komputerze przed zbierane są dane dotyczące wydajności, należy określić komputer, na którym mają być zbierane dane dotyczące wydajności.

5.  Wybierz **kategorii wydajności** do filtrowania kategorii liczników wydajności, dane. Zostanie wyświetlone dwie kolumny danych, z którego ma zostać Wybierz liczniki wydajności.

    > [!NOTE]
    > Niektóre kategorii licznika wymaga także wybrać wystąpienia. Na przykład wybierz licznik SQL, muszą wybranie wystąpienie serwera SQL, ponieważ może istnieć więcej niż jedno wystąpienie programu SQL Server zainstalowana na komputerze docelowym.

6.  Wybierz licznik i wystąpienie do dodania do zestawu liczników niestandardowych.

     \- lub -

     Wybierz **wszystkie liczniki** przycisk radiowy, aby wybrać wszystkie dostępne liczniki.

7.  Wybierz **OK**.

    > [!NOTE]
    > Istnieje również możliwość Dodawanie liczników do licznika, ustawione przez prawo Wybieranie istniejącej licznika lub kategorii licznika, wybierając kopiowania, i wklejając je do różnych licznika Ustaw węzła. Dodatkowe liczniki, które są kopiowane, ale nie jest to konieczne, mogą zostać usunięte.

## <a name="see-also"></a>Zobacz także

- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)