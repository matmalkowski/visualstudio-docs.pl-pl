---
title: "Dodawanie tagów do mapowaniach zbioru liczników dla obciążenia testowania w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, counter set mappings, computer tags
ms.assetid: f52a73e1-036a-4b28-a6c8-848284bf4488
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 70f3f2c58974478b17c78c3de4014a1921accd76
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-add-computer-tags-to-counter-set-mappings-using-the-load-test-editor"></a>Porady: dodawanie tagów do mapowania zestawów liczników za pomocą edytora testu obciążenia

Tagów pozwalają na identyfikację za pomocą łatwy do rozpoznania nazwy komputera. Znaczniki są wyświetlane w **mapowaniach zbioru liczników** węzeł w drzewie w edytorze testu obciążenia. Większe znaczenie znaczniki są wyświetlane w raportach programu Excel, które pomagają zidentyfikować uczestników jaką rolę komputer ma w teście obciążenia. Na przykład "Web serwer1 w lab2" lub "Serwer2 SQL w pakiecie office Phoenix". Aby uzyskać więcej informacji, zobacz [raportowanie wyników testów obciążenia do potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md).

## <a name="to-add-a-tag-to-a-computer"></a>Aby dodać tag do komputera

1.  Otwórz testu obciążenia.

2.  Wybierz **Zarządzaj zbiorami liczników** przycisku.

     — lub —

     Kliknij prawym przyciskiem myszy **zbiorów liczników** folderu w obciążenia testowanie drzewa i wybierz **Zarządzaj zbiorami liczników**.

     **Zarządzaj zbiorami liczników** zostanie wyświetlone okno dialogowe.

3.  (Opcjonalnie) W **wybrane komputery i zbiory liczników zostaną dodane następujące parametry uruchomieniowe** pola listy, wybierz inne ustawienie uruchamiania.

    > [!NOTE]
    > Dotyczy to tylko, jeśli masz więcej niż jedno ustawienie uruchamiania w teście obciążenia sieci.

4.  W obszarze **komputera i licznik ustawia do monitorowania**, wybierz komputer, który chcesz zastosować do znacznika.

    > [!NOTE]
    > Aby uzyskać informacje dotyczące sposobu dodawania komputera, zobacz [porady: Zarządzanie zbiorami liczników](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

5.  W **tagów** polu tekstowym, wpisz tag do skojarzenia z komputera. Na przykład "TestMachine12 w lab3".

6.  Wybierz **OK**.

## <a name="see-also"></a>Zobacz także

- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Porady: Zarządzanie zbiorami liczników](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)