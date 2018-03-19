---
title: "Zarządzanie kontrolerami testów i agenci testowi w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d99d01dbe26354b8a3b3afa18d1337c64d1b390
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="manage-test-controllers-and-test-agents"></a>Zarządzanie kontrolerami testów i agenci testowi

Jeśli chcesz użyć programu Visual Studio, aby zdalnie uruchamiać testy, rozkładanie testu na wielu komputerach lub Uruchamianie testów obciążenia, należy skonfigurować kontrolera testów, agenci testowi i plik ustawień testu. W tym temacie opisano, jak zarządzać kontrolerów testów i agenci testowi po zainstalowaniu i skonfigurowaniu ich po raz pierwszy.

Jeśli program Microsoft Test Manager używane do uruchamiania testów w środowiskach laboratoryjnych, zarządzać kontrolerów testów i agentów ich za pomocą **Test Manager kontrolera** w **Centrum laboratoryjnego** dla programu Microsoft Test Manager. Ten temat dotyczy tylko wtedy, gdy Uruchamianie testów za pomocą programu Visual Studio.

Aby dowiedzieć się, jak instalowanie i konfigurowanie agentów testowych i testowanie kontrolerów do uruchamiania testów w programie Visual Studio, zobacz [Konfigurowanie agentów testowych i kontrolerów](../test/configure-test-agents-and-controllers-for-load-tests.md).

Do konfigurowania i monitorowania kontrolera testów i wszystkich zarejestrowanych agentów, musi mieć plik ustawień testu w projekcie testowym zawierający testy, które chcesz uruchomić. Otwórz plik ustawień testu, wybierz pozycję **roli** i wybierz polecenie **Zarządzaj aplikacją Test Controller** z listy rozwijanej dla **kontrolera** pola.

W projekcie testu obciążenia można także **Zarządzaj aplikacją Test Controller** z **testów obciążenia** menu.

## <a name="add-a-test-agent-to-a-test-controller"></a>Dodaj agenta testowego z kontrolerem testu

Można dodać agenta testowego do innego kontrolera testów lub może być konieczne Dodaj agenta testowego z kontrolerem testu, który został właśnie zainstalowany.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Aby dodać agenta testowego z kontrolerem testu

1. Wybierz **Start** > **testu narzędzie konfiguracji agenta**.

     **Skonfigurować agenta testowego** zostanie wyświetlone okno dialogowe.

    > [!NOTE]
    > Musi mieć agenta testowego, zainstalowane, aby dodać go do kontrolera testów. Aby uzyskać więcej informacji na temat instalowania agenta testowego, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

