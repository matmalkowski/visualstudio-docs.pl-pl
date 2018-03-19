---
title: "Limity czasu dla adapterów danych diagnostycznych w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Diagnostic Data Adapter, increasing time-outs
ms.assetid: 39fff4fc-9233-4f67-96ac-e81bbaf7ca82
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 50bdf23e83ca9ef70c40b010050a3e6aba90e0a5
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-prevent-time-outs-for-diagnostic-data-adapters"></a>Porady: zapobieganie limitom czasu dla adapterów danych diagnostycznych

Jeśli używasz adapterów danych diagnostycznych w ustawieniach testu, limit czasu może wystąpić, gdy uruchomienie testu z jednego z następujących powodów:

-   Usługa kontrolera testu nie jest uruchomiona na komputerze kontrolera testów. Może być konieczne ponowne uruchomienie usługi. Aby uzyskać więcej informacji na temat określić kontroler testu i Zarządzanie kontrolerami testów, zobacz [Zarządzanie kontrolerami testów i agentów testu z programem Visual Studio](../test/manage-test-controllers-and-test-agents.md).

-   Jeśli na komputerze zdalnym jest zbieranie danych, Zapora może blokować Microsoft Test Manager. Komputer, na którym działa program Microsoft Test Manager musi akceptować połączenia przychodzące z kontrolera testów. Limit czasu występuje, gdy program Microsoft Test Manager zostanie wyświetlony komunikat z kontrolera, ponieważ jest on zablokowany przez zaporę. Należy sprawdzić ustawienia zapory na komputerze z uruchomionym programem Microsoft Test Manager. Aby uzyskać więcej informacji na temat ustawień zapory, zobacz następujące tematy [witrynę sieci Web](http://go.microsoft.com/fwlink/?LinkId=184980).

-   Kontroler testów nie można rozpoznać nazwę komputera, na którym działa program Microsoft Test Manager. Taka sytuacja może wystąpić, jeśli DNS zawiera nieprawidłowy adres dla tego komputera. Może być konieczne skontaktuj się z administratorem sieci, aby rozwiązać ten problem.

 Po uruchomieniu długi test, który należy zbierać dużą ilość danych, może się okazać, że limit czasu zbierania tych danych. Poniższa procedura służy do rozwiązania tego problemu.

 Aktualizowanie pliku konfiguracji dla programu Microsoft Test Manager lub pliku konfiguracji agenta testowego, który limit czasu może zwiększyć limit czasu.

 Program Microsoft Test Manager plik konfiguracji jest nazywany **mtm.exe.config**. Znajduje się w następującym katalogu: *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

 Aby zaktualizować agenta testowego, należy zaktualizować następujące pliki konfiguracji na komputerze agenta testowego. Wszystkie te pliki znajdują się na komputerze agenta testowego, w tym samym katalogu: *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

-   QTAgent.exe.config

-   QTAgent32.exe.config

-   QTDCAgent.exe.config

-   QTDCAgent32.exe.config

 Jeśli Uruchamianie testów ręcznych i zbierać dane ze środowiska po utworzeniu usterki lub przypadek testowy jest ukończona, wszystkie dane zostały zebrane przez adaptery danych diagnostycznych jest przekazywany do komputera, na którym jest uruchomione testy ręczne. W przypadku zebrania dużych ilości danych lub użytkownik ma powolne połączenie sieciowe, może trwać dłużej niż domyślna wartość 60 sekund. Na przykład skonfigurowanie adaptera IntelliTrace do zbierania zdarzeń funkcji IntelliTrace i informacji o wywołaniach dla wielu procesów transferu tych danych może przekroczyć domyślny limit czasu. Zwiększenie tej wartości, można użyć poniższej procedury można zaktualizować **mtm.exe.config**.

 Jeśli upłynie limit czasu działania Test Runner lub jeśli upłynie limit czasu agenta testowego jest wyświetlany komunikat o błędzie. Komunikat o błędzie dla agenta testowego zawierają informacje o który test agent komputera został przekroczony. Użyj poniższej procedury, aby zaktualizować pliki konfiguracji, w zależności od tego, który użytkownik otrzymał komunikat o błędzie.

## <a name="to-increase-the-time-outs-for-your-diagnostic-data-adapters"></a>Zwiększenie limitów czasu dla karty danych diagnostycznych

1.  Otwórz okno Eksploratora Windows (lub Eksploratora plików).

     Aby to zrobić, kliknij prawym przyciskiem myszy **Start** i wskaż **Eksploruj**.

    > [!NOTE]
    > Może wymagać uprawnienia administracyjne, aby zaktualizować pliku.

2.  Znajdź katalog na komputerze *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* zawierający plik, który należy zaktualizować.

3.  Kliknij prawym przyciskiem myszy plik, a następnie wskaż **Otwórz za pomocą**. Wybierz edytor.

     Plik jest wyświetlany w edytorze. Istnieje wiele ustawień przechowywanych w tym pliku. Większość tych ustawień można zmienić za pomocą programu Microsoft Test Manager. Jednak ustawienia limitu czasu można zmienić ręcznie, zgodnie z opisem w poniższych krokach.

4.  Należy zmodyfikować sekcja Ustawienia wykonywania testu, aby zwiększyć wartości limitów czasu. Ta sekcja ma następujący format:

    ```
    <!-- Begin: Test execution settings -->

        <!-- How long test runner will wait for an event raised to all local data collectors to complete.  Default is 300. -->
        <add key="DataCollectorEventTimeoutInSeconds" value="300"/>

        <!-- How long test runner will wait for test run operations, such as starting or stopping a test run, to complete.  Default is 60. -->
        <add key="RunOperationTimeoutInSeconds" value="60"/>

        <!-- End: Test execution settings -->
    ```

5.  Aby zwiększyć czas oczekiwania przez adaptery danych diagnostycznych dla zdarzeń, które należy wykonać, zwiększ wartość dla klucza **DataCollectorEventTimeoutInSeconds**

6.  W przypadku przekroczenia limitu czasu komunikat o błędzie dla działania Test Runner, należy zwiększyć wartość dla klucza **RunOperationTimeoutInSeconds**.

7.  Aby zwiększyć limit czasu dla transferu danych zebranych usterki lub gdy test kończy się na komputerze, na którym jest uruchomione testy, należy dodać następujące limit czasu na **mtm.exe.config** w sekcji appSettings pliku:

    ```
    <!-- How long test runner waits for data collected by diagnostic data adapters to be transferred to the computer. Default is 60 seconds. -->
    <add key="GetCollectorDataTimeout" value="300"/>
    ```

    > [!NOTE]
    > Jest wartość limitu czasu w sekundach.

8.  Zapisz zmiany wprowadzone do pliku i ponownie uruchom testy, które przekroczyły limit czasu wcześniej.

## <a name="see-also"></a>Zobacz także

- [Zbierz informacje diagnostyczne przy użyciu ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)