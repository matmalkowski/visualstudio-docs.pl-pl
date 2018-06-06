---
title: Analizowanie kodowanych testów interfejsu użytkownika przy użyciu dzienników testu kodowanego interfejsu użytkownika w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f28ae1e73a22be7e1e9a677df9fb68fc4c954926
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750730"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analiza dzienników zakodowanych testów interfejsu użytkownika

Zakodowanych filtru dzienników testu interfejsu użytkownika i rekord, który uruchamia ważne informacje o kodowanego testu interfejsu użytkownika. Dzienniki są przedstawione w formacie, który umożliwia szybkie debugowanie problemów.

## <a name="step-1-enable-logging"></a>Krok 1: Włączanie rejestrowania

W zależności od scenariusza należy użyć jednej z następujących metod Aby włączyć dziennik:

- Docelowy .NET Framework w wersji 4 bez *App.config* plik istnieje w projekcie testowym:

   1. Otwórz **QTAgent32_40.exe.config** pliku. Domyślnie ten plik znajduje się w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

   2. Zmień wartość dla EqtTraceLevel na poziom dziennika, który ma.

   3. Zapisz plik.

- Docelowy .NET Framework w wersji 4.5 bez *App.config* plik istnieje w projekcie testowym:

   1. Otwórz **QTAgent32.exe.config** pliku. Domyślnie ten plik znajduje się w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

   2. Zmień wartość EqtTraceLevel na poziom dziennika, który ma.

   3. Zapisz plik.

- *App.config* plik znajduje się w projekcie testowym:

    - Otwórz *App.config* pliku w projekcie i Dodaj następujący kod w węźle Konfiguracja:

      ```xml
      <system.diagnostics>
        <switches>
          <add name="EqtTraceLevel" value="4" />
        </switches>
      </system.diagnostics>`
      ```

- Włącz rejestrowanie z kodu testu:

   <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Krok 2: Uruchamianie kodowanego testu interfejsu użytkownika i sprawdź dzienniki

Po uruchomieniu kodowanego testu interfejsu użytkownika ze zmianami do **QTAgent32.exe.config** pliku w miejscu, zobacz dane wyjściowe link w wynikach testów Explorer. Pliki dziennika są produkowane nie tylko w przypadku, gdy test zakończy się niepowodzeniem, ale także dla testów powiodło się, gdy poziom śledzenia jest ustawiona na "pełne."

1.  Na **testu** menu, wybierz **Windows** , a następnie wybierz **Eksploratora testów**.

2.  Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

3.  W Eksploratorze testów, wybierz kodowanego testu interfejsu użytkownika, które chcesz uruchomić, otwórz menu skrótów, a następnie wybierz **Uruchom testy wybierz**.

     Testy automatyczne uruchamianie i wskazują one przekazany lub niepowodzenie.

    > [!TIP]
    > Aby wyświetlić narzędzia Eksplorator testów, wybierz **testu** > **Windows**, a następnie wybierz pozycję **Eksploratora testów**.

4.  Wybierz **dane wyjściowe** łącze w wynikach narzędzia Eksplorator testów.

     ![Dane wyjściowe link w Eksploratora testów](../test/media/cuit_htmlactionlog1.png)

     Zostaną wyświetlone dane wyjściowe dla testu, który zawiera łącze do dziennika akcji.

     ![Wyniki i łącza dane wyjściowe z kodowanego testu interfejsu użytkownika](../test/media/cuit_htmlactionlog2.png)

5.  Wybierz *UITestActionLog.html* łącza.

     Dziennik jest wyświetlany w przeglądarce sieci web.

     ![Plik dziennika w kodowanego testu interfejsu użytkownika](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Porady: Uruchamianie testów za pomocą programu Microsoft Visual Studio](http://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)