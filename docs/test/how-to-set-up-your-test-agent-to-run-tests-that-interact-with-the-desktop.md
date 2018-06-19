---
title: Konfigurowanie agenta testowego programu Visual Studio, aby uruchomić testy wchodzące w interakcje z pulpitem
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d1b6655dd493a2ac62ba333f3858b299ee398f8d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974809"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Porady: konfigurowanie agenta testowego do przeprowadzania testów w interakcji z pulpitem

Jeśli chcesz uruchomić zautomatyzowanych testów w interakcji z pulpitem, należy skonfigurować agenta do uruchamiania jako proces zamiast usługi. Na przykład jeśli chcesz uruchomić zdalnie przy użyciu kontrolera testów i agenta testowego kodowanego testu interfejsu użytkownika lub chcesz uruchomić test i przechwytywania nagrania po uruchomieniu wideo, należy skonfigurować agenta do uruchamiania jako proces. Podczas przypisywania agentów do ról w ustawieniach testu przy użyciu programu Visual Studio, lub możesz przypisać agentów do ról w środowisku przy użyciu narzędzia Microsoft Test Manager, należy zmienić zestaw dla wszystkich agentów przypisane do ról, które mają wchodzić w interakcje z pulpitem.

> [!WARNING]
> Jeśli program Microsoft Test Manager umożliwia konfigurowanie środowiska laboratoryjnego, instaluje agenta testowego. W kreatorze tworzenia środowiska można określić chcesz skonfigurować jedną z ról do uruchomienia kodowanych testów interfejsu użytkownika.

> [!IMPORTANT]
> Komputera, na którym jest uruchomiony agent, na którym chcesz uruchomić kodowane testy interfejsu użytkownika nie może być zablokowany lub ma aktywny wygaszacz ekranu.

Jeśli używasz kodowane testy interfejsu użytkownika, które Uruchom przeglądarkę, konto usługi agenta testowego służy do uruchomienia tej przeglądarki. To konto usługi musi być taka sama jak konto użytkownika, który jest aktywnego użytkownika na tym komputerze. Jeśli nie jest tym samym kontem użytkownika, przeglądarka nie zostanie uruchomiona.

> [!IMPORTANT]
> Jeśli używasz kodowanego testu interfejsu użytkownika, który otwiera przeglądarkę jako część definicji kompilacji konta usługi dla usługi kompilacji służy do uruchomienia tej przeglądarki. To konto usługi musi być taka sama jak konto użytkownika, który jest aktywnego użytkownika na tym komputerze. Jeśli nie jest tym samym kontem użytkownika, przeglądarka nie zostanie uruchomiona.

 Użyj poniższej procedury do skonfigurowania wszystkich agentów, które są przypisane do roli, który wykonuje zadanie, które wymaga interakcji z pulpitem.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Aby skonfigurować agenta do uruchamiania jako proces

1.  Aby skonfigurować agenta testowego zostały zainstalowane do uruchamiania jako proces, przejdź do **Start**, **wszystkie programy**, **programu Microsoft Visual Studio**, **programu Microsoft Visual Studio Testowanie narzędzie konfiguracji agenta**.

     **Skonfigurować agenta testowego** zostanie wyświetlone okno dialogowe.

2.  Aby wyświetlić stronę, aby wybrać do uruchamiania jako proces, wybierz **opcji przebiegu**.

     Zostanie wyświetlona strona, który umożliwia wybranie do uruchamiania jako proces lub usługi agenta.

3.  Wybierz **procesu interaktywnego**. Będzie można uruchomić agenta testowego jako proces zamiast usługi. Wybierz **dalej**.

     Teraz możesz wprowadzić szczegóły użytkownika do użycia podczas uruchamiania agenta testowego jako proces i inne opcje.

    > [!NOTE]
    > Użytkownik, który można dodać do rozpoczęcia procesu również muszą zostać dodane jako członek grupy TeamTestAgentService na komputerze kontrolera testów dla tego agenta. W przypadku tego użytkownika bieżącego użytkownika, po dodaniu tego użytkownika na komputerze kontrolera testów, musisz wylogować lub ponownego uruchamiania tego komputera.

4.  Wpisz nazwę w **nazwy użytkownika**.

