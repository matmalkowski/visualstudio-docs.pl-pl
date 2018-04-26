---
title: Przypisywanie ról kontrolerowi testu i agentowi testowemu w celu automatycznego testowania w programie Visual Studio
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 1294083fa14bd71ca0d46aed481a963b8dfd39d1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Przypisywanie ról kontrolera testów i Agent testowy

W tym przewodniku pokazano, jak utworzyć i skonfigurować ustawienie testu używa kontrolera testów i agent testowy do dystrybucji testowania na kilku komputerach przy użyciu programu Visual Studio. Ponadto w tym przewodniku przedstawiono sposób dodawania dane diagnostyczne i dane karty Ustawienia testu.

W tym przewodniku będzie wykonać następujące zadania:

-   Tworzenie ustawień testu.

-   Przypisywanie ról do kontrolera i testowania agentów testowych.

-   Przypisanie dane diagnostyczne i dane karty Ustawienia testu.

## <a name="prerequisites"></a>Wymagania wstępne

-   Utwórz testy jednostkowe ani kodowane testy interfejsu użytkownika, aby uruchomić z ustawieniami testu.

-   Zainstaluj agentów testowych kontrolera i testowania. Aby uzyskać informacje o sposobie instalowania kontrolera testów i agenci testowi, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Aby utworzyć i skonfigurować ustawienia testu

1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **elementy rozwiązania** wskaż **Dodaj**, a następnie wybierz pozycję **nowy element**.

     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.

2.  W **zainstalowane szablony** okienku wybierz **ustawień testu**.

3.  W **nazwa** wpisz **TestSettingDistributedTestWalkthrough**.

4.  Wybierz **dodać**.

     Nowy test TestSettingDistributedTestWalkthrough.testsettings plik zostanie wyświetlony w Eksploratorze rozwiązań w obszarze **elementy rozwiązania** folderu.

     **Ustawień testu** zostanie wyświetlone okno dialogowe. **Ogólne** strony jest zaznaczone.

     Teraz możesz edytować i zapisać wartości ustawień testu.

    > [!NOTE]
    > Każdego ustawienia testu, tworzonych jest wymienione jako rozwiązaniem dla **wybierz aktywne ustawienia testu** i **edytowanie ustawień testu** opcje na **Test** menu.

5.  W obszarze **nazwa**, wpisz nazwę dla ustawienia testu.

6.  W obszarze **opis**, typ **ustawień testów rozproszonych**.

7.  Pozostaw **domyślny schemat nazewnictwa** wybrane.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Aby przypisać role do testu kontrolera i agenci testowi

1.  Wybierz **ról**.

     **Ról** zostanie wyświetlona strona.

2.  Aby uruchomić zdalnie test, należy użyć **wykonywania metoda testowa** listy rozwijanej i wybierz **zdalne wykonywanie kodu**.

3.  W **kontrolera** listy rozwijanej liście, wpisz nazwę komputera [kontroler testu](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Jeśli po raz pierwszy, dodawania kontrolera, nie ma żadnych kontrolerów wymienione na liście rozwijanej. Lista zostanie wypełniona przez poprzednie kontrolery, określonych w innych ustawień testu.

4.  W obszarze **ról**, wybierz **Dodaj**.

5.  W wyróżnionych wierszu w obszarze **nazwa** wpisz **rozproszonego testu**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Aby przypisać adaptera danych diagnostycznych i danych do ustawienia testu

1.  Wybierz **danych i informacji diagnostycznych**.

     **Danych i informacji diagnostycznych** zostanie wyświetlona strona.

2.  W obszarze **roli**, upewnij się, że **rozproszonego testu** wybrać rolę.

3.  W obszarze **dane i Diagnostyka w przypadku roli wybierz**, wybierz pozycję **IntelliTrace** i **informacje o systemie** kart.

     Aby uzyskać informacji o tych kart i innych kart, które można używać w środowisku testowym, zobacz [Konfigurowanie testów jednostkowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4.  Wybierz **hostów**.

5.  (Opcjonalnie) Jeśli komputer działa w 64-bitowej wersji systemu Microsoft Windows i kompilowane, za pomocą testu **Any CPU** konfiguracji, użyj **Uruchamianie testu w procesie 32-bitowy lub 64-bitowym** listy rozwijanej i wybierz pozycję **Uruchom testy w procesie 64-bitowym na 64-bitowym komputerze**.

    > [!TIP]
    > Maksymalna elastyczność należy skompilować projektów testów z **Any CPU** konfiguracji. Następnie możesz uruchomić na zarówno 32-bitowe i 64-bitowych agentów. Nie ma żadnych dodatkowych zalet kompilowanie projektów testów z **64-bitowych** konfiguracji.

6.  Aby zapisać nowe ustawienia testu, wybierz **Zastosuj**.

7.  Wybierz **Zamknij**.

8.  W Test menu wybierz **wybierz aktywne ustawienia testu** , a następnie wybierz **TestSettingDistributedTestWalkthrough.testsettings**.

9. Uruchomienie testu w zwykły sposób.

     Gdy kontroler testów przetwarza testy jednostkowe i kodowane testy interfejsu użytkownika, kontrolera testu testy są podzielone na grupy 100 i wysyła je na maszynie agenta testowego. Na przykład jeśli masz 250 testów jednostkowych i trzy agenci testowi, testy jednostkowe pierwszych 100 zostaną wysłane do agent1, testy jednostkowe następne 100 zostaną wysłane do agent2 i pozostałe testy jednostkowe 50 zostaną wysłane do agent3.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)