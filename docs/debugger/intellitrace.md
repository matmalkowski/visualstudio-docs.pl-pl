---
title: IntelliTrace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c5812f73d86bd585cb24f2e8d599c82d2d6e7ab
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478951"
---
# <a name="intellitrace"></a>IntelliTrace

Można poświęcają mniej czasu, debugowania aplikacji, korzystając z funkcji IntelliTrace do rejestrowania i śledzenia historii wykonywania kodu. Błędy można znaleźć łatwe, ponieważ umożliwia IntelliTrace:

- Rejestruje określone zdarzenia

     Zbadanie kodu powiązanego, dane wyświetlane przez **zmiennych lokalnych** okno podczas zdarzenia debugera i informacji o wywołania funkcji

- Debugowanie błędów, które są trudne do odtworzenia lub zachodzące we wdrożeniu

Można użyć funkcji IntelliTrace w Visual Studio Enterprise edition (ale nie wersji Professional lub społeczności).

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

|||
|-|-|
|**Debugowaniem aplikacji przy użyciu funkcji IntelliTrace:**<br /><br /> — Pokaż poza zdarzenia.<br />— Pokaż mnie informacje ze zdarzeniami poprzednich wywołań.<br />-Zapisz moje sesji funkcji IntelliTrace.<br />-Formant dane, które umożliwia zbieranie danych funkcji IntelliTrace.|- [Wskazówki: Używanie funkcji IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [Funkcje IntelliTrace](../debugger/intellitrace-features.md)<br />- [Debugowanie historyczne](../debugger/historical-debugging.md)<br />- [Migawki widoku przy użyciu zwrotnego krok IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md)|
|**Gromadzenie danych IntelliTrace w trakcie sesji testu w Test Manager**|- [Zbieranie większej ilości danych podczas wykonywania testów ręcznych](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)|
|**Gromadzenie danych IntelliTrace z wdrożonej aplikacji**|- [Za pomocą autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Uruchom profilowanie z plikiem dziennika funkcji IntelliTrace (.iTrace pliku).**|- [Przy użyciu zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)|

## <a name="IntelliTraceSupport"></a> Jakie aplikacje można debugować przy użyciu funkcji IntelliTrace?

|||
|-|-|
|**Obsługiwane**|-Aplikacje Visual Basic i Visual C#, korzystających z programu .NET Framework 2.0 lub nowszych wersjach.<br/>Można debugować większość aplikacji, w tym ASP.NET, Microsoft Azure, formularze systemu Windows, WCF, WPF, przepływu pracy systemu Windows, programu SharePoint 2010, SharePoint 2013 i aplikacje 64-bitowe.<br/>Debugowanie aplikacji SharePoint przy użyciu funkcji IntelliTrace, zobacz [wskazówki: debugowanie aplikacji SharePoint przy użyciu funkcji IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> Aby debugować aplikacje Microsoft Azure przy użyciu funkcji IntelliTrace, zobacz [debugowania usługi chmury opublikowane za pomocą funkcji IntelliTrace i Visual Studio](/azure/vs-azure-tools-intellitrace-debug-published-cloud-services).|
|**Ograniczona obsługa**|-.NET core aplikacji platformy ASP.NET Core w obsługiwane i dla niektórych tylko zdarzenia (zdarzeń kontrolera MVC, ADO.NET i HTTPClicent) debugowania lokalnego. Autonomiczny moduł zbierający nie jest obsługiwana w przypadku aplikacji .NET Core i ASP.NET Core.<br />-Aplikacje F # na zasadach eksperymentalnych<br />-Aplikacje platformy uniwersalnej systemu Windows obsługuje tylko zdarzenia|
|**Nieobsługiwane**|— C++ innych języków i skryptu<br />-Usługi systemu Windows, Silverlight, Xbox, lub [!INCLUDE[winmobile](../debugger/includes/winmobile_md.md)] aplikacji|

> [!NOTE]
> Jeśli chcesz debugować procesu, który jest już uruchomiona, można zebrać tylko zdarzenia IntelliTrace (Brak informacji wywołania). Możesz dołączyć do procesu 32-bitowy lub 64-bitowych tylko na komputerze lokalnym. Nie są zbierane zdarzenia występujące przed dołączeniem do procesu.

##  <a name="IntelliTraceVSTraditional"></a> Dlaczego debugować przy użyciu funkcji IntelliTrace?

Tradycyjny lub *live* debugowania pokazuje tylko aplikacji bieżący stan, z ograniczoną ilość danych o zdarzeniach w przeszłości. Możesz mieć do wywnioskowania tych zdarzeń, w oparciu o bieżący stan aplikacji lub trzeba ponownie utworzyć te zdarzenia przez ponowne uruchomienie aplikacji.

IntelliTrace rozszerza standardowe debugowanie poprzez zapisywanie określonych zdarzeń i danych w konkretnym czasie. Dzięki temu można zobaczyć, co się stało z aplikacji bez ponownego uruchamiania, zwłaszcza, jeśli krok w przeszłości w przypadku błędu. Funkcja IntelliTrace jest domyślnie włączana podczas standardowego debugowania i zbiera dane automatycznie i w sposób niewidoczny. W ten sposób można łatwo przełączać się między standardowym debugowaniem i debugowaniem IntelliTrace, aby wyświetlić zapisane informacje. Zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md) i [, jakie dane zbiera danych funkcji IntelliTrace?](#WhatData)

Funkcja IntelliTrace może również debugować błędy, które są trudne do odtworzenia lub mają miejsce we wdrożeniu. Możesz zbierać dane IntelliTrace i zapisywać je do pliku dziennika IntelliTrace (plik iTrace). Plik iTrace zawiera szczegóły dotyczące wyjątków, zdarzeń dotyczących wydajności, żądań sieci Web, danych testowych, wątków, modułów i innych informacji o systemie. Można otworzyć tego pliku w Visual Studio Enterprise, wybierz element i rozpocząć debugowanie przy użyciu funkcji IntelliTrace. Dzięki temu można przejść do dowolnego zdarzenia w pliku i sprawdzić szczegółowe informacje na temat aplikacji w danym momencie.

Możesz zapisywać dane IntelliTrace z następujących źródeł:

- Sesja IntelliTrace w Visual Studio 2017 Enterprise, Visual Studio 2015 Enterprise lub starszych wersji programu Visual Studio Ultimate.

- Sesję testu w programie Microsoft Test Manager

- Aplikacje ASP.NET sieci Web hostowane w usłudze IIS lub aplikacje SharePoint 2010 i SharePoint 2013 działające we wdrożeniu, gdy używasz programu Microsoft Monitoring Agent samodzielnie lub w połączeniu z programem System Center 2012. Zobacz [używać autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) i [monitorowania za pomocą programu Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).

 Oto kilka przykładów, jak IntelliTrace może pomóc w debugowaniu:

- Aplikacja ma uszkodzony plik danych, ale nie wiadomo, w którym wystąpiło to zdarzenie.

     Bez IntelliTrace musi sprawdzać przez kod, aby znaleźć możliwe pliku, umieścić punkty przerwania w tych dostępie i ponownie uruchom aplikację można znaleźć, w którym wystąpił problem. Przy użyciu funkcji IntelliTrace widać wszystkie zdarzenia zebrane dostęp do plików i szczegółowe informacje na temat aplikacji przy każdym zdarzenie wystąpiło.

- Ma miejsce wyjątek.

     Bez funkcji IntelliTrace pojawi się komunikat o wyjątku, ale nie ma wiele informacji dotyczących zdarzeń, które spowodowało wyjątek. Należy zbadać stos wywołań, aby wyświetlić łańcuch wywołań, które doprowadziły do wyjątek, ale nie widać sekwencję zdarzeń, które wystąpiły podczas wywołań. Z IntelliTrace można sprawdzić zdarzenia, które miały miejsce przed wystąpieniem wyjątku.

- Aplikacja ulegnie awarii na komputerze testowym, ale zostanie pomyślnie uruchomiony na komputerze dewelopera.

     Możesz zbierać dane IntelliTrace z Microsoft Test Manager, zapisać dane w pliku iTrace i dołączyć ten plik do elementu pracy programu Team Foundation Server, aby przeprowadzić późniejszą analizę. Zobacz [zbierać więcej danych diagnostycznych podczas wykonywania testów ręcznych](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests) i [Użyj zapisywane są dane funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md).

- Błąd lub awarii odbywa się we wdrożonej aplikacji.

     Dla opartych na platformie Azure aplikacje firmy Microsoft można skonfigurować zbieranie danych IntelliTrace, przed opublikowaniem aplikacji. Gdy aplikacja działa, IntelliTrace zapisuje dane do pliku .iTrace. Zobacz [debugowania usługi opublikowana chmura za pomocą funkcji IntelliTrace i Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248).

     W przypadku aplikacji ASP.NET sieci Web obsługiwanych przez usługi IIS 7.0, 7.5 i 8.0 oraz aplikacji SharePoint 2010 lub SharePoint 2013 możesz używać programu Microsoft Monitoring Agent, samego lub w połączeniu z System Center 2012, aby zapisywać dane IntelliTrace w pliku iTrace.

     Jest to przydatne, gdy chcesz zdiagnozować problemy z aplikacjami w trakcie wdrażania. Zobacz [używać autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

##  <a name="WhatData"></a> Jakie dane funkcji IntelliTrace zbiera?

**Zbieranie informacji o zdarzeniach**

Domyślnie IntelliTrace rejestruje tylko zdarzenia funkcji IntelliTrace: debuger zdarzenia, wyjątki zdarzenia .NET Framework i innych zdarzeń systemowych, które mogą pomóc Ci z debugowaniem. Możesz wybrać typy zdarzeń IntelliTrace, które mają być zbierane, z wyjątkiem zdarzeń debugera i wyjątków, które są zawsze zbierane. Zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).

- **Zdarzenia debugera**

     IntelliTrace zawsze zapisuje zdarzenia mające miejsce w debugerze Visual Studio. Na przykład uruchamianie aplikacji jest zdarzeń debugera. Innych zdarzeń debugera są zatrzymywanie zdarzenia, które powodują przerwać wykonywanie aplikacji. Na przykład program trafienia punktu przerwania trafienia śledzenia i wykonuje **krok** polecenia.

     Domyślnie ułatwiające wydajności, IntelliTrace nie zapisuje każdej możliwe wartości dla zdarzeń debugera. Zamiast tego zapisuje następujące wartości:

    - Wartości w **zmiennych lokalnych** okna. Zachowaj **zmiennych lokalnych** okna otwarte, aby wyświetlić te wartości.

    - Wartości w **automatycznych** tylko wtedy, gdy okno **automatycznych** jest otwarte okno

    - Wartości w DataTips, które są wyświetlane, gdy ustawisz wskaźnik myszy nad zmienną w oknie źródłowym, aby zobaczyć jej wartość. IntelliTrace nie zbiera wartości w unieruchomionych DataTips.

    Jeśli włączony jest tryb migawki i zdarzenia funkcji IntelliTrace, IntelliTrace będzie utworzenie migawki procesu aplikacji przy każdym debugera **punktu przerwania** i **krok** zdarzeń. Zarejestruje to wartości w **zmiennych lokalnych**, **automatycznych**, i **czujki** systemu windows, niezależnie od tego, czy systemu windows są otwarte, czy nie. Wartości w dowolnej etykietki danych przypięte również będą zbierane.

- **Wyjątki**

     IntelliTrace zapisuje typ wyjątku i komunikat dla tego rodzaju wyjątków:

    - Obsługiwane wyjątki, gdy wyjątek jest generowany i przechwycony

    - Nieobsługiwane wyjątki

- **Zdarzenia .NET framework**

     IntelliTrace domyślnie zapisuje najbardziej typowe zdarzenia .NET Framework. Na przykład:

    - W przypadku zdarzenia sprawdzania pola wyboru IntelliTrace zbiera stan pola wyboru i tekst.

- **Zdarzenia aplikacji SharePoint 2010 oraz SharePoint 2013**

     Można zapisać zdarzenia dotyczące profili użytkowników i zdarzenia w podzbiorze Unified Logging System (ULS) do aplikacji SharePoint 2010 i 2013 działających poza programem Visual Studio. Zdarzenia te można zapisać w pliku iTrace. Wymaga programu Visual Studio Enterprise 2017, Visual Studio Enterprise 2015, poprzednia wersja programu Visual Studio Ultimate, lub [programu Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) w **śledzenia** tryb.

     Po otwarciu pliku iTrace wprowadź identyfikator korelacji programu SharePoint, aby znaleźć odpowiadające mu żądanie sieci Web, zobaczyć zarejestrowane zdarzenia i rozpocząć debugowanie od określonego zdarzenia. Jeśli plik zawiera nieobsłużone wyjątki, można wybrać identyfikator korelacji, aby uruchomić debugowanie wyjątku.

     Zobacz:

    - [Korzystanie z autonomicznego modułu zbierającego funkcji IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

    - [Korzystanie z zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)

    - [Przewodnik: Debugowanie aplikacji SharePoint przy użyciu narzędzia IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Przechwytywania migawek**

Można skonfigurować funkcji IntelliTrace do przechwytywania migawek w każdym punkcie przerwania i debuger krok zdarzenia. IntelliTrace rejestruje pełnym stanem aplikacji w każdej migawki, która pozwala wyświetlić zmienne złożone i obliczać wyrażeń.

Zobacz [wyświetlić migawki IntelliTrace krok zwrotnego pomocą](../debugger/how-to-use-intellitrace-step-back.md).

**Zbieranie informacji o wywołania funkcji**

Możesz skonfigurować IntelliTrace, aby zbierać informacje dotyczące wywołań dla funkcji. Te informacje pozwalają wyświetlać historię stosu wywołań i umożliwiają poruszanie się w wywołaniach kodu w dowolnym kierunku. W przypadku każdego wywołania funkcji IntelliTrace rejestruje następujące dane:

- Nazwa funkcji
- Wartości pierwotnych typów danych przekazywanych jako parametry w punktach wejścia do funkcji i zwracanych w punktach wyjścia z funkcji
- Wartości właściwości automatycznych, gdy są one odczytywane lub zmieniane
- Wskaźniki do pierwszego poziomu obiektów podrzędnych, ale nie ich wartości inne, niż gdyby były równe null lub nie

> [!NOTE]
> IntelliTrace zbiera tylko 256 pierwszych obiektów w tablicach i pierwszych 256 znaków w ciągach.

Zobacz [kontroli aplikacji za pomocą debugowania historycznego](../debugger/historical-debugging-inspect-app.md).

**Zbieranie informacji o modułu**

Aby kontrolować, ile informacji na temat wywołania gromadzi IntelliTrace, określ tylko te moduły, która Cię interesują. Może to zwiększyć wydajność aplikacji w kolekcji. Zobacz sekcję [kontrolować ilość informacji zbiera dane funkcji IntelliTrace](../debugger/intellitrace-features.md#ControlCallData) w funkcji IntelliTrace.

## <a name="AffectPerformance"></a> IntelliTrace będzie spowolnić Moja aplikacja?

IntelliTrace domyślnie zbiera dane tylko dla wybranych zdarzeń IntelliTrace. To może lub nie może to spowolnić aplikacji, w zależności od organizacji kodu i struktury. Na przykład jeśli IntelliTrace często rejestruje zdarzenie, może to spowolnić aplikacji. To może również, że należy wziąć pod uwagę refaktoryzacji aplikacji.

Zbieranie informacji o wywołaniu może znacznie spowolnić pracę aplikacji. Może to również zwiększyć rozmiar wszystkich plików dziennika IntelliTrace (iTrace) zapisywanych na dysku. Aby zminimalizować te skutki, zbieraj informacji o wywołaniach tylko interesujących Cię modułów.  Aby zmienić maksymalny rozmiar plików .iTrace, przejdź do **narzędzia**, **opcje**, **IntelliTrace**, **zaawansowane**. 

## <a name="in-this-section"></a>W tej sekcji

[Funkcje IntelliTrace](../debugger/intellitrace-features.md)
[diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md)
[Użyj zapisywane są dane funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)

### <a name="blogs"></a>Blogi

[Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)

### <a name="forums"></a>Fora

[Diagnostyka programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)
