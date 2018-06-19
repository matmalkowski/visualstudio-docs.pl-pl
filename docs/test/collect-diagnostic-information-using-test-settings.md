---
title: Zbierz informacje diagnostyczne przy użyciu ustawień testów w programie Visual Studio
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
ms.openlocfilehash: 50a2462fc6b32d1f1375314a9799055acfab909b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974887"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Zbierz informacje diagnostyczne przy użyciu ustawień testów

Można użyć *ustawienia testu* w programie Visual Studio, aby zbierać dodatkowe dane po uruchomieniu testów. Na przykład można wprowadzić wideo rejestrowania w momencie uruchamiania testu. Istnieją adapterów danych diagnostycznych:

-   Zbieraj każdego kroku akcji interfejsu użytkownika w formacie tekstowym

-   Rejestrowania wszystkich akcji IU dla odtwarzanie do tyłu

-   Zbieranie informacji o systemie

-   Zbieranie danych dziennika zdarzeń

-   Gromadzenie danych IntelliTrace w celu ułatwienia izolacji błędów odtworzenia

Adaptery danych diagnostycznych mogą służyć do zmiany zachowania maszynę testową. Na przykład przy użyciu ustawienia testu w programie Visual Studio, możesz emulować różnych wąskich gardeł topologii sieci do oceny wydajności zespołu w aplikacji.

## <a name="use-test-settings-with-visual-studio"></a>Ustawienia testu za pomocą programu Visual Studio

Aby uruchomić urządzenia, kodowanego interfejsu użytkownika wydajności sieci web i testów obciążenia przy użyciu programu Visual Studio możesz można dodać, skonfiguruj i wybierz ustawienia testu do użycia podczas uruchamiania testów. Do uruchomienia testów, zbierania danych lub mają wpływ na maszynę testową zdalnie, należy określić kontrolera testu do użycia w ustawieniach testu. Kontroler testu będzie miał agentów, które mogą być używane dla każdej roli w ustawieniach testu.

## <a name="diagnostic-data-adapter-details"></a>Szczegóły adaptera danych diagnostycznych

Poniższa tabela zawiera omówienie sposobów można skonfigurować do użytku z rolami komputera lokalnego lub zdalnego adapterów danych diagnostycznych.

