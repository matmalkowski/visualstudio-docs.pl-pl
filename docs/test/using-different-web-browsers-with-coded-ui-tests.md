---
title: "Przy użyciu różnych przeglądarek sieci Web z kodowanych testów interfejsu użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: ca381d794569ebae4da2d46225d800dbfe4cf480
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>Korzystanie z różnych przeglądarek sieci Web do przeprowadzania kodowanych testów interfejsu użytkownika
Zakodowane testy interfejsu użytkownika mogą zautomatyzować testowanie aplikacji sieci Web przez rejestrowanie testów przy użyciu przeglądarki Internet Explorer. Następnie można dostosować swoje badania i odtwarzać je za pomocą Internet Explorer lub innego typu przeglądarki dla tych aplikacji sieci Web.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
-   Systemy operacyjne:  
  
    -   Microsoft Windows 7  
  
    -   System Microsoft Windows 8  
  
    -   Microsoft Windows Server 2008 R2 SP1  
  
-   Wersje przeglądarki sieci Web:  
  
    -   Windows Internet Explorer 9  
  
    -   Program Windows Internet Explorer 10  
  
    -   Obsługiwane wersje Mozilla Firefox i Google Chrome, przejdź [tutaj](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)  
  
-   Zainstaluj [składników Selenium kodowanego interfejsu użytkownika dla wielu przeglądarki testowania](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
 **Co to jest obsługiwana przez wszystkie przeglądarki sieci web?**  
  
-   [Dodaj niestandardowy kod kontrolowanie funkcji](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) takich jak elementy właściwości wyszukiwania i odtwarzania.  
  
-   Wyskakujące okienka i okna dialogowe  
  
-   [Wykonywanie podstawowych JavaScript bez zwracanego typu](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)  
  
-   Wyszukiwanie odporności (przy użyciu inteligentne zgodne) i [ulepszenia wydajności](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)  
  
## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Dlaczego należy używać zakodowanych testów interfejsu użytkownika w kilku przeglądarkach sieci Web?  
 Testując aplikację sieci Web za pomocą przeglądarek sieci Web różnego typu, można lepiej emulować doświadczenia z interfejsem użytkowników korzystających z różnych przeglądarek. Na przykład aplikacja może zawierać formant lub kod w Internet Explorer, który nie jest zgodny z innymi przeglądarkami sieci Web. Uruchamianie kodowanych testów interfejsu użytkownika w różnych przeglądarkach pozwoli wykryć i naprawić wszelkie problemy, zanim wpłyną one na doświadczenia klientów.  
  
## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Jak nagrywać i odtwarzać kodowane testy interfejsu użytkownika w aplikacjach sieci Web przy użyciu obsługiwanych przeglądarek sieci Web?  
 **Rejestrowanie:** Aby zarejestrować testu aplikacji sieci web przy użyciu programu Internet Explorer, należy użyć konstruktora kodowanego interfejsu użytkownika testu. Można opcjonalnie dodać sprawdzanie poprawności i niestandardowy kod dla formantów testowanych przy użyciu wstępnie zdefiniowanego zestawu właściwości, jak zwykle w przypadku kodowanych testów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Użyj interfejsu użytkownika do testów Your kodu automatyzacji](../test/use-ui-automation-to-test-your-code.md).  
  
> [!NOTE]
>  Nie można zarejestrować zakodowanych testów interfejsu użytkownika przy użyciu przeglądarek Google Chrome i Mozilla Firefox.  
  
 **Odtwarzanie z programem Internet Explorer:** gdy przeglądarka nie jest jawnie określony, domyślnie testy zostaną uruchomione w programie Internet Explorer. Można jawnie określać przeglądarki, które mają być używane przez ustawienie **BrowserWindow.CurrentBrowser** właściwości w kodzie testu. Dla programu Internet Explorer, ta właściwość powinna być równa **IE** lub **programu Internet Explorer**.  
  
 **Odtwarzanie z przeglądarki sieci web z systemem innym niż Internet Explorer:** odtwarzać w przeglądarkach sieci web z systemem innym niż Internet Explorer, zmień właściwość BrowserWindow.CurrentBrowser kod testu w jednej **Firefox** lub **Chrome** .  
  
 Aby odtworzyć testy w przeglądarkach sieci web-IE, należy zainstalować **składników Selenium kodowanego interfejsu użytkownika dla wielu przeglądarki testowania**.  
  
#### <a name="installing-selenium-components"></a>Instalowanie składników środowiska Selenium  
  
1.  Na **narzędzia** menu, wybierz **rozszerzenia i aktualizacje**.  
  
