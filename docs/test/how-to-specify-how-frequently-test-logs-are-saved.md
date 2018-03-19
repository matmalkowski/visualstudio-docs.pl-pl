---
title: "Rejestruje zapisywanie testu obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 9ac88d8a-4777-462c-aa0e-244dadb2cfd1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 0178be52299183a072532d62f323a4612a93f531
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-how-frequently-test-logs-are-saved-using-the-load-test-editor"></a>Porady: określanie, jak często za pomocą edytora testu obciążenia zapisywane są dzienniki testów

Po utworzeniu testu obciążenia z **załadować Test Kreatora nowego**, można użyć **edytorze testu obciążenia** Zmień obciążenia testów właściwości, aby spełnić potrzeby testowania i cele. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md).

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametry uruchomieniowe i ich opisy, zobacz [właściwości ustawień uruchamiania testu obciążenia](../test/load-test-run-settings-properties.md).

Można określić, jak często czy Dziennik testu jest zapisywane w teście obciążenia za pomocą edytora testu obciążenia, zmieniając **Zapisz częstotliwość zapisów w dzienniku dla testów zakończona** właściwości w oknie właściwości.

## <a name="to-specify-the-frequency-for-saving-the-test-log-in-a-load-test"></a>Określenie częstotliwości, aby zapisać dziennik testu w teście obciążenia

1.  Otwórz testu obciążenia.

     Zostanie wyświetlone edytora testu obciążenia. Wyświetla drzewa testu obciążenia.

2.  Obciążenia test drzew **parametrów uruchomieniowych** folderu, wybierz węzeł uruchomieniowy, który chcesz określić, jak często zapisania Dziennik testu dla.

3.  Na **widoku** menu, wybierz opcję **okna właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w oknie właściwości.

4.  W polu tekstowym dla **Zapisz częstotliwość zapisów w dzienniku dla testów zakończona** właściwości, wpisz liczbę, aby wskazać częstotliwość, z jaką będą zapisywane w dzienniku testu. Liczba wskazuje, że jeden poza co podana liczba testów zostanie zapisany dziennik testu. Na przykład wprowadzenie wartości 10 określa, czy dziesiątym dniu, dwadzieścia, trzydziestą i tak dalej będą zapisywane w dzienniku testu.

    > [!NOTE]
    > Przy użyciu wartości 0 dla **Zapisz częstotliwość zapisów w dzienniku dla testów zakończona** właściwość określa, że żadnych dzienników testu są zapisywane.

5.  Po zmianie właściwości, wybierz **zapisać** na **pliku** menu.

     Dane, które są zapisywane w dzienniku można wyświetlić przy użyciu widoku tabeli analizatora testu obciążenia. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Wskazówki: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md)
- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Porady: Określanie, czy niepowodzenia testu są zapisywane w dziennikach testów](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)
- [Porady: Konfigurowanie zbierania szczegółowych, aby włączyć wykres aktywności użytkownika wirtualnego](../test/how-to-configure-load-tests-to-collect-full-details.md)