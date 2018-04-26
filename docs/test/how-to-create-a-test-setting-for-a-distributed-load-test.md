---
title: Tworzenie ustawień testu dla rozproszonego testu obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 1b9ffd7206023885fc45e66af585ca34f75ce67f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-test-setting-for-a-distributed-load-test"></a>Porady: tworzenie ustawień testu dla rozproszonego testu obciążenia

Skonfiguruj *ustawienia testu* dla testów obciążenia, dzięki czemu może dystrybuować te testy na wielu komputerach przy użyciu agentów testowych i kontrolery testów. Można również skonfigurować ustawienia testu, aby używać *adapterów danych diagnostycznych*, który określa rodzaj danych, które mają być zbierane lub jak wpływają na testowe maszyny, podczas uruchamiania testów obciążenia w programie Visual Studio.

Na przykład umożliwia profilera ASP.NET adaptera danych diagnostycznych zbieranie podział wydajność kodu. Ponadto adapterów danych diagnostycznych może służyć do symulowania wąskich gardeł na maszynie testowej lub Zmniejsz dostępnej pamięci systemu.

Ustawienia testu dla programu Visual Studio są przechowywane w pliku. Ustawienia testu definiują następujące informacje dotyczące poszczególnych ról:

-   Zestaw ról, które są wymagane dla aplikacji w ramach testu

-   Rola służące do uruchamiania testów

-   Adaptery danych diagnostycznych do użycia dla każdej roli

Po uruchomieniu testów, należy wybrać do użycia jako ustawienia aktywnego testu, w zależności od tego, czy wymagane dla tego uruchomienia testu określonych ustawień testu. Plik ustawień testu jest przechowywana jako część rozwiązania. Nazwa pliku ma rozszerzenie *.testsettings*.

Po dodaniu wydajności sieci Web i testów obciążenia projektu do rozwiązania, *Default.testsettings* tworzony jest plik. Plik jest automatycznie dodawany do rozwiązania, w obszarze **elementy rozwiązania** folderu. Ten plik uruchomi testy lokalnie bez żadnych adapterów danych diagnostycznych. Można dodać inny *.testsettings* plików lub edytować *.testsettings* pliku, aby określić adapterów danych diagnostycznych i kontrolery testów.