|Adapter danych diagnostycznych, używanym w ustawienia testu|Testy ręczne na komputerze lokalnym|Testy automatyczne|Testy ręczne: Zbieranie danych przy użyciu zestawu ról i środowisku|Uwagi|
|----------------------------------------------------------|-----------------------------------|---------------------|------------------------------------------------------------------------------|-----------|
|**Serwer Proxy klienta ASP.NET dla funkcji IntelliTrace i wpływ testu:** ten serwer proxy umożliwia zbieranie informacji o połączenia http z klienta do serwera sieci Web dla adapterów danych diagnostycznych funkcji IntelliTrace i wpływ testu.|Tak|Tak|Tak|— Użyj tego tylko po wybraniu funkcji IntelliTrace lub wpływ testu adapterów danych diagnostycznych dla roli klienta.|
|**ASP.NET profiler:** można utworzyć ustawienia testu, która obejmuje profilowania, ASP.NET, która zbiera dane dotyczące wydajności w aplikacji sieci Web ASP.NET.|Nie|Tak (zobacz Uwagi)|Nie|-Adapter danych diagnostycznych jest obsługiwana tylko w przypadku uruchamiania testów obciążenia w programie Visual Studio.|
|**Pokrycie kodu:** można utworzyć ustawienia testu, który zawiera informacje o pokryciu kodu, używany do sprawdzania, czy jaka część kodu jest objęta testy.|Nie|Tak (zobacz Uwagi)|Nie|-Pokrycie kodu można używać tylko w przypadku uruchamiania testów automatycznych z programu Visual Studio lub mstest.exe i tylko z komputera, na którym działają testu. Kolekcja zdalnego nie jest obsługiwana.<br />-Zbierania danych pokrycie kodu nie działa, jeśli masz ustawienia testu skonfigurowana do zbierania informacji IntelliTrace. **Uwaga:** adapter danych diagnostycznych ma zastosowanie tylko do ustawień testu Visual Studio. Nie jest on używany dla ustawień testu w programie Microsoft Test Manager. Ponadto ta karta jest zgodność z projekty testowe programu Visual Studio 2010. **Uwaga:** zgodności stosuje automatyczne testy są uruchamiane z Microsoft Test Manager lub na zdalnym agenta testowego w programie Visual Studio przy użyciu starszej wersji runner MSTest pokrycia kodu.|
|**Dziennik zdarzeń:** można skonfigurować testu ustawienie obejmują zbieranie dzienników zdarzeń, które zostaną uwzględnione w wynikach testu.|Tak|Tak|Tak||
|**IntelliTrace:** można skonfigurować adapter danych diagnostycznych dla *IntelliTrace* do zbierania informacji śledzenia diagnostycznego określonego celu ułatwienia izolacji błędów trudnych do odtworzenia. Spowoduje to utworzenie pliku IntelliTrace, który zawiera te informacje. IntelliTrace plik ma rozszerzenie .iTrace. Podczas testu nie powiedzie się, można utworzyć usterki. Ten błąd jest automatycznie łączony pliku IntelliTrace, który jest zapisany wraz z wyników testu. Dane są zbierane w pliku IntelliTrace zwiększa wydajność debugowania, skracając czas wymagany do odtworzenia i diagnozowanie błędów w kodzie. Z tej funkcji IntelliTrace plik sesji lokalnej może być symulowane na innym komputerze. Pozwala to ograniczyć ryzyko błędu jest nie do odtworzenia.|Tak|Tak|Tak|-Włączenie zbierania danych IntelliTrace, zbierania danych pokrycie kodu nie będzie działać.<br />— Jeśli używasz funkcji IntelliTrace dla roli klienta sieci Web, musisz też wybrać serwer Proxy klienta ASP.NET dla funkcji IntelliTrace i wpływ testu adaptera danych diagnostycznych.<br />— Obsługiwane są tylko następujące wersje programu IIS: usług IIS 7.0, IIS 7.5 i IIS 8.0.|
|**Emulacja sieci:** można określić, że chcesz umieścić obciążenia sieciowego sztuczne na test przy użyciu ustawienia testu. Emulacja sieci dotyczy emulowanie szybkość połączenia w określonej sieci, takich jak programu dial-up komunikacja do i z komputera. **Uwaga:**|Nie|Tak (zobacz Uwagi)|Nie|Adapter danych diagnostycznych emulacji sieci można użyć dla roli serwera lub klienta. Nie trzeba używać karty dla obu tych ról, które komunikują się ze sobą. **Uwaga:** adapter danych diagnostycznych ma zastosowanie tylko do ustawień testu Visual Studio. Nie jest on używany dla ustawień testu w programie Microsoft Test Manager. **Uwaga:** emulacji sieci nie można użyć w celu zwiększenia szybkości połączenia sieciowego. **Ostrzeżenie:** jeśli zawierają adapter danych diagnostycznych emulacji sieci w ustawieniach testu i zamierzasz używać go na komputerze lokalnym, a następnie może także powiązać sterownik emulacji sieci do jednej z kart sieciowych na komputerze. Sterownik emulacji sieci jest wymagana dla adaptera danych diagnostycznych emulacji sieci do funkcji. Sterownik emulacji sieci jest zainstalowany i powiązane z karty na dwa sposoby: <ul><li>**Sterownik emulacji sieci zainstalowane z Microsoft Visual Studio Test Agent:** Microsoft Visual Studio Test Agent może służyć na komputerze lokalnym i komputerach zdalnych. Po zainstalowaniu programu Visual Studio Test Agent proces instalacji obejmuje kroku konfiguracji, który wiąże sterownik emulacji sieci, do karty sieciowej. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).</li><li>**Sterownik emulacji sieci zainstalowane z Microsoft Visual Studio Test Professional:** użycie emulacji sieci po raz pierwszy, zostanie wyświetlony monit o sterownik emulacji sieci należy powiązać karty sieciowej.</li></ul> Można również zainstalować sterownik emulacji sieci z poziomu wiersza polecenia na komputerze lokalnym bez instalowania agenta testowego programu Visual Studio za pomocą następującego polecenia: **/Install VSTestConfig NETWORKEMULATION**  **Ostrzeżenie:** karty emulacja sieci jest ignorowana przez testów obciążenia. Testy obciążenia Użyj ustawień, które są określone w konfiguracji sieci w scenariuszu testu obciążenia.|
|**Informacje o systemie:** można skonfigurować ustawienia testu systemu o informacje dotyczące komputera, na którym uruchomiona jest test.|Tak|Tak|Tak||
|**Testowanie wpływu:** można zbierać informacje o tym, które metody kodu aplikacji zostały użyte podczas uruchamiania przypadkiem testowym. To może być używany razem zmiany wprowadzone przez deweloperów w celu ustalenia, które testy wpłynęła na te zmiany programowanie kodu aplikacji.|Tak|Tak|Tak|— Jeśli są zbierane dane wpływu testu dla roli klienta sieci Web, musisz też wybrać serwer Proxy klienta ASP.NET dla funkcji IntelliTrace i wpływ testu adaptera danych diagnostycznych.<br />— Obsługiwane są tylko następujące wersje programu IIS: usług IIS 7.0, IIS 7.5 i IIS 8.0.|
|**Rejestrator wideo:** można utworzyć nagrywanie wideo z sesji pulpitu po uruchomieniu testu. Wideo może pomóc innym członkom zespołu wyizolować problemy z aplikacji, które są trudne do odtworzenia.|Tak|Tak (zobacz Uwagi)|Tak|— Jeśli jest włączone oprogramowanie agenta testowego do uruchamiania jako proces zamiast usługi, można utworzyć nagrania podczas uruchamiania testów automatycznych wideo.|