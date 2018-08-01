---
title: Limity czasu dla adapterów danych diagnostycznych w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, increasing time-outs
ms.assetid: 39fff4fc-9233-4f67-96ac-e81bbaf7ca82
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8359aa76dc2f62afb63f6a36984492210d9aeeff
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380017"
---
# <a name="how-to-prevent-time-outs-for-diagnostic-data-adapters"></a>Porady: zapobieganie limitom czasu dla adapterów danych diagnostycznych

Jeśli używasz adapterów danych diagnostycznych w ustawieniach testu, limit czasu może wystąpić po uruchomieniu testu z jednego z następujących powodów:

-   Usługa kontrolera testów nie jest uruchomiona na komputerze kontrolera testów. Trzeba będzie ponownie uruchomić usługę. Aby uzyskać więcej informacji na temat sposobu ustalania używanego kontrolera testów i Zarządzaj kontrolerami testów, zobacz [zarządzać kontrolerami testów i agentami testowymi za pomocą programu Visual Studio](../test/manage-test-controllers-and-test-agents.md).

-   Jeśli zbierasz dane na komputerze zdalnym Zapora może blokować program Microsoft Test Manager. Komputera, na którym działa program Microsoft Test Manager musi akceptować połączenia przychodzące z kontrolera testów. Limit czasu upłynie, gdy program Microsoft Test Manager nie komunikat o błędzie z kontrolera, ponieważ jest on zablokowany przez zaporę. Należy sprawdzić ustawienia zapory na komputerze, na którym działa program Microsoft Test Manager.

-   Kontroler testów nie można rozpoznać nazwę komputera, na którym działa program Microsoft Test Manager. Taka sytuacja może wystąpić, jeśli DNS podaje niepoprawny adres dla tego komputera. Trzeba skontaktować się z administratorem sieci, aby rozwiązać ten problem.

Po uruchomieniu długiego testu, który musi zebrać dużą ilość danych, może się okazać, że limit czasu zbierania tych danych. Aby rozwiązać ten problem, można użyć poniższej procedury.

Możesz zwiększyć limit czasu aktualizując plik konfiguracyjny dla programu Microsoft Test Manager lub plik konfiguracyjny dla agenta testowego, dla którego upływa limit.

W programie Microsoft Test Manager plik konfiguracji jest nazywany *mtm.exe.config*. Znajduje się w następującym katalogu: *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

Aby zaktualizować agenta testowego, należy zaktualizować następujące pliki konfiguracji na komputerze agenta testowego. Wszystkie te pliki znajdują się na komputerze agenta testowego, w tym samym katalogu: *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

-   *QTAgent.exe.config*

-   *QTAgent32.exe.config*

-   *QTDCAgent.exe.config*

-   *QTDCAgent32.exe.config*

Jeśli Uruchamianie testów ręcznych i zbierać dane ze środowiska, gdy tworzona jest usterka lub kończony jest przypadek testowy, wszelkie dane, które zostały zebrane przez adaptery danych diagnostycznych jest przekazywana do komputera, na którym jest uruchomione testy ręczne. Jeżeli została zebrana duża danych lub masz powolne połączenie sieciowe, może trwać dłużej niż domyślna wartość 60 sekund. Na przykład jeśli skonfigurowaniu adapter IntelliTrace do zbierania zdarzeń narzędzia IntelliTrace i wywołania informacji dla wielu procesów, przeniesienie tych danych może przekraczać domyślny limit czasu. Aby zwiększyć tę wartość, służy poniższa procedura Aby zaktualizować *mtm.exe.config*.

Jeśli upłynie limit czasu działania Test Runner lub jeśli upłynie limit czasu agenta testowego jest wyświetlany komunikat o błędzie. Komunikat o błędzie dla agenta testowego będzie zawierać informacji dotyczących testu, którego komputera agenta przekroczyło limit czasu. Użyj poniższej procedury można zaktualizować pliki konfiguracyjne, w zależności od komunikatu o błędzie otrzymałeś.

## <a name="to-increase-the-time-outs-for-your-diagnostic-data-adapters"></a>Aby zwiększyć limity czasu dla kart danych diagnostycznych

1.  Otwórz okno Eksploratora Windows (lub Eksploratora plików).

     Aby to zrobić, kliknij prawym przyciskiem myszy **Start** i wskaż **Eksploruj**.

    > [!NOTE]
    > Możesz wymagać uprawnień administracyjnych, aby zaktualizować plik.

2.  Znajdź katalog na komputerze *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* zawierającego plik, który należy zaktualizować.

3.  Kliknij plik prawym przyciskiem myszy i wskaż **Otwórz za pomocą**. Zaznacz Edytor.

     Plik jest wyświetlany w edytorze. Istnieją w tym pliku jest przechowywanych wiele ustawień. Większość z tych ustawień można zmienić za pomocą programu Microsoft Test Manager. Jednak ustawienia limitu czasu można zmienić ręcznie, zgodnie z opisem w poniższych krokach.

4.  Należy zmodyfikować sekcję ustawień wykonywania testu, aby zwiększyć wartości limitu czasu. Ta sekcja ma następujący format:

    ```text
    <!-- Begin: Test execution settings -->

        <!-- How long test runner will wait for an event raised to all local data collectors to complete.  Default is 300. -->
        <add key="DataCollectorEventTimeoutInSeconds" value="300"/>

        <!-- How long test runner will wait for test run operations, such as starting or stopping a test run, to complete.  Default is 60. -->
        <add key="RunOperationTimeoutInSeconds" value="60"/>

        <!-- End: Test execution settings -->
    ```

5.  Aby wydłużyć czas karty danych diagnostycznych czekają na zakończenie zdarzeń, zwiększ wartość dla klucza **DataCollectorEventTimeoutInSeconds**.

6.  Jeśli komunikat o błędzie limitu czasu dla działania narzędzia Test Runner, należy zwiększyć wartość klucza **RunOperationTimeoutInSeconds**.

7.  Aby zwiększyć limit czasu dla przesyłania wszelkich danych zebranych dla błędu lub w przypadku, gdy test kończy się na komputerze, na którym są uruchomione testy, należy dodać następujące limity czasu do *mtm.exe.config* w sekcji appSettings pliku:

    ```text
    <!-- How long test runner waits for data collected by diagnostic data adapters to be transferred to the computer. Default is 60 seconds. -->
    <add key="GetCollectorDataTimeout" value="300"/>
    ```

    > [!NOTE]
    > Wartość limitu czasu jest w ciągu kilku sekund.

8.  Zapisz zmiany wprowadzone do pliku i uruchom ponownie testy, których wcześniej upłynął.

## <a name="see-also"></a>Zobacz także

- [Zbieranie informacji diagnostycznych za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)