2. Jeśli chcesz zmienić sposób uruchomienia agenta testowego, wybierz **opcji przebiegu**.

     Dostępne są dwie opcje jak idzie agenta testowego do uruchomienia:

     **Usługa** , jeśli jest konieczne uruchamianie zautomatyzowanych testów w interakcji z pulpitem, takie jak kodowanych testów interfejsu użytkownika lub tworzenie nagrania, gdy test jest uruchamiany, w obszarze wideo **Uruchom agenta testowego jako**, wybierz pozycję **usługi**. Agent testowy zostanie uruchomiona jako usługa. Wybierz **dalej**.

     Teraz można wprowadzić szczegóły użytkownika podczas uruchamiania usługi agenta testowego.

    1. Wprowadź nazwę w **nazwy użytkownika**.

    2. Wprowadź hasło w **hasło**.

        |**Informacje o koncie użytkownika ważne**|
        |--------------------------------------------|
        |-Null hasła nie są obsługiwane dla kont użytkowników.|
        |— Jeśli chcesz użyć modułu zbierającego IntelliTrace lub emulacji sieci, konto użytkownika musi być członkiem grupy Administratorzy.|
        |— Jeśli nazwa użytkownika agenta nie jest w usłudze agenta spróbuje dodać ją, co wymaga uprawnień na kontrolerze testów.|
        |-Użytkownika, który próbuje użyć kontrolera testu musi być w konta użytkowników z kontrolerem testów lub nie będzie można uruchamiać testy na kontrolerze.|

     **Proces interakcyjny** Jeśli chcesz uruchomić zautomatyzowanych testów, które musi współdziałać z pulpitem, takich jak kodowanych testów interfejsu użytkownika lub tworzenie nagrania po uruchomieniu testu wideo, wybierz **procesu interaktywnego**. Będzie można uruchomić agenta testowego jako procesu interaktywnego zamiast usługi.

     Na następnej stronie wprowadź szczegóły użytkownika podczas uruchamiania agenta testowego jako proces i inne opcje.

    1. Wprowadź nazwę w **nazwy użytkownika**.

    2. Wprowadź hasło w **hasło**.

        > [!NOTE]
        > Konfigurowanie agenta testowego do uruchamiania jako proces interaktywny z innym użytkownikiem, który nie jest aktualnie aktywnego użytkownika, należy ponownie uruchomić komputer, zaloguj się jako tego inny użytkownik, który można uruchomić agenta. Ponadto null hasła nie są obsługiwane dla kont użytkowników. Jeśli chcesz użyć modułu zbierającego IntelliTrace lub emulacji sieci, konto użytkownika musi być członkiem grupy Administratorzy.

        |**Informacje o koncie użytkownika ważne**|
        |--------------------------------------------|
        |-Null hasła nie są obsługiwane dla kont użytkowników.|
        |— Jeśli chcesz użyć IntelliTrace lub danych emulacji sieci i diagnostycznych karty, konto użytkownika musi być członkiem grupy Administratorzy. Jeśli komputer, który jest uruchomiony agent testowy ma systemu operacyjnego, który ma najmniej uprzywilejowane konto użytkownika, konieczne będzie również uruchomić jako administrator (z podwyższonym poziomem uprawnień).|
        |— Jeśli nazwa użytkownika agenta nie jest w usłudze agenta spróbuje dodać ją, co wymaga uprawnień na kontrolerze testów.|
        |-Użytkownika, który próbuje użyć kontrolera testu musi być w konta użytkowników z kontrolerem testów lub nie będzie można uruchamiać testy na kontrolerze.|

    3. Aby upewnić się, że po ponownym uruchomieniu komputera mającego agenta testowego można uruchomić testy, należy skonfigurować komputer do automatycznego logowania jako Użyj agenta testowego. Wybierz **automatyczne logowanie**. To będzie przechowywać nazwy użytkownika i hasła w postaci zaszyfrowanej w rejestrze.

    4. Aby upewnić się, że wygaszacz ekranu jest wyłączona, ponieważ może to zakłócać żadnych testów automatycznych, które musi współdziałać z pulpitem, wybierz **jest wyłączona, upewnij się, że wygaszacz ekranu**.

        > [!WARNING]
        > Jeśli automatyczne logowanie lub wyłączenie wygaszacza ekranu są zagrożenia bezpieczeństwa. Po włączeniu automatycznej dziennika na, można włączyć innych użytkowników, aby uruchomić ten komputer i aby móc korzystać z konta, który loguje się automatycznie. Wyłączenie wygaszacza ekranu komputera nie może być wyświetlany monit dla użytkownika zalogować się do odblokowania komputera. Dzięki temu każda osoba, która uzyskać dostęp do komputera, jeśli mają dostęp fizyczny do komputera. Po włączeniu tych funkcji na komputerze, należy upewnić się, że te komputery znajdują się fizycznie zabezpieczonej. Na przykład te komputery znajdują się w fizycznie zabezpieczonej laboratorium. (Jeśli wyczyścisz **jest wyłączona, upewnij się, że wygaszacz ekranu**, nie obsługuje wygaszacz ekranu.)

3. Aby zarejestrować tego agenta z innego kontrolera testu, wybierz **Zarejestruj w kontrolerze testu.** Wpisz nazwę kontrolera testu, a następnie **:** i numer portu, którego używasz w **zarejestrować agenta testowego w następującym kontrolerem testów**. Na przykład wpisz **agent1:6901**.

    > [!NOTE]
    > Domyślny numer portu to 6901.

4. Aby zapisać zmiany, wybierz **Zastosuj ustawienia**. Zamknij **Podsumowanie konfiguracji** okno dialogowe, a następnie zamknij narzędzie konfiguracji agenta testowego.

> [!WARNING]
> Jeśli agent jest skonfigurowana do uruchamiania na inny kontroler testu, należy usunąć agenta testowego z danego kontrolera.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Usuń agenta testowego z kontrolera testów

Agent testowy można ustawić stanu offline, można było usunąć.

> [!NOTE]
> Nie można użyć tej procedury można usunąć agentów, które są zarejestrowane z kontrolerem jako część środowiska laboratoryjnego. Aby usunąć tych agentów z kontrolerem, należy usunąć ze środowiskiem za pomocą programu Microsoft Test Manager.

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Aby usunąć agenta testowego z kontrolera testów

