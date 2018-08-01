---
title: Wyświetl dane i załączniki danych diagnostycznych dla testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, data and diagnostics attachments
ms.assetid: 73309bdd-437a-4eb0-88c8-702c3e24b9b0
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 228f8306b803fcbd0e83e23e5b8e919dc2116c37
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382467"
---
# <a name="how-to-view-data-and-diagnostic-attachments-using-the-load-test-analyzer"></a>Porady: przeglądanie danych i załączników diagnostycznych za pomocą analizatora testu obciążenia

Przed uruchomieniem Załaduj test, możesz wybrać ustawienia testu, który określa karty dane diagnostyczne i dane, które chcesz użyć. Po zakończeniu testu obciążeniowego, należy użyć **analizatora testu obciążenia** Aby wyświetlić szczegółowe informacje dotyczące karty te dane diagnostyczne i dane podczas analizowania wyników. Aby wyświetlić dane i szczegóły adaptera diagnostycznego, wybierz **Wyświetl dane i załączniki danych diagnostycznych** znajdujący się na **analizatora testu obciążenia** paska narzędzi. Na przykład jeśli test obciążeniowy karty informacje systemu, które są skonfigurowane w ustawieniach testu, możesz wyświetlić informacje o komputerze który został użyty podczas uruchomienia testu obciążenia w systemie.

![Wybieranie okna dialogowego załącznik karty danych diagnostycznych](../test/media/load_adapterdialog.png)

Innym przykładem jest test obciążenia, który zawiera karty IntelliTrace w ustawieniach testu. IntelliTrace adapter umożliwia otwieranie **krótki opis IntelliTrace** strony.

![Podsumowanie funkcji IntelliTrace](../test/media/load_intellitrace.png)

Aby uzyskać więcej informacji, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md) i [danych zbierania IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).

## <a name="to-view-data-and-diagnostic-attachments-in-a-load-test-from-the-load-test-analyzer"></a>Aby wyświetlić dane i załączniki danych diagnostycznych podczas testów obciążenia w analizatorze testu obciążenia

1.  Po zakończeniu testu obciążeniowego lub po otwarciu wyniku testu obciążeniowego w **analizatora testu obciążenia** narzędzi, wybierz **Wyświetl dane i załączniki danych diagnostycznych**.

     **Wybierz adaptera danych diagnostycznych** zostanie wyświetlone okno dialogowe.

2.  Wybierz załącznik adaptera danych diagnostycznych, który chcesz analizować, a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
