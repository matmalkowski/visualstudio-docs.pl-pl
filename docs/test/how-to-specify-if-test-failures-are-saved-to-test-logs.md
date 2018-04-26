---
title: Zapisz dziennik testu obciążenia dla niepowodzenia testu w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e184fbab591698404bde4593f4ad7b61fa1815ae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Porady: określanie, czy niepowodzenia testu są zapisywane w dziennikach testów za pomocą edytora testu obciążenia

Po utworzeniu testu obciążenia z **załadować Test Kreatora nowego**, można użyć **edytorze testu obciążenia** można zmienić właściwości testu obciążenia, aby spełnić potrzeby testowania i cele. Zobacz [wskazówki: tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md). Można określić, jeśli chcesz, aby dziennik testu, jeśli test zakończy się niepowodzeniem w teście obciążenia, zmieniając zapisywane **Zapisz dziennik podczas niepowodzenia testu** właściwości.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametry uruchomieniowe i ich opisy, zobacz [właściwości ustawień uruchamiania testu obciążenia](../test/load-test-run-settings-properties.md).


## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Aby określić, czy Dziennik testu jest zapisywana, gdy test zakończy się niepowodzeniem w przypadku scenariusza

1.  Otwórz testu obciążenia.

     Zostanie wyświetlone edytora testu obciążenia. Zostanie wyświetlone drzewo testu obciążenia.

2.  Obciążenia test drzew **parametrów uruchomieniowych** folderu, wybierz węzeł uruchomieniowych, który chcesz określić maksymalną liczbę iteracji testowych dla.

3.  Na **widoku** menu, wybierz opcję **okna właściwości**.

     Parametry uruchomieniowe kategorii i właściwości są wyświetlane w oknie właściwości.

4.  W **Zapisz dziennik podczas niepowodzenia testu** właściwości, wybierz albo wartość True lub False, aby określić, czy chcesz zapisać testu dziennika w przypadku niepowodzenia testu, w tym scenariuszu.

     Po zmianie właściwości, wybierz **zapisać** na **pliku** menu.

     Dane, które są zapisywane w dzienniku można wyświetlić przy użyciu widoku tabeli analizatora testu obciążenia. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Przewodnik: Tworzenie i uruchamianie testów obciążeniowych](../test/walkthrough-create-and-run-a-load-test.md)
- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Porady: Konfigurowanie zbierania szczegółowych, aby włączyć wykres aktywności użytkownika wirtualnego](../test/how-to-configure-load-tests-to-collect-full-details.md)
- [Porady: Określ, jak często zapisywane są dzienniki testów](../test/how-to-specify-how-frequently-test-logs-are-saved.md)