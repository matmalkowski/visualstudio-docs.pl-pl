---
title: Konfigurowanie ustawień testu obciążenia w programie Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 70998285b5f1702be45cc1a5d31a976fa8c48ce8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="configure-load-test-run-settings"></a>Konfigurowanie ustawień testu obciążenia

*Ustawienia uruchomienia* to zbiór właściwości wpływające na uruchomień testów obciążenia. Parametry uruchomieniowe są pogrupowane według kategorii w oknie właściwości.

Może mieć więcej niż jedno ustawienie uruchamiania w teście obciążenia, ale tylko jeden z parametrów uruchomieniowych może być aktywny na przebieg. Pozostałe parametry uruchomieniowe oferują szybki sposób wyboru alternatywnego ustawienia do kolejnych przebiegów testowych.

Ustawienia uruchamiania wstępnego jest tworzony podczas tworzenia testu obciążenia za pomocą **załadować Test Kreatora nowego**.

![Parametry uruchomieniowe testu obciążenia](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-----------|-----------------------|
|**Dodaj ustawienia więcej uruchomienia testu obciążenia:** oraz ustawienie uruchamiania jest tworzony w momencie uruchomienia załadować Test Kreator nowego, można dodać więcej uruchomić ustawień testu obciążenia, co umożliwia uruchamianie testów w różnych warunkach.|-   [Porady: Dodawanie dodatkowych ustawień dla testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Określ aktywny uruchomieniowego do użycia z testu obciążenia:** można wybrać ustawienie uruchamiania, które mają być używane dla testu obciążenia za pomocą edytora testu obciążenia. Aktywny parametr jest identyfikowany za pomocą przyrostka „[Aktywny]”.|-   [Porady: Wybieranie ustawień aktywnych dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Edytuj uruchomienie ustawienie właściwości:** można edytować użytkownika Uruchom ustawienie właściwości czynności, takich jak opcje rejestrowania (Zobacz więcej poniżej), określania długość testu, czas trwania nagrzewania, maksymalna liczba błędów podać szczegóły, częstotliwość próbkowania połączenia Model (tylko testy wydajności sieci Web), typ magazynu wyników, poziom sprawdzania poprawności i śledzenia SQL. Parametry uruchomieniowe powinny odzwierciedlać cele testu obciążeniowego.|-   [Właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md)<br />-   [Zmiana ustawień właściwości](../test/load-test-run-settings-properties.md#LoadTestRunSettingsHowToChange)|
|**Określanie liczby iteracji testu w ustawieniach testu obciążenia:** można określić liczbę razy, aby uruchomić wszystkie testy wydajności i jednostki sieci Web we wszystkich scenariuszach testów obciążenia przez skonfigurowanie **iteracje testu** Właściwość.|-   [Porady: Określanie liczby iteracji testowych w ustawieniach testu](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Określ częstotliwość próbkowania dla ustawień testu obciążenia:** można określić, jak często mają obciążenia testowania wydajności zbierania danych licznika konfigurując **częstotliwość próbkowania** właściwości.|-   [Porady: określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Określ opcję magazynowania szczegółów chronometrażu:** można określić sposób szczegółów testu obciążenia zapisywane przez skonfigurowanie **magazynowania szczegółów chronometrażu** właściwości.|-   [Porady: Określanie właściwości magazynowania szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Określ czas przechowywania zasobów testu:** przyspieszenia testu > Usuń > Sprawdź jeszcze raz cykl, zachowując zasoby testów w określonym przedziale przez ustawienie **czas zachowania zasobów** właściwości.|-   [Zachowania zasobów w celu przyspieszenia testów obciążenia](https://www.visualstudio.com/docs/test/performance-testing/getting-started/getting-started-with-performance-testing#retain-resources)|
|**Użyj parametrów kontekstu:** parametrów kontekstu umożliwia parametryzacja ciąg. Na przykład jeśli test obciążeniowy zawiera testy wydajności sieci Web, które używają parametryzowanego serwera sieci Web, można dodać parametr kontekstu do parametrów uruchomieniowych, które są mapowane na inny serwer.|-   [Porady: Dodawanie parametrów kontekstu do ustawień](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Konfigurowanie właściwości rejestrowania testu:** można skonfigurować, jak często dane są zapisywane w dzienniku, który jest skojarzony z załadować ustawień testu. Może to być ważne, gdy uruchamiasz duży lub złożony test obciążeniowy, ponieważ dziennik może mieć wielkość kilku gigabajtów.<br /><br /> Można także skonfigurować plik dziennika, aby automatycznie zapisywał informacje o testach obciążeniowych, które zakończyły się niepowodzeniem, aby pomóc w debugowaniu i analizowaniu aplikacji.|-   [Modyfikowanie ustawień logowania dla testu obciążenia](../test/modify-load-test-logging-settings.md)|