1. Jeśli kontroler testów nie jest zarejestrowany z projektem zespołowym, wykonaj następujące kroki.

    1. W programie Visual Studio Otwórz plik ustawień testu dla projektu testowego, wybierz pozycję **roli** i wybierz polecenie **Zarządzaj aplikacją Test Controller** z listy rozwijanej dla **kontrolera** pola.

         **Administrowania kontrolerem testów** zostanie wyświetlone okno dialogowe.

    2. W **kontrolera** listy rozwijanej liście, wpisz nazwę komputera, na którym skonfigurowano kontrolera testu. Jeśli wcześniej administrowanych kontrolera testów, można wybrać nazwę z listy.

    3. W **agentów** okienku, wybierz nazwę agenta testowego. Jeśli agent jest nadal w trybie online, wybierz **Offline.** Aby usunąć go, wybierz **Usuń**.

        > [!NOTE]
        > Usuwanie agenta testowego, po prostu usuwa skojarzenia go z kontrolera testów. Aby całkowicie odinstalować agenta testowego, użyj **programy i funkcje** Panelu sterowania na komputerze agenta testowego.

2. Jeśli kontroler testów został zarejestrowany z projektem zespołowym, należy usunąć agenta przy użyciu programu Microsoft Test Manager.

## <a name="change-the-settings-for-a-test-agent"></a>Zmień ustawienia dla agenta testowego

Stan agenta testowego może być jednym z następujących wartości:

|Stan|Opis|
|------------|-----------------|
|Uruchamianie testu|Uruchamianie testów|
|Gotowe|Uruchom testy lub zbierać dane i informacje diagnostyczne|
|Offline|Aby uruchomić testy lub zbierać dane i informacje diagnostyczne niedostępny|
|odłączony|Agent testowy nie jest uruchomiona.|

Można zmienić stanu i inne ustawienia dla agenta testowego, korzystając z poniższych procedur.

### <a name="to-change-the-settings-of-a-test-agent"></a>Aby zmienić ustawienia agenta testowego

> [!NOTE]
> Jeśli agent testowy jest zarejestrowany do kontrolera testu, który został zarejestrowany z projektem zespołowym, Zmień ustawienia w programie Microsoft Test Manager.

1. Do konfigurowania i monitorowania kontrolera testów i wszystkich agentów zarejestrowanych dla testu obciążenia, wybierz **testów obciążenia** menu w programie Visual Studio, a następnie wybierz **Zarządzaj aplikacją Test Controller**. Do innych testów, otwórz plik ustawień testu dla projektu testowego w programie Visual Studio, wybierz pozycję **roli** i wybierz polecenie **Zarządzaj aplikacją Test Controller** z listy rozwijanej dla **kontrolera**pola.

   **Zarządzanie aplikacją Test Controller** zostanie otwarte okno dialogowe.

1. Wybierz nazwę kontrolera testu agentów testowych, których chcesz zmienić liście kontrolera testu. Jeśli kontroler testów nie znajdują się na liście, sprawdź, czy kontroler testu jest poprawnie zarejestrowany. Aby uzyskać więcej informacji zobacz procedurę o sposobie konfigurowania kontrolera testu.

1. (Opcjonalnie) W **Test agentów** okienku, wybierz komputer agenta testu, dla którego chcesz zmienić właściwości.

1. Wybierz **właściwości**.

1. Zmień następujące właściwości agenta testowego zgodnie z wymaganiami:

|Właściwości agenta testowego|Opis|
|-------------------------|-----------------|
|**Wagi**|Umożliwia rozłożenie obciążenia, gdy użytkownik korzysta z różne poziomy wydajności agentów testowych. Na przykład agenta testowego z wagi 100 otrzymuje dwa razy obciążenia jako agenta testowego z wagi 50.|
|**Przełączania IP**|Służy do konfigurowania przełączania IP. Przełączania IP umożliwia agenta testowego do wysyłania żądań do serwera przy użyciu zakresu adresów IP. Symuluje to wywołania, które pochodzą z różnych klientów.<br /><br /> Przełączanie IP jest ważne, jeśli test obciążenia uzyskuje dostęp do farmy sieci Web. Większość modułów równoważenia obciążenia ustanowić koligację między klientem a konkretnego serwera sieci Web przy użyciu adresu IP klienta. Jeśli wszystkie żądania są one pochodzą z jednego klienta, usługi równoważenia obciążenia nie będą Równoważenie obciążenia. Uzyskanie Równoważenie obciążenia dobrej w kolektywie serwerów sieci Web, upewnij się, że żądania pochodzą z zakresu adresów IP. **Uwaga:** można określić kartę sieciową lub użyć **(wszystkie nieprzypisane)** do automatycznego wybierania który obecnie nie jest używany. <br /><br /> Aby użyć funkcji przełączania IP, musi działać usługa Visual Studio Test Agent użytkownika do grupy Administratorzy na tym komputerze agenta. Ten użytkownik jest wybrane podczas instalacji agenta, ale może zostać zmieniona przez zmodyfikowanie właściwości usługi i uruchomić ją ponownie.<br /><br /> Aby sprawdzić, czy przełączania IP działa poprawnie, Włącz rejestrowanie na serwerze sieci Web usług IIS, za pomocą funkcji rejestrowania usług IIS można sprawdzić, czy żądania pochodzą z adresów IP, które można skonfigurować.|
|**Atrybuty**|Zestaw par nazw i wartości, których można użyć w zaznaczeniu agenta testowego. Na przykład test może wymagać określonego systemu operacyjnego. Można dodawać atrybuty w **ról** kartę testowe pliku ustawień i może służyć do wybierz agenta testowego, który posiada odpowiadającego atrybutów. Jeśli chcesz uruchomić test na wielu komputerach, tworzenia atrybutu w rola ustawień testu, który jest skonfigurowany do uruchomienia testów, a następnie skonfiguruj pasującego atrybutu na każdy agent testu, który ma być używany w tej roli. **Uwaga:** to ustawienie jest dostępna tylko dla agentów testowych, które są rejestrowane w kontrolerze testu, który nie jest zarejestrowany do projektu zespołowego, ponieważ te atrybuty są używane tylko w ustawieniach testu dla programu Visual Studio.|