5.  Wpisz hasło w **hasło**.

     **Informacje o koncie użytkownika ważne:**

    -   Wartość null hasła nie są obsługiwane dla kont użytkowników.

    -   Jeśli chcesz użyć IntelliTrace lub danych emulacji sieci i diagnostycznych karty, konto użytkownika musi być członkiem grupy Administratorzy. Jeśli urządzenia, na którym jest uruchomiony agent testowy jest uruchomiony system operacyjny, który ma najmniej uprzywilejowane konto użytkownika, należy również uruchomić jako administrator (z podwyższonym poziomem uprawnień). Jeśli nazwa użytkownika agenta nie jest w usłudze agenta spróbuje dodać ją, co wymaga uprawnień na kontrolerze testów.

    -   Użytkownik próbuje użyć kontrolera testów musi należeć do kont użytkowników z kontrolerem testów lub nie będą mogli uruchamiać testy dla kontrolera.

6.  Aby upewnić się, że w komputerze agenta testowego można uruchomić testy po jego ponownym uruchomieniu, należy skonfigurować komputer do automatycznego logowania jako użytkownika agenta testowego. Wybierz **automatyczne logowanie**. To będzie przechowywać nazwy użytkownika i hasła w postaci zaszyfrowanej w rejestrze.

    > [!NOTE]
    > Po nawiązaniu połączenia ze środowiskiem laboratorium, za pomocą pulpitu zdalnego lub połączenia gościa, mogą pojawić się często, nieoczekiwany rozłącza. Jedną z możliwych przyczyn utraty połączenia jest, że maszyna jest skonfigurowana do automatycznego logowania do sieci.

7.  Aby upewnić się, że wygaszacz ekranu jest wyłączona, ponieważ może to zakłócać żadnych testów automatycznych, które musi współdziałać z pulpitem, wybierz **jest wyłączona, upewnij się, że wygaszacz ekranu**.

    > [!WARNING]
    > Jeśli automatyczne logowanie lub wyłączenie wygaszacza ekranu są zagrożenia bezpieczeństwa. Po włączeniu automatycznej dziennika na, można włączyć innych użytkowników, aby uruchomić ten komputer i aby móc korzystać z konta, który loguje się automatycznie. Wyłączenie wygaszacza ekranu komputera nie może być wyświetlany monit dla użytkownika zalogować się do odblokowania komputera. Dzięki temu każda osoba, która dostęp do komputera, jeśli mają dostęp fizyczny do komputera. Po włączeniu tych funkcji na komputerze, należy upewnić się, że te komputery znajdują się fizycznie zabezpieczonej. Na przykład te komputery znajdują się w fizycznie zabezpieczonej laboratorium. Jeśli wyczyścisz **jest wyłączona, upewnij się, że wygaszacz ekranu**, nie obsługuje wygaszacz ekranu.

     Aby zmienić agenta wstecz do uruchamiania jako usługa, można użyć tego narzędzia i wybierz **usługi**.

8.  Aby zastosować zmiany, wybierz **Zastosuj ustawienia**.

     A **Podsumowanie konfiguracji** wyświetlone okno dialogowe wyświetla stan poszczególnych kroków, aby skonfigurować agenta testowego.

9. Aby zamknąć **Podsumowanie konfiguracji** oknie dialogowym wybierz **zamknąć**. Następnie wybierz pozycję **zamknąć** ponownie, aby zamknąć narzędzie konfiguracji agenta testowego.

    > [!NOTE]
    > Brak ikony w obszarze powiadomień, który jest uruchomiony na komputerze agenta testowego, w którym jest uruchomiona jako proces. Wskazuje ono stan agenta testowego. Można uruchomić, zatrzymać lub ponownie uruchomić agenta, jeśli została uruchomiona jako proces, za pomocą tego narzędzia. Aby uruchomić agenta testowego jako proces, jeśli nie jest uruchomiona, wybierz **Start**, **wszystkie programy**, **programu Microsoft Visual Studio**, **Microsoft Visual Studio Test Agent**.

     Jeżeli kontrolera testu dla tego agenta testowego jest zarejestrowany w programie Team Foundation Server, stan agenta testowego, w którym jest uruchomiony jako proces interaktywny jest wyświetlany w **kontrolerów** wyświetlić w **Centrum laboratoryjnego**dla programu Microsoft Test Manager. Znajduje się on z poprzednim symbol gwiazdki oznaczający, że jest on uruchomiony jako proces interaktywny. Aby ponownie uruchomić agenta testowego należy użyć narzędzia, które działają na komputerze agenta testowego i nie **kontrolerów** widoku.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)