---
title: Ustawienia rejestrowania w programie Visual Studio Test obciążeniowy
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
ms.openlocfilehash: 61b67cb950ee1d429f5f65ef745ff5ac75ca69d8
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379660"
---
# <a name="modify-load-test-logging-settings"></a>Modyfikowanie ustawień rejestrowania testu obciążeniowego

Wynik testu obciążenia dla ukończonego testu obciążenia zawiera próbki liczników wydajności i informacje o błędach, które zostały zebrane w dzienniku okresowo z komputerów objętych testami. Duża liczba próbek liczników wydajności może być zbierana w trakcie przebiegu testu obciążeniowego. Dane wydajności, które są zbierane zależy od długości przebiegu, interwał próbkowania, liczby komputerów w ramach testu i liczbę liczników do zbierania. Na dużym teście obciążenia ilość zebranych danych wydajności może łatwo wynieść kilka gigabajtów; w związku z tym, należy rozważyć zmodyfikowanie jak często dane są zapisywane w dzienniku. Zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

*Kontrolera testów* buforuje wszystkie zebrane obciążenia testu przykładowe dane do dziennika bazy danych, gdy uruchomiony jest test. Dodatkowe dane, takie jak szczegółowych informacji o czasie i szczegóły błędu są ładowane do bazy danych, po zakończeniu testu.

|Zadanie|Skojarzone tematy|
|----------|-----------------------|
|**Określ, jak często zapisać dzienniki podczas przebiegu testu obciążeniowego:** można określić, jak często mają Dziennik testu, zapisane po uruchomieniu testu obciążenia.|-   [Porady: Określanie, jak często zapisywane są dzienniki testów](../test/how-to-specify-how-frequently-test-logs-are-saved.md)|
|**Zapisywanie dzienników, w przypadku niepowodzenia testu obciążeniowego:** można określić, jeśli chcesz zapisać dziennik testu, zawsze wtedy, gdy test obciążenia kończy się niepowodzeniem.|-   [Porady: Określanie, czy niepowodzenia testu są zapisywane do testowania dzienników](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Ustaw maksymalny rozmiar pliku dla pliku dziennika:** można edytować plik konfiguracji XML, który jest skojarzony z usługi kontrolera testów, aby określić maksymalny rozmiar pliku chcesz użyć dla pliku dziennika.|[Porady: określanie maksymalnego rozmiaru pliku dziennika](../test/how-to-specify-the-maximum-size-for-the-log-file.md)|

## <a name="related-tasks"></a>Informacje o zadaniach pokrewnych

Powiązane właściwości **przechowywanie informacji**. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie zbierania szczegółowych, aby włączyć wykres aktywności wirtualnych użytkowników](../test/how-to-configure-load-tests-to-collect-full-details.md).

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)