Przetestuj agenta wagi i test agent atrybutu zmiany zaczynają obowiązywać natychmiast, ale nie wpływają na testy, które są uruchomione. Zakres adresów IP zostanie uwzględniona po ponownym uruchomieniu kontrolera testów.

(Opcjonalnie) Aby zmienić stan agenta testowego, wybierz z listy agenta, a następnie wybierz akcję z dostępnych wyborów na podstawie bieżącego stanu agenta.

> [!NOTE]
> Jeśli agenta testowego jest uruchomiona jako proces, możesz zarządzać stan agenta testowego z ikonę w obszarze powiadomień, które działają na komputerze, w którym zainstalowano agenta testowego. Oznacza to, stan agenta testowego. Można uruchomić, zatrzymać lub ponownie uruchomić agenta, jeśli została uruchomiona jako proces, za pomocą tego narzędzia. Aby uruchomić agenta testowego jako proces, jeśli nie jest uruchomiona, wybierz **Start**, **wszystkie programy**, **programu Microsoft Visual Studio** , **Microsoft Visual Studio Test Agent**. Spowoduje to dodanie ikonę w obszarze powiadomień.

## <a name="configure-a-test-controller"></a>Skonfiguruj kontrolera testu

Aby skonfigurować kontroler testu, należy użyć **zespołu Test Controller Configuration Tool**. Po skonfigurowaniu kontroler testu można zarejestrować kontrolera testu z innej kolekcji projektów zespołowych lub Wyrejestruj kontroler testu z kolekcji projektów zespołowych.

Jeśli chcesz zarejestrować kontroler testu z kolekcji projektów Team Foundation Server, konto używane dla usługi kontrolera testu musi być członkiem grupy kont usługi testów kolekcji projektów dla kolekcji projektów zespołowych, lub Konto używane do uruchamiania narzędzia do konfiguracji kontrolera testu musi być Administrator kolekcji projektów.

> [!NOTE]
> Jeśli musisz wyrejestrować kontrolera testu z kolekcji projektu zespołowego o istniejących środowiskach w kolekcji projektów zespołowych, tych środowisk nadal są obsługiwane, jeśli można przenieść tej kolekcji projektów zespołowych i wykonaj ponowną rejestrację kontrolera testów do tego zespołu przeniesiony Kolekcja projektu.

### <a name="to-configure-a-test-controller"></a>Można skonfigurować kontrolera testów

1. Aby uruchomić narzędzie w dowolnym momencie zmienić konfigurację kontroler testu, wybierz **Start** > **wszystkie programy** >  **programu Microsoft Visual Studio**  >  **Programu Microsoft Visual Studio Test Controller Configuration Tool**.

     **Konfigurowania kontrolera testu** zostanie wyświetlone okno dialogowe.

2. Wybierz użytkownika do użycia jako konto logowania usługi kontrolera testu.

    > [!NOTE]
    > Wartość null hasła nie są obsługiwane dla kont użytkowników.

4. (Opcjonalnie) Jeśli nie chcesz kontroler testu za pomocą środowiska laboratoryjnego, ale tylko do uruchamiania testów w programie Visual Studio, usuń zaznaczenie **zarejestrować się w kolekcji projektów zespołowych**.

