---
title: Ustawienia rejestrowania w programie Visual Studio Test obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ffd20812ec37e324dc919ea5943cf30a5329321b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="modify-load-test-logging-settings"></a>Modyfikowanie ustawień logowania dla testu obciążenia

Wynik testu obciążenia do testu obciążenia ukończone zawiera próbek licznika wydajności i informacje o błędzie, zebrane w dzienniku okresowo komputerów na mocy testu. Duża liczba próbek licznika wydajności mogą być zbierane w trakcie uruchomienia testu obciążenia. Zbierane dane dotyczące wydajności zależy od długości Uruchom, interwał próbkowania, liczbę komputerów w ramach testu i liczbę liczników do zbierania. Dla testów obciążenia duża ilość zbieranych danych wydajności mogą być łatwo kilku gigabajtów; w związku z tym należy rozważyć zmodyfikowanie, jak często dane są zapisywane w dzienniku. Zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

*Kontrolera testów* buforuje wszystkie zebrane obciążenia testu przykładowe dane do dziennika bazy danych, gdy test jest uruchomiony. Dodatkowe dane, takie jak szczegółów chronometrażu i szczegóły błędu, została załadowana do bazy danych po zakończeniu testu.

|Zadanie|Skojarzone — tematy|
|----------|-----------------------|
|**Określ, jak często zapisać dzienników podczas uruchomienia testu obciążenia:** można określić, jak często mają Dziennik testu zapisane po uruchomieniu testu obciążenia.|-   [Porady: Określ, jak często zapisywane są dzienniki testów](../test/how-to-specify-how-frequently-test-logs-are-saved.md)|
|**Zapisać dzienniki w przypadku niepowodzenia testu obciążenia:** można określić, czy chcesz zapisać dziennik testu zawsze, gdy nie powiedzie się w teście obciążenia.|-   [Porady: Określanie, czy niepowodzenia testu są zapisywane w dziennikach testów](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Ustaw maksymalny rozmiar pliku dla pliku dziennika:** można edytować plik konfiguracji XML, który jest skojarzony z usługą kontrolera testów, aby określić maksymalny rozmiar pliku ma być używany dla pliku dziennika.|[Porady: określanie maksymalnego rozmiaru pliku dziennika](../test/how-to-specify-the-maximum-size-for-the-log-file.md)|

## <a name="related-tasks"></a>Tematy pokrewne

Właściwość powiązane jest **szczegółów chronometrażu** magazynu. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie zbierania szczegółowych informacji umożliwiających włączyć wirtualnego wykres aktywności użytkownika](../test/how-to-configure-load-tests-to-collect-full-details.md).

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)