2.  W oknie dialogowym rozszerzenia i aktualizacje, wyszukaj `Selenium components for Cross Browser Testing`.  
  
3.  Zaznacz rozszerzenie, a następnie wybierz pozycję **Pobierz**.  
  
    > [!TIP]
    >  Możesz również pobrać składników Selenium kodowanego interfejsu użytkownika dla wielu przeglądarki testowania z [tutaj](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
 Aby uzyskać więcej informacji na temat tworzenia i używania kodowanego interfejsu użytkownika testy, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
### <a name="enable-debugging"></a>Włączanie debugowania  
 Aby włączyć debugowanie aplikacji sieci Web, należy zastosować następujące opcje konfiguracji:  
  
1.  Włączyć funkcję Tylko mój kod:  
  
    1.  Na **narzędzia** menu, wybierz **opcje** , a następnie wybierz **debugowanie**.  
  
    2.  Wybierz **Włącz opcję tylko mój kod**.  
  
2.  Wyłączyć wyjątki CLR:  
  
    1.  Na **debugowania** menu, wybierz **wyjątki**.  
  
    2.  Dla **wspólnego języka środowiska uruchomieniowego wyjątki**, usuń zaznaczenie pola wyboru **nieobsługiwanych przez użytkownika**.  
  
##  <a name="generate"></a>*Nie widzę opcja zmiany BrowserWindow.CurrentBrowser w kodowanego testu interfejsu użytkownika.*  
 Być może używasz wersji [!INCLUDE[vs2011_first](../test/includes/vs2011_first_md.md)] , który nie obsługuje kodowane testy interfejsu użytkownika przy użyciu różnych przeglądarek sieci web. Aby używać takich kodowane testy interfejsu użytkownika, należy użyć programu Visual Studio Enterprise.  
  
 *Co należy wiedzieć?*  
 **Uwagi**  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnym") Apple Safari przeglądarka sieci web nie jest obsługiwana.  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnym") akcji uruchamiania przeglądarki sieci web musi być częścią kodowanego testu interfejsu użytkownika.  
  
     Jeśli masz już otwartą przeglądarkę sieci Web i chcesz wykonać w niej te czynności, odtwarzanie zakończy się niepowodzeniem, chyba że używasz Internet Explorer. Dlatego najlepiej uwzględniać uruchamianie przeglądarki sieci Web jako część zakodowanych testów interfejsu użytkownika.  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnym") Automatyzowanie określonych w przeglądarce akcji interfejsu użytkownika, takie jak zmaksymalizować, zminimalizować i przywracania nie jest obsługiwana.  
  
 **Porady**  
  
-   ![Porada](../test/media/tip.png "Porada") możesz skonfigurować dane wyjściowe do zrzutów ekranu w dziennikach kodowanego interfejsu użytkownika. Aby to zrobić, należy zmienić kilka ustawień konfiguracji w pliku QTAgent32.exe.config. Domyślnie ten plik jest instalowany w następującej lokalizacji:  
  
     **C:\Program pliki (x86) \Microsoft Visual Studio 11.0\Common7\IDE**  
  
     Ustaw następujące wartości:  
  
    -   `EqtTraceLevel`w `system.diagnostics` sekcji.  
  
    -   `<add name="EqtTraceLevel" value="4" />`  
  
         Ustawiając wartość 3 lub większą, zrzuty ekranu są pobierane dla każdego działania. Gdy wartość jest równa 1 lub 2, zrzuty ekranu są wykonywane tylko w przypadku błędów.  
  
     Aby uzyskać więcej informacji, zobacz [analizowanie kodowanych testów przy użyciu kodowanego interfejsu użytkownika dzienników testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="videos"></a>Wideo  
 [Zarejestruj w przeglądarce IE i odtwarzania wszędzie](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)  
  
 [Autor cross testy przeglądarki z konstruktora kodowanego testu interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)  
  
 [Autor cross testów przeglądarki, za pomocą kodowania zwykły ręcznie bez mapy interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)  
  
 [Krzyżowe przeglądarki testy są wykonywane sekwencyjnie w różnych przeglądarkach](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)  
  
 [Rozwiązywanie problemów z innej przeglądarki niepowodzenia testu](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 2: testy jednostkowe: testowanie wewnątrz](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 5: Automatyzacja testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="faq"></a>Najczęściej zadawane pytania  
 [Kodowanych testów interfejsu użytkownika — często zadawane pytania - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Kodowanych testów interfejsu użytkownika — często zadawane pytania -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [Visual Studio automatyzacji testów UI (w tym kodowanego interfejsu użytkownika)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Analizowanie kodowanych testów interfejsu użytkownika za pomocą dzienników zakodowanych testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
