---
title: "Zawierają nagrania ekranu i głosu podczas testów przy użyciu ustawień testów w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/03/2016
ms.topic: article
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: ed05f037bbc1450e33a904f1b35a84bfaa6645be
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Porady: uwzględnianie podczas testów nagrań głosu i zawartości ekranu przy użyciu ustawień testów

Z edytora konfiguracji w programie Visual Studio możesz skonfigurować adapter danych diagnostycznych, które rejestruje ekranu i głosu użytkownika, który jest uruchomiony test. Adapter danych diagnostycznych zapisuje nagrania ekranu i głosu sesji pulpitu podczas testu. Nagrania są zapisywane z wynikami testu lub można dołączyć do usterki. Za pomocą rejestrowania innych członków zespołu można wykrywać wady aplikacji, które są trudne do odtworzenia.

> [!WARNING]
> Nagrywanie ekranu i głosu nie obsługują wiele konfiguracji monitora.

Rejestrator ekran i dźwięk można łączyć z testy ręczne lub automatyczne. Na przykład jeśli zdalne uruchamianie kodowanego testu interfejsu użytkownika można zarejestrować pulpitu, aby zobaczyć kodowanego testu interfejsu użytkownika podczas jego wykonywania. Aby uzyskać więcej informacji o sposobie przechwytywania ekranu i zdalnie rejestrowania dźwięku, zobacz [porady: Ustaw zapasowej Your agenta testowego do uruchamiania testów, które interakcji z pulpitem](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Aby skonfigurować ekran i dźwięk rejestrowania dla ustawień testu

1.  Otwórz ustawienia testu, które chcesz skonfigurować do rejestrowania ekranu i głosu. Aby uzyskać więcej informacji, zobacz [zbierania danych diagnostycznych podczas testowania (VSTS)](/vsts/manual-test/collect-diagnostic-data) lub [zbieranie diagnostycznych informacji za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md).

2.  W ustawieniach testu, wybierz **roli** służące do rejestrowania ekranu i głosu.

    > [!NOTE]
    > Testy ręczne i automatyczne testy będzie to komputer, który uruchamia testy.

3.  Wybierz **nagrywanie ekranu i głosu** , a następnie wybierz **Konfiguruj**.

     Konfigurowanie adaptera danych diagnostycznych — zostanie wyświetlone okno dialogowe nagrywanie ekranu i głosu.

     ![Konfiguracja wideo](../test/media/testsettingvideoconfiggdr.png "TestSettingVideoConfigGDR")

4.  (Opcjonalnie) Wybierz **Włącz nagrywanie głosu** do przechwytywania nagranie audio zawartość.

5.  (Opcjonalnie) Zaznacz pole wyboru obok pozycji **Zapisz nagrywanie, jeżeli przypadek testowy jest zaliczony** zapisywania nagrania ekranu i głosu dla obu nie powiodło się i przekazany testy.

    > [!WARNING]
    > W przypadku wybrania **Zapisz nagrywanie, jeżeli przypadek testowy jest zaliczony**, nagrania są przechowywane z wynikami testu, który używa miejsca do magazynowania na serwerze. Można użyć narzędzia czyszczący załącznika testu, aby wyczyścić te załączniki.

6.  W obszarze **jakości nagrywania ekranu**, skonfiguruj następujące opcje listy rozwijanej:

    1.  **Szybkość klatek:** Określ, ile ramek na sekundę, które mają być używane w nagrywanie ekranu i głosu. Wartość domyślna to 4 klatek na sekundę. Można określić wartości od 2 do 20.

    2.  **Szybkość transmisji bitów:** Określ liczbę kilobajtów na sekundę do użycia w nagrywanie ekranu i głosu. Wartość domyślna to 512. Można określić wartości od 512 do 10 000.

    3.  **Quality(1-100):** można określić jakość ekranu i głosu rejestrowanie przez wybieranie zakresu od 1 do 100. Wartość domyślna to 50 (średniej).

7.  Wybierz **OK**. Ustawienia modułu zbierającego diagnostycznymi śledzenia są teraz skonfigurowane i zapisywane do użycia w ustawieniach testu.

    > [!TIP]
    > Można zresetować konfiguracji dla tego adaptera danych diagnostycznych, wybierz **przywrócić konfigurację domyślną** dla programu Visual Studio i **Przywróć ustawienia domyślne** dla programu Microsoft Test Manager.

## <a name="see-also"></a>Zobacz także

- [Zbierane dane diagnostyczne podczas testowania (VSTS)](/vsts/manual-test/collect-diagnostic-data)
- [Zbieranie danych diagnostycznych podczas wykonywania testów ręcznych (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)
- [Zbierz informacje diagnostyczne przy użyciu ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Uruchom testy ręczne (VSTS)](/vsts/manual-test/getting-started/run-manual-tests)