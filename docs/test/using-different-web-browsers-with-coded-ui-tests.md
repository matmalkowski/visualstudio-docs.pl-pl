---
title: Przy użyciu różnych przeglądarek sieci Web z kodowanych testów interfejsu użytkownika w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fc998fc5065b49ca68f4a46afa1da94cd3d23b07
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36235066"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Korzystanie z różnych przeglądarek internetowych do przeprowadzania kodowanych testów interfejsu użytkownika

Zakodowane testy interfejsu użytkownika mogą zautomatyzować testowanie aplikacji internetowych przez rejestrowanie testów przy użyciu przeglądarki Internet Explorer. Następnie można dostosować swoje badania i odtwarzać je za pomocą Internet Explorer lub innego typu przeglądarki dla tych aplikacji internetowych.

Najpierw zainstaluj [składników Selenium kodowanego interfejsu użytkownika dla wielu przeglądarki testowania](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

## <a name="whats-supported-across-all-web-browsers"></a>Co to jest obsługiwana przez wszystkie przeglądarki sieci web?

-   [Dodaj niestandardowy kod kontrolowanie funkcji](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) takich jak elementy właściwości wyszukiwania i odtwarzania.

-   Wyskakujące okienka i okna dialogowe

-   [Wykonywanie podstawowych JavaScript bez zwracanego typu](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)

-   Wyszukiwanie odporności (przy użyciu inteligentne zgodne) i [ulepszenia wydajności](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Dlaczego należy używać zakodowanych testów interfejsu użytkownika w kilku przeglądarkach sieci Web?

Testując aplikację internetową za pomocą przeglądarek internetowych różnego typu, można lepiej emulować doświadczenia z interfejsem użytkowników korzystających z różnych przeglądarek. Na przykład aplikacja może zawierać formant lub kod w Internet Explorer, który nie jest zgodny z innymi przeglądarkami sieci Web. Uruchamianie kodowanych testów interfejsu użytkownika w różnych przeglądarkach pozwoli wykryć i naprawić wszelkie problemy, zanim wpłyną one na doświadczenia klientów.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Jak nagrywać i odtwarzać kodowane testy interfejsu użytkownika w aplikacjach internetowych przy użyciu obsługiwanych przeglądarek internetowych?

**Rejestrowanie:** Aby zarejestrować testu aplikacji sieci web przy użyciu programu Internet Explorer, należy użyć konstruktora kodowanego interfejsu użytkownika testu. Można opcjonalnie dodać sprawdzanie poprawności i niestandardowy kod dla formantów testowanych przy użyciu wstępnie zdefiniowanego zestawu właściwości, jak zwykle w przypadku kodowanych testów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Użyj interfejsu użytkownika do testów Your kodu automatyzacji](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Nie można zarejestrować zakodowanych testów interfejsu użytkownika przy użyciu przeglądarek Google Chrome i Mozilla Firefox.

 **Odtwarzanie z programem Internet Explorer:** gdy przeglądarka nie jest jawnie określony, domyślnie testy zostaną uruchomione w programie Internet Explorer. Można jawnie określać przeglądarki, które mają być używane przez ustawienie **BrowserWindow.CurrentBrowser** właściwości w kodzie testu. Dla programu Internet Explorer, ta właściwość powinna być równa **IE** lub **programu Internet Explorer**.

 **Odtwarzanie z przeglądarki sieci web z systemem innym niż Internet Explorer:** odtwarzać w przeglądarkach sieci web z systemem innym niż Internet Explorer, zmień właściwość BrowserWindow.CurrentBrowser kod testu w jednej **Firefox** lub **Chrome** .

 Aby odtworzyć testy w przeglądarkach sieci web-IE, należy zainstalować **składników Selenium kodowanego interfejsu użytkownika dla wielu przeglądarki testowania**.

### <a name="install-selenium-components"></a>Zainstaluj składniki Selenium

1.  Na **narzędzia** menu, wybierz **rozszerzenia i aktualizacje**.

2.  W oknie dialogowym rozszerzenia i aktualizacje, wyszukaj `Selenium components for Cross Browser Testing`.

3.  Zaznacz rozszerzenie, a następnie wybierz pozycję **Pobierz**.

    > [!TIP]
    > Możesz również pobrać składników Selenium kodowanego interfejsu użytkownika dla wielu przeglądarki testowania z [tutaj](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

Aby uzyskać więcej informacji na temat tworzenia i używania kodowanego interfejsu użytkownika testy, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md).

### <a name="enable-debugging"></a>Włączanie debugowania

Aby włączyć debugowanie aplikacji internetowej, należy zastosować następujące opcje konfiguracji:

1.  Włączyć funkcję Tylko mój kod:

    1.  Na **narzędzia** menu, wybierz **opcje** , a następnie wybierz **debugowanie**.

    2.  Wybierz **Włącz opcję tylko mój kod**.

2.  Wyłączyć wyjątki CLR:

    1.  Na **debugowania** menu, wybierz **wyjątki**.

    2.  Dla **wspólnego języka środowiska uruchomieniowego wyjątki**, usuń zaznaczenie pola wyboru **nieobsługiwanych przez użytkownika**.

Jeśli nie widzisz opcję, aby zmienić `BrowserWindow.CurrentBrowser` w kodowanego testu interfejsu użytkownika może korzystasz z wersji programu Visual Studio, która nie obsługuje kodowane testy interfejsu użytkownika przy użyciu różnych przeglądarek sieci web. Aby używać takich kodowane testy interfejsu użytkownika, należy użyć programu Visual Studio Enterprise edition.

Poniżej przedstawiono niektóre elementy, których należy wiedzieć:

- Przeglądarka Safari firmy Apple nie jest obsługiwana.

- Akcja uruchomienia przeglądarki sieci Web musi być częścią kodowanego testu interfejsu użytkownika.

   Jeśli masz już otwartą przeglądarkę sieci Web i chcesz wykonać w niej te czynności, odtwarzanie zakończy się niepowodzeniem, chyba że używasz Internet Explorer. Dlatego najlepiej uwzględniać uruchamianie przeglądarki sieci Web jako część zakodowanych testów interfejsu użytkownika.

- Automatyzacja funkcjonowania przeglądarki na podstawie działań interfejsu użytkownika, takich jak maksymalizowanie, minimalizowanie i przywracanie, nie jest obsługiwana.

## <a name="tips"></a>Porady

Można skonfigurować dane wyjściowe do uwzględnienia zrzutów ekranu w zakodowanych dziennikach interfejsu użytkownika. Aby to zrobić, należy ustawić niektóre ustawienia konfiguracji *QTAgent32.exe.config* pliku. Domyślnie ten plik jest instalowany w następującej lokalizacji:

*% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Ustaw następujące wartości:

- `EqtTraceLevel` w `system.diagnostics` sekcji.

- `<add name="EqtTraceLevel" value="4" />`

   Ustawiając wartość 3 lub nowszej, zrzuty ekranu są pobierane dla każdego działania. Gdy wartość jest równa 1 lub 2, zrzuty ekranu są wykonywane tylko w przypadku błędów.

Aby uzyskać więcej informacji, zobacz [analizowanie kodowanych testów przy użyciu kodowanego interfejsu użytkownika dzienników testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Zasoby wideo

 [Zarejestruj w przeglądarce IE i odtwarzania wszędzie](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

 [Autor cross testy przeglądarki z konstruktora kodowanego testu interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

 [Autor cross testów przeglądarki, za pomocą kodowania zwykły ręcznie bez mapy interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

 [Krzyżowe przeglądarki testy są wykonywane sekwencyjnie w różnych przeglądarkach](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

 [Rozwiązywanie problemów z innej przeglądarki niepowodzenia testu](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Analizowanie kodowanych testów interfejsu użytkownika za pomocą dzienników zakodowanych testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