5. (Opcjonalnie) Aby skonfigurować kontroler testu dla testów obciążenia, wybierz **Konfiguruj na potrzeby testowania obciążenia**. Następnie wpisz wystąpienia programu SQL Server w **wyników testów obciążenia tworzenie bazy danych w wystąpieniu programu SQL Server następujące**.

> [!NOTE]
> Aby rozwiązywanie informacji na temat kontrolerów testów więcej problemów, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Zarządzanie agentów po uruchomieniu testów z kontrolera testów

Po dodaniu ról dla aplikacji z ustawień testu dla programu Visual Studio można dodać właściwości agenta dla każdej z ról użytkownika. Określa, który test agentów są dostępne dla tej roli. Po uruchomieniu testów, używając ustawienia testu, kontrolera testu, który został wybrany do ustawień testu określa dostępność wymaganych agentów. Są to następujące sytuacje, które mogą wystąpić podczas zależy od dostępności agenta:

-   Nie ma agenta dostępnej dla roli, który należy uruchomić testy. Nie można uruchomić testy. Można wykonać jedną z następujących czynności, a następnie ponownie uruchom testy:

    -   Możesz poczekać agentowi staną się dostępne dla tej roli uruchomić testy.

    -   W przypadku wszystkich agentów, którzy są w trybie offline, które mogą być używane dla tej roli, można ponownie uruchomić agenta, aby była dostępna.

    -   Możesz dodać innego agenta z właściwościami poprawne agenta dla tej roli do kontrolera testu.

    -   Można zmienić właściwości agenta dla tej roli w ustawieniach testu, aby włączyć innych agentów, które chcesz użyć.

-   Nie ma agenta dostępnej dla jednego lub więcej ról, które uruchamianie adapterów danych diagnostycznych. Testy można uruchomić, ale nie można uruchomić adaptera danych diagnostycznych. Można uruchomić testy bez adaptera danych diagnostycznych, lub możesz wykonać jedną z następujących czynności i ponownie uruchomić testy:

    -   Możesz poczekać agentowi staną się dostępne dla tych ról.

    -   W przypadku wszystkich agentów, którzy są w trybie offline, które mogą być używane dla tej roli, musisz zmienić stan agenta online z **administrowania kontrolerem testów** na **testu** menu. Ponadto może być konieczne ponowne uruchomienie agenta, jeśli została ona odłączona od kontrolera.

    -   Upewnij się, że wszystkich agentów, które mogą wymagać dla tego uruchomienia testu nie zajęty uruchomionych testów. Można sprawdzić stan wszystkich agentów z **administrowania kontrolerem testów** na **testu** menu.

    -   Możesz dodać innego agenta z właściwościami poprawne agenta dla roli z kontrolerem testów.

    -   Można zmienić właściwości agenta dla roli w ustawieniach testu, aby włączyć innych agentów, które chcesz użyć.

## <a name="load-tests-from-delay-signed-assemblies"></a>Testy obciążenia z zestawów podpisywany z opóźnieniem

Test controller i agenci testowi może ładować tylko zestawy testów, które są zdecydowanie podpisanych zestawów lub zestawy nieoznaczone. Niektóre zestawy testowe opóźnienie zalogowano ponieważ muszą mieć dostęp do produkcji zestawów dla aplikacji. Jednak te zestawy są nie silnego podpisu, ponieważ są one tylko zestawy testowe, a nie są dystrybuowane. Nie można załadować tych zestawów, ponieważ są one, podpisywany z opóźnieniem, dlatego należy wyłączyć weryfikacja jednoznacznych nazw dla tych zestawów na wszystkich komputerach, na którym zestawu zostaną załadowane w tym komputerze kontrolera testów. Aby wyłączyć weryfikację podpisu z opóźnieniem, należy użyć sn.exe. Token klucza publicznego zestawu podpisywany z opóźnieniem, dla którego wnioskuje się do pominięcia weryfikacji silnej nazwy może być również konieczne zostanie uwzględniona.

Użyj Sn.exe (narzędzie Strong Name), aby wyłączyć weryfikację podpisu z opóźnieniem.

Weryfikacja silnej nazwy dla określonego zestawu, powoduje wyłączenie na komputerze, na którym uruchomiono polecenie. Można to zrobić tylko wtedy, gdy masz wystarczające uprawnienia.

Po zakończeniu uruchomienia testu, należy ponownie włączyć podpisywanie opóźnione weryfikacji za pomocą polecenia SN.exe.

Zalecanym sposobem wyłączenie i ponowne włączenie Weryfikacja podpisywania jest użycie poleceń SN.exe w skryptach. Można wyłączyć weryfikację w skrypcie Instalatora i ponownie włączyć weryfikację za pomocą skryptów czyszczenia.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)