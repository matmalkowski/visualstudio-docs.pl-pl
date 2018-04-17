---
title: Przeglądanie danych i załączników diagnostycznych dla testów obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, data and diagnostics attachments
ms.assetid: 73309bdd-437a-4eb0-88c8-702c3e24b9b0
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 08e4ce09103cd5f06926147ae38b916ae666648b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-view-data-and-diagnostic-attachments-using-the-load-test-analyzer"></a>Porady: przeglądanie danych i załączników diagnostycznych za pomocą analizatora testu obciążenia

Przed uruchomieniem obciążenia test, możesz wybrać ustawienie testu, które określa kart dane diagnostyczne i dane, które chcesz użyć. Po zakończeniu testu obciążenia umożliwia analizatora testu obciążenia przeglądanie szczegółowych informacji o tych kartach dane diagnostyczne i dane podczas analizowania wyników. Aby wyświetlić danych i informacji diagnostycznych karty, wybierz **widoku danych i załączników diagnostycznych** przycisk na pasku narzędzi analizatora testu obciążenia. Na przykład w przypadku testu obciążenia były adapter informacji systemu skonfigurowane ustawienia testu, można wyświetlić informacje o systemie maszyny, która została użyta podczas uruchomienia testu obciążenia.

![Załącznik adaptera danych diagnostycznych w oknie dialogowym Wybieranie](../test/media/load_adapterdialog.png "Load_AdapterDialog")

Innym przykładem jest test obciążenia, który zawiera kartę IntelliTrace w ustawieniach testu. IntelliTrace adapter umożliwia otwarcie strony Podsumowanie funkcji IntelliTrace.

![Podsumowanie funkcji IntelliTrace](../test/media/load_intellitrace.png "Load_IntelliTrace")

Aby uzyskać więcej informacji, zobacz [zbieranie diagnostycznych informacji za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md) i [IntelliTrace zbieranie danych](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).

## <a name="to-view-data-and-diagnostic-attachments-in-a-load-test-from-the-load-test-analyzer"></a>Aby wyświetlić dane i załączniki diagnostyczne w teście obciążenia z analizatora testu obciążenia

1.  Po zakończeniu testu obciążenia lub po otwarciu wyniku testu obciążenia, załadować Test analizatora na pasku narzędzi wybierz opcję **widoku danych i załączników diagnostycznych**.

     **Wybierz adaptera danych diagnostycznych** zostanie wyświetlone okno dialogowe.

2.  Wybierz załącznik adaptera danych diagnostycznych, który chcesz przeanalizować, a następnie wybierz pozycję **OK**.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)