Kontroler testu będzie miał agentów, które mogą być używane dla każdej roli w ustawieniach testu. Aby uzyskać więcej informacji na temat kontrolerów testów i agentów testowych, zobacz [Zarządzanie kontrolerami testów i agentów testu z programem Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Wykonaj następujące kroki, aby utworzyć i Usuń ustawień testu w rozwiązaniu dla testów obciążenia, które mają działać w programie Visual Studio.

## <a name="create-a-test-setting-for-a-distributed-load-test"></a>Tworzenie ustawień testu dla rozproszonego testu obciążenia

### <a name="to-add-a-test-settings-for-a-distributed-load-test"></a>Aby dodać ustawienia testu dla rozproszonego testu obciążenia

1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **elementy rozwiązania**, wskaż polecenie **Dodaj**, a następnie wybierz pozycję **nowy element**.

     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.

2.  W **zainstalowane szablony** okienku wybierz **ustawień testu**.

3.  (Opcjonalnie) W **nazwa** Zmień nazwę pliku ustawień testu.

4.  Wybierz **dodać**.

     Nowy plik ustawień testu jest wyświetlana w Eksploratorze rozwiązań w obszarze **elementy rozwiązania** folderu.

    > [!NOTE]
    > Listę ustawień testu, które wyświetla Visual Studio Enterprise jest określana na podstawie listy plików ustawień testu w **elementy rozwiązania** folderu. Na przykład pliki ustawień testu w folderze elementów rozwiązania są wyświetlane podczas korzystania z **wybierz aktywne ustawienia testu** opcja **Test** menu. Oznacza to, że po przeniesieniu pliku ustawień testów do innej lokalizacji w hierarchii rozwiązania go można już używać jako ustawienie testu w Visual Studio zintegrowane środowisko programistyczne.

5.  **Ustawień testu** zostanie wyświetlone okno dialogowe. **Ogólne** strony jest zaznaczone.

     Teraz możesz edytować i zapisać wartości ustawień testu.

    > [!NOTE]
    > Każdego ustawienia testu, tworzonych jest wymienione jako rozwiązaniem dla **wybierz aktywne ustawienia testu** i **edytowanie ustawień testu** opcje na **Test** menu.

6.  W obszarze **nazwa**, wpisz nazwę dla ustawienia testu.

7.  (Opcjonalnie) W obszarze **opis**, wpisz opis testu ustawienie tak innych członków zespołu wiedzieć, co jest przeznaczone do.

8.  (Opcjonalnie) Aby wybrać domyślny schemat nazewnictwa dla Twojego uruchomień testów, zaznacz **domyślny schemat nazewnictwa**. Aby zdefiniować własny schemat nazewnictwa, wybierz **użytkownika schemat** i wpisz tekst, który ma być **prefiksu tekstu**. Aby dołączyć sygnaturę daty i godziny do nazwy uruchomienia testu, wybierz **Dołącz sygnaturę daty i godziny**.

9. Wybierz **ról**.

     **Ról** zostanie wyświetlona strona.

     ![Rola ustawień testu](../test/media/load_testtestrole.png "Load_TestTestRole")

10. Do uruchomienia testów zdalnie, lub aby zdalnie uruchamiać testy i zdalne zbieranie danych, należy użyć **wykonywania metoda testowa** listy rozwijanej i wybierz pozycję **zdalne wykonywanie kodu**.

11. Użyj **kontrolera** listy rozwijanej wybierz kontrolera testu dla agentów testowych z **kontrolera** który będzie służyć do uruchamiania testów lub zbierania danych.

    > [!NOTE]
    > Jeśli po raz pierwszy, dodawania kontrolera, kontrolery nie będzie wyświetlane na liście rozwijanej. Lista zostanie wypełniona przez poprzednie kontrolery, określonych w innych ustawień testu. Nazwa kontrolera, należy wpisać w polu (na przykład **TestControllerMachine1**).

12. Aby dodać role, które mają być używane do uruchamiania testów i zbierania danych, w obszarze **ról**, wybierz **Dodaj**.

13. Wpisz nazwę roli w **nazwa** kolumny. Na przykład rola może być "Serwera sieci Web".

14. Powtórz kroki od 12 i 13, aby dodać wszystkie role, które są potrzebne.

     Każda rola używa agenta testowego, który jest zarządzany przez kontrolera testu.

15. Wybierz rolę, którą chcesz uruchomić testy, a następnie wybierz pozycję **Ustaw jako rolę do uruchomienia testów**.

    > [!IMPORTANT]
    > Inne role, które możesz utworzyć i zdefiniować testy nie zostaną uruchomione, ale będzie można użyć tylko w celu zbierania danych zgodnie z danych i adapterów diagnostycznych, które można określić dla ról w **dane i Diagnostyka** strony.

16. Aby ograniczyć liczbę agentów, które mogą być używane dla roli, wybierz rolę, a następnie wybierz **Dodaj** na pasku narzędzi w obszarze **atrybuty agenta dla wybranej formant Karta**e.

     **Reguły wyboru agenta** zostanie wyświetlone okno dialogowe.

     Wpisz nazwę w **nazwa atrybutu** i wartość w **wartość atrybutu**, a następnie wybierz pozycję **OK**. Dodaj dowolną liczbę atrybutów, ile potrzebujesz.

     Na przykład można dodać atrybutu o nazwie "Pamięci RAM > 16GB" o wartości "True" lub "False", aby odfiltrować testowe maszyny agenta, które mają więcej niż 16GB pamięci. Aby zastosować ten sam atrybut jeden lub więcej agentów testowych, możesz użyć okno dialogowe Zarządzanie aplikacją Test Controller. Aby uzyskać więcej informacji, zobacz [Zarządzanie kontrolerami testów i agentami testowymi za pomocą programu Visual Studio](../test/manage-test-controllers-and-test-agents.md).

17. Wybierz **danych i informacji diagnostycznych**.

     **Danych i informacji diagnostycznych** zostanie wyświetlona strona.

     ![Testowanie ustawienie danych i informacji diagnostycznych](../test/media/load_testtest.png "Load_TestTest")

18. W **dane i Diagnostyka** strony, należy zdefiniować, co oznacza wybierając rolę *adapterów danych diagnostycznych* że roli będzie używać do zbierania danych. W związku z tym jeśli jeden lub więcej danych i adapterów diagnostycznych są włączone dla roli, kontrolera testu wybierz komputer agenta testowania zbierania danych dla określonych danych i adapterów diagnostycznych na podstawie atrybutów, które zdefiniowane dla roli. Aby wybrać danych i adapterów danych diagnostycznych, które mają być zbierane dla każdej roli, wybierz rolę. Dla każdej roli wybierz adapterów danych diagnostycznych, odpowiednio do potrzeb testów. Aby skonfigurować poszczególne karty danych diagnostycznych, wybranej dla każdej roli, należy wybrać **Konfiguruj**.

     **Przykład ról i adapterów danych diagnostycznych:**

     Na przykład można utworzyć roli klienta o nazwie "Desktop Client", który ma atrybut "Używa SQL" wartość "True", a rola serwera o nazwie "SQL Server", który ma atrybut ustawiony na "Pamięci RAM > 16GB". Jeśli określono, że "Desktop Client" Uruchom testy, wybierając **Ustaw jako rolę do uruchomienia testów** w **ról** , kontroler testów zostanie wybierz maszyny, które mają agentów testowych, które zawierają atrybut "Używa SQL" ustawiony na wartość "True", na której uruchamiać testy. Kontroler testów zostanie również wybrać maszyny serwera SQL, których agentów testowych, obejmujące atrybut "Pamięci RAM > 16GB" tylko do zbierania danych został zdefiniowany przez danych i adapterów diagnostycznych, które znajdują się w roli. Agent testy "Desktop Client" może również zbierać dane dotyczące maszyn, na których zostanie wykonany, jeżeli wybierzesz zbyt danych i adapterów diagnostycznych dla tej roli.

     Aby uzyskać szczegółowe informacje dotyczące każdego adaptera danych diagnostycznych i sposobie konfigurowania go można wyświetlić skojarzonego tematu w poniższej tabeli.

     Aby uzyskać więcej informacji na temat adapterów danych diagnostycznych, zobacz [zbieranie diagnostycznych informacji za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md).

     **Adaptery danych diagnostycznych dla testów obciążenia**

    |Adapter danych diagnostycznych|Używanie w testach obciążenia|Skojarzonego tematu|
    |-----------------------------|-------------------------|----------------------|
    |**Serwer Proxy klienta ASP.NET dla funkcji IntelliTrace i wpływ testu:** ten serwer proxy umożliwia zbieranie informacji o połączenia http z klienta do serwera sieci Web dla adapterów danych diagnostycznych funkcji IntelliTrace i wpływ testu.|![Ikona informacji](../test/media/vc364f4.gif)<br /><br /> W przypadku braku konkretna potrzeba do zbierania informacji systemowych maszyny agenta testowego nie zawierają tej karty. **Uwaga:** nie zaleca się użycie karty IntelliTrace w testach obciążenia z powodu problemów występujących ze względu na dużą ilość zbieranych danych. <br /><br /> Dane wpływu testu nie są zbierane za pomocą testów obciążenia.||
    |**IntelliTrace:** można skonfigurować określone diagnostycznymi śledzenia informacji przechowywanych w pliku dziennika. Plik dziennika ma rozszerzenie .tdlog. Po uruchomieniu testu i krok testu kończy się niepowodzeniem, można utworzyć usterki. Plik dziennika, zawierający dane śledzenia diagnostycznego są automatycznie dołączane do tej usterki. Dane są zbierane w pliku dziennika zwiększa wydajność debugowania, skracając czas wymagany do odtworzenia i diagnozowanie błędów w kodzie. Z tego dziennika plik sesji lokalnej można utworzyć ponownie na innym komputerze. Pozwala to ograniczyć ryzyko błędu nie można odtworzyć.<br /><br /> Aby uzyskać więcej informacji, zobacz [IntelliTrace zbieranie danych](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Ikona ważnej informacji](../test/media/vc364f3.gif)<br /><br /> Nie zaleca się użycie karty IntelliTrace w testach obciążenia z powodu problemów występujących z powodu dużej ilości danych, który został zebrany i rejestrowane. Należy próbować używać karty IntelliTrace tylko w testach obciążenia, które nie są uruchamiane długa i nie należy używać wielu agentów testowych.|[Porady: zbieranie danych IntelliTrace pomocnych w debugowaniu trudnych problemów](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**ASP.NET Profiler:** można utworzyć ustawienia testu, która obejmuje profilowania, ASP.NET, która zbiera dane dotyczące wydajności w aplikacji sieci Web ASP.NET.|Adapter danych diagnostycznych profilera ASP.NET profile proces Internet Information Services (IIS), więc nie będzie działać na serwerze sieci Web development. Profilowanie witryny sieci Web w teście obciążenia sieci, należy zainstalować agenta testowego na maszynie, która jest zasilany z usług IIS. Agent testowy nie będzie generowany obciążenia, ale będzie ona tylko agenta. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).|[Porady: Konfiguracja profilera ASP.NET do ładowania testów za pomocą ustawień testów](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Dziennik zdarzeń:** można skonfigurować testu ustawienie obejmują zbieranie dzienników zdarzeń, które zostaną uwzględnione w wynikach testu.||[Porady: Konfigurowanie zbierania zdarzeń dziennika przy użyciu ustawień testów](http://msdn.microsoft.com/en-us/48d67891-6018-4549-83e3-213d5d824a02)|
    |**Emulacja sieci:** można określić, czy chcesz umieścić obciążenia sieciowego sztuczne na test przy użyciu ustawienia testu. Emulacja sieci dotyczy emulowanie szybkość połączenia w określonej sieci, takich jak programu dial-up komunikacja do i z komputera. **Uwaga:** emulacji sieci nie można użyć w celu zwiększenia szybkości połączenia sieciowego.|Karty emulacja sieci jest ignorowana przez testów obciążenia. Testy obciążenia Użyj ustawień, które są określone w konfiguracji sieci w scenariuszu testu obciążenia.<br /><br /> Aby uzyskać więcej informacji, zobacz [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Informacje o systemie:** można skonfigurować ustawienia testu systemu o informacje dotyczące maszyn, na których uruchomiono modułu zbierającego dane diagnostyczne i dane informacje o systemie. Informacje o systemie jest określony w wynikach testów przy użyciu ustawienia testu.|![Ikona informacji](../test/media/vc364f4.gif)<br /><br /> Może zbierać informacje o systemie z agentów obciążenia i systemu w ramach testu.|Do zebrania tych informacji jest wymagana żadna konfiguracja.|
    |**Wpływ testu:** można zbierać informacje o tym, które metody kodu aplikacji zostały użyte podczas uruchamiania przypadkiem testowym. To może być używany razem zmiany wprowadzone przez deweloperów w celu ustalenia, które testy wpłynęła na te zmiany programowanie kodu aplikacji.|Dane wpływu testu nie są zbierane z testami obciążenia.||
    |**Rejestrator wideo:** można utworzyć nagranie sesję pulpitu, po uruchomieniu testów automatycznych. Może to być przydatne w celu wyświetlenia akcje użytkownika dla kodowanego testu interfejsu użytkownika. Wideo może pomóc innym członkom zespołu wyizolować problemy z aplikacji, które są trudne do odtworzenia. **Uwaga:** , gdy testy są uruchomione zdalnie Rejestrator wideo nie będzie działać, chyba że agent jest uruchomiony w trybie procesu interaktywnego.|![Ikona ważnej informacji](../test/media/vc364f3.gif) **Ostrzeżenie:** nie zaleca się użycie karty Rejestrator wideo dla testów obciążenia.|[Porady: zawierają nagrania ekranu i głosu podczas testów przy użyciu ustawień testów](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Wybierz **wdrożenia**.

     **Wdrożenia** zostanie wyświetlona strona.

20. Aby utworzyć oddzielny katalog wdrożenia zawsze uruchomić testy, wybierz **włączyć wdrożenie**.

    > [!NOTE]
    > Jeśli to zrobisz, można skompilować aplikację podczas uruchamiania testów.

21. Aby dodać plik do katalogu, którego używasz do uruchamiania testów, wybierz **Dodaj plik**, a następnie wybierz plik, który chcesz dodać.

    > [!NOTE]
    > Podczas uruchamiania obciążenia testy wtyczki zestawy, pliki danych i przekazane pliki są automatycznie wdrażane.

22. Aby dodać katalog do katalogu, którego używasz do uruchamiania testów, wybierz **Dodaj katalog** , a następnie wybierz katalog, który chcesz dodać.

23. Aby uruchomić skrypty przed i po testy, wybierz **skrypty instalacyjne i czyszczące**.

     **Skrypty instalacyjne i czyszczące** zostanie wyświetlona strona.

    1.  Wpisz lokalizację pliku skryptu w **skrypt instalacyjny** lub wybierz wielokropek (**...** ) można znaleźć w skrypcie Instalatora.

    2.  Wpisz lokalizację pliku skryptu w **skrypt czyszczący** lub wybierz wielokropek (**...** ) można znaleźć skrypt czyszczenia.

24. Aby uruchomić testy przy użyciu innego hosta, wybrać **hostów**.

    1.  W **typ hosta**, upewnij się, że **domyślne** jest zaznaczone.

        > [!NOTE]
        > **ASP.NET** w **hosta typu** nie jest obsługiwane w testach obciążenia.

    2.  Umożliwia Uruchom test w procesie 32-bitowy lub 64-bitowych listy rozwijanej wybierz, czy testy wydajności i jednostki sieci Web w teście obciążenia, sieci do uruchamiania jako procesów 32-bitowy lub 64-bitowej.

        > [!NOTE]
        > Maksymalna elastyczność należy skompilować wydajności sieci Web i obciążenia projekty testowe przy użyciu **Any CPU** konfiguracji. Następnie możesz uruchomić na zarówno 32-bitowe i 64-bitowych agentów. Kompilowanie wydajności sieci Web i testów obciążenia projektów przy użyciu **64-bitowych** konfiguracji oferuje nie korzyści.

25. (Opcjonalnie) Aby ograniczyć czas dla każdego uruchomienia testu i poszczególne testy, wybierz **przekroczeń limitu czasu testu.**

    1.  Aby przerwać testu po przekroczeniu limitu czasu, wybierz **Przerwij uruchomienie testu, jeśli całkowity czas przekracza** , a następnie wpisz wartość dla tego limitu.

    2.  Niepowodzenie pojedynczy test, po przekroczeniu limitu czasu, wybierz **Oznacz pojedynczy test jako zakończony niepowodzeniem, jeśli czas jego wykonywania przekroczy**i wprowadź wartość dla tego limitu.

26. Pomiń **testu jednostkowego**. Testy obciążenia nie należy używać tych ustawień.

27. Pomiń **sieci Web testu**. Testy obciążenia nie należy używać tych ustawień.

28. Aby zapisać ustawienia testu, wybierz **Zapisz jako**. Wpisz nazwę pliku, który ma być **nazwa obiektu**.

    > [!NOTE]
    > Jeśli należy zmienić ustawienia testu, wybierz **Test** , a następnie wybierz **edytowanie ustawień testu** i wskaż Ustawienia testu, które zostały utworzone.

### <a name="to-remove-a-test-settings-from-your-solution"></a>Aby usunąć ustawienia testu z rozwiązania

W folderze elementów rozwiązania w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy ustawień testu, które chcesz usunąć, a następnie wybierz pozycję **Usuń**.

Plik ustawień testu jest usuwany z rozwiązania. Ta zmiana jest odzwierciedlone na liście opcji **wybierz aktywne ustawienia testu** i **edytowanie ustawień testu** opcje na **testu** menu.

## <a name="see-also"></a>Zobacz także

- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Zbierz informacje diagnostyczne przy użyciu ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)