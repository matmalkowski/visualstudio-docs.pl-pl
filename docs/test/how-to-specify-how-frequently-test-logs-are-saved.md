---
title: Trwa zapisywanie testu obciążeniowego dzienniki w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 9ac88d8a-4777-462c-aa0e-244dadb2cfd1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3464ffc1db1a757ac20e3f77d0d901ec731a7cab
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381937"
---
# <a name="how-to-specify-how-frequently-test-logs-are-saved-using-the-load-test-editor"></a>Porady: Określanie, jak często zapisywane są dzienniki testów za pomocą edytora testu obciążenia

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** do zmiany obciążenia sprawdza właściwości w celu spełnienia potrzeb i celów testowania. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md).

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

Możesz określić jak często jest zapisać dziennik testu w teście obciążeniowym w przy użyciu **edytora testu obciążenia** zmienić **Zapisz częstotliwość zapisów w dzienniku dla testów zakończone** właściwości w **właściwości** okna.

## <a name="to-specify-the-frequency-for-saving-the-test-log-in-a-load-test"></a>Aby określić częstotliwość zapisywania dziennika testu w teście obciążeniowym

1.  Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawia się. Wyświetla drzewo testu obciążenia.

2.  Obciążenia test drzewa **parametrów uruchomieniowych** folderu, wybierz węzeł uruchomieniowy, który chcesz określić jak często, że dziennik testu są zapisywane dla.

3.  Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w **właściwości** okna.

4.  W polu tekstowym dla **Zapisz częstotliwość zapisów w dzienniku dla testów zakończone** właściwości, wpisz liczbę określającą częstotliwość, z jaką będą zapisywane w dzienniku testu. Liczba wskazuje, że jeden z każdym podanej liczby testów zostaną zapisane w dzienniku testu. Na przykład wprowadzenie wartości dziesięciu Określa, że dziesiątym dniu, dwadzieścia, trzydziestą i tak dalej będą zapisywane w dzienniku testu.

    > [!NOTE]
    > Przy użyciu wartości 0 dla **Zapisz częstotliwość zapisów w dzienniku dla testów zakończone** właściwość określa, że żadnych dzienników testu są zapisywane.

5.  Po zakończeniu, zmiana wartości właściwości, wybierz **Zapisz** na **pliku** menu.

     Dane, które są zapisywane w dzienniku można wyświetlać przy użyciu widoku tabeli analizatora testu obciążenia. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
- [Porady: Określanie, czy niepowodzenia testu są zapisywane do testowania dzienników](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)
- [Porady: Konfigurowanie zbierania szczegółowych, aby włączyć wykres aktywności wirtualnych użytkowników](../test/how-to-configure-load-tests-to-collect-full-details.md)