---
title: Ustawia licznik testu obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: b2ff43592819e5834f1e5f7b5088c00f61d8b1c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Porady: zarządzanie zbiorami liczników za pomocą edytora testu obciążenia

Podczas tworzenia testu obciążenia z wykorzystaniem **załadować Test Kreatora nowego**, Dodaj początkowego zestawu liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego.

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji o sposobie używania maszyny zdalnej w teście obciążenia sieci, zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

Zarządzanie zbiorami liczników obejmuje wybranie zestaw komputerów, które mają być zbierane dane dotyczące wydajności z i przypisywanie zestaw zbiorów liczników, które mają być zbierane z każdego komputera. Zarządzanie liczniki w **edytora testu obciążenia**.

![Zarządzanie zbiorami liczników](../test/media/loadtestmanagecountersets.png "LoadTestManageCounterSets")

## <a name="to-manage-counter-sets"></a>Aby zarządzanie zbiorami liczników

1.  Otwórz testu obciążenia.

2.  Wybierz **Zarządzaj zbiorami liczników** przycisku.

     — lub —

     Kliknij prawym przyciskiem myszy **zbiorów liczników** folderu w obciążenia testowanie drzewa i wybierz **Zarządzaj zbiorami liczników**.

     **Zarządzaj zbiorami liczników** zostanie wyświetlone okno dialogowe.

3.  (Opcjonalnie) W **wybrane komputery i zbiory liczników zostaną dodane następujące parametry uruchomieniowe** pola listy, wybierz inne ustawienie uruchamiania.

    > [!NOTE]
    > Dotyczy to tylko, jeśli masz więcej niż jedno ustawienie uruchamiania w teście obciążenia sieci.

4.  (Opcjonalnie) Wybierz **Dodaj komputer** Aby dodać nowy komputer do monitorowania. Pojawi się monit o podanie nazwy. Wpisz nazwę komputera, i zobaczysz węzłów poniżej nowy wpis. Na przykład **ASP.NET**, **IIS**, **SQL**i inne. Zaznacz pola wyboru przed węzły, które chcesz wybrać. Nowe liczniki są wyświetlane w **Podgląd opcji** okienka.

5.  (Opcjonalnie) W **tagów** polu tekstowym, wpisz tag do skojarzenia z komputera. Na przykład "TestMachine12 w lab3".

     Tagów pozwalają na identyfikację za pomocą łatwy do rozpoznania nazwy komputera.

     Znaczniki są wyświetlane w **mapowaniach zbioru liczników** węzeł w drzewie w edytorze testu obciążenia. Większe znaczenie znaczniki są wyświetlane w raportach programu Excel, które pomagają zidentyfikować uczestników jaką rolę komputer ma w teście obciążenia. Na przykład "Web serwer1 w lab2" lub "Serwer2 SQL w pakiecie office Phoenix". Aby uzyskać więcej informacji, zobacz [raportowanie wyników testów obciążenia do potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md).

6.  Wybierz **OK**.

## <a name="see-also"></a>Zobacz także

- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)