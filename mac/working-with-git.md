---
title: Praca z usługą Git
description: Przy użyciu narzędzia Git w programie Visual Studio dla komputerów Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.openlocfilehash: 8b263ee21c87acd665e22d39b7eb9c46172d9548
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="working-with-git"></a>Praca z usługą Git

Git to system kontroli wersji rozproszonej, który umożliwia zespołom jednocześnie pracować na tym samym dokumentów. Oznacza to, że znajduje się centralny serwer zawierający wszystkie pliki, ale po repozytorium jest wyewidencjonowany z tego źródła centralnej, całe repozytorium został sklonowany na komputerze lokalnym.

W poniższych rozdziałach zastosuje jak Git może służyć do kontroli wersji w programie Visual Studio dla komputerów Mac.

## <a name="git-version-control-menu"></a>Menu kontroli wersji Git

Na poniższym obrazie przedstawiono opcje podał przez element menu kontroli wersji programu Visual Studio dla komputerów Mac:

![Element menu kontroli wersji](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Wypychania i ściągania 

Wypychanie i ściąganie są dwa najczęściej używane akcje w ramach Git. Aby zsynchronizować zmiany, które inne osoby do repozytorium zdalnego zostały wprowadzone, należy najpierw **ściągnięcia** stamtąd. Odbywa się w programie Visual Studio dla komputerów Mac, wybierając **kontrolą wersji > rozwiązanie aktualizacji**.

Po aktualizacji plików, sprawdzone i zatwierdzone ich należy następnie **Push** ich do zdalnego repozytorium, aby inni mogli uzyskać dostępu do zmiany. Odbywa się w programie Visual Studio dla komputerów Mac, wybierając **kontrolą wersji > Push zmiany**. To będzie wyświetlane okno dialogowe wypychania, który umożliwia przeglądanie zatwierdzone zmiany i wybierz gałąź do:

![Gałąź, aby przekazać do wyświetla okno dialogowe](media/version-control-gitPush.png)

Możesz również Zatwierdź i Wypchnij zmiany w tym samym czasie, za pomocą okna dialogowego zatwierdzenia:

![Opcja przedstawiająca sposób Zatwierdź i Wypchnij w tym samym czasie.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Blame dziennika i scalania

W dolnej części okna istnieją pięć kart wyświetlane, jak przedstawiono poniżej:

![Wersja formantu karty](media/version-control-gitTabs.png)

Umożliwiają one następujące akcje:

* **Źródło** -Wyświetla pliku kodu źródłowego.
* **Zmiany** -wyświetla zmiany w kodzie między Twoim lokalnym plikiem a plikiem podstawowym. Można także porównać różne wersje pliku z różnych wartości skrótu:

    ![Karta zmiany](media/version-control-gitChange.png)

* **Blame** -Wyświetla nazwę użytkownika skojarzonego z każdej sekcji kodu.
* **Dziennik** -Wyświetla wszystkie zatwierdzeń, godziny, dat, wiadomości i użytkowników, którzy są zobowiązani do pliku:

    ![Karta dziennik](media/version-control-gitLog.png)

* **Scalanie** — może być używany, jeśli występuje konflikt scalania, gdy zatwierdzania pracy. Przedstawia on wizualną reprezentację zmiany wprowadzone przez Ciebie i inne deweloperów, umożliwiając prawidłowo łączyć zarówno fragmentów kodu. 

## <a name="switching-branches"></a>Przełączania gałęzi 

Domyślnie jest nazywany pierwszej gałęzi utworzone w repozytorium **wzorca** gałęzi. Nie ma technicznie nic różnic między głównej gałęzi i inne, ale głównej gałęzi jest ten, który jest najczęściej traktować w zespoły deweloperów jako gałąź "na żywo" lub "produkcja".

Niezależnie od wiersza rozwoju mogą być tworzone przez Rozgałęzianie poza główny (lub innej gałęzi, istotnego dla badania). Zapewnia to nowej wersji głównej gałęzi w punkcie w czasie, co pozwala na projektowanie niezależnie od co to jest "live". Za pomocą gałęzi w ten sposób jest często używany do funkcji w rozwoju oprogramowania

Użytkownicy mogą tworzyć tyle gałęzie zgodnie z ich jak każdego repozytorium, ale zaleca się, że po zakończeniu ich za pomocą gałęzi, ich usunięcia go, aby zachować repozytorium organizowane.

Oddziały są wyświetlane w programie Visual Studio dla komputerów Mac, przechodząc do **kontrolą wersji > Zarządzanie gałęzi i element zdalny...** :

![Widok gałęzi](media/version-control-gitBranch2.png)

Przełącz się do innego oddziału firmy, wybierając go na liście i naciskając klawisz **przełączyć do gałęzi** przycisku.

Aby utworzyć nowy Wybierz gałąź **nowy** przycisk w oknie dialogowym konfiguracji repozytorium Git. Wprowadź nową nazwę gałęzi:

![Tworzenie nowej gałęzi](media/version-control-gitBranch.png)

Można również ustawić gałęzi zdalnej z _śledzenia_ gałęzi. Przeczytaj więcej na temat śledzenia gałęzie w [dokumentacji Git](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Zobacz bieżącej gałęzi w konsoli do rozwiązania, obok nazwy projektu:

 ![Bieżąca gałąź wyświetlane w konsoli rozwiązania](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Przeglądu i zatwierdzania 

Przeglądanie zmian w plikach Użyj zmiany, winy, dziennika i scal kart na każdy dokument przedstawione wcześniej w tym temacie.

Przejrzyj wszystkie zmiany w projekcie, przechodząc do **kontrolą wersji > rozwiązanie przeglądu i zatwierdzania** element menu:

![Przejrzyj widoku kodu](media/version-control-gitReviewCommit.png)

Umożliwia wyświetlanie wszystkich zmian w każdym pliku projektu z możliwością przywrócenia, Utwórz poprawkę lub czy zatwierdzić.

Można przekazać pliku do zdalnego repozytorium, naciśnij klawisz **zatwierdzenia...** , wpisz wiadomość, zatwierdzenia i Potwierdź u przycisk Zatwierdź:

![Zatwierdzanie pliku](media/version-control-gitCommit.png)

Po popełnienie zmiany Wypchnij je do zdalnego repozytorium, aby inni użytkownicy mogli je widzieć.