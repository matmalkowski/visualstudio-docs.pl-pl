---
title: Praca z samouczka Python kroku 6, Praca z usługą Git
description: Krok 6 wskazówki podstawowe języka Python w programie Visual Studio, obejmujące funkcje związane z Git programu Visual Studio.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: dc9128a28ea0fd007a97b20331f15227b86d46f7
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056498"
---
# <a name="step-6-work-with-git"></a>Krok 6: Praca z usługą Git

**Poprzedni krok: [instalowanie pakietów i zarządzanie środowiskiem Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Program Visual Studio udostępnia bezpośrednia Integracja z lokalnym repozytoriów Git i repozytoria zdalne na usługi, takie jak GitHub i Visual Studio Team Services. Integracja obejmuje klonowanie repozytorium, zatwierdzania zmian i zarządzania gałęzi.

Ten artykuł zawiera omówienie tworzenia lokalnego repozytorium Git dla istniejącego projektu i zapoznawanie się z niektórych funkcji związanych z Git programu Visual Studio.

1. Z projektem Otwórz w programie Visual Studio, takich jak projekt z [poprzedniego kroku](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Dodaj rozwiązanie do kontroli źródła**. Program Visual Studio tworzy lokalne repozytorium Git, który zawiera kod Twojego projektu.

1. Gdy Visual Studio wykryje, że projekt jest zarządzana w formantach Git związane z repozytorium Git są wyświetlane na prawym dolnym rogu okna programu Visual Studio. Pokaż formanty oczekujących zatwierdzeń, zmiany nazwy repozytorium i oddziału. Umieść kursor nad formantów, aby wyświetlić dodatkowe informacje.

    ![Dodatkowe informacje są wyświetlane po aktywowaniu Git formantu w oknie programu Visual Studio](media/working-with-git-01.png)

1. Podczas tworzenia nowego repozytorium lub wybierz jedno z formantów Git, Visual Studio otworzy **Team Explorer** okna. (W dowolnym momencie można otworzyć okna **Widok > Team Explorer** polecenia menu.) Okno ma trzy główne okienka, które przełączać za pomocą listy rozwijanej na **Team Explorer** nagłówka. **Synchronizacji** okienko, które udostępnia operacje publikowania, pojawia się również, po wybraniu formantu wypychania (się ikonę strzałki):

    ![Program Team Explorer w programie Visual Studio po utworzeniu lokalnego repozytorium](media/working-with-git-02.png)

1. Wybierz **zmiany** (lub kontrolki Git z ołówka) do przeglądania niezatwierdzone zmiany i zatwierdzić je, jeśli to konieczne.

    ![Program Team Explorer w programie Visual Studio przedstawiający niezatwierdzone zmiany](media/working-with-git-03.png)

    Kliknij dwukrotnie plik w **zmiany** listy, aby otworzyć widok różnicowego dla tego pliku:

    ![Widok porównania dla zmian w pliku](media/working-with-git-05.png)

1. Wybierz **gałęzie** (lub formant Git o nazwie gałęzi) do badania gałęzie i wykonywanie operacji scalania i rebase:

    ![Program Team Explorer w programie Visual Studio przedstawiający gałęzi](media/working-with-git-04.png)

1. Wybranie kontrolki Git o nazwie repozytorium ("CosineWave" w poprzedniej ilustracji), **Team Explorer** pokazuje **Connect** interfejsu, z którego można szybko przełączyć się do innego repozytorium całkowicie.

1. Korzystając z lokalnego repozytorium, zatwierdzone zmiany przejdź bezpośrednio do repozytorium. Jeśli korzystasz z repozytorium zdalnym nagłówek listy rozwijanej wybierz **Team Explorer**, wybierz **synchronizacji** Aby przełączyć się do **synchronizacji** sekcji i pracy z Brak przedstawionych ściągania i pobieranie poleceń.

## <a name="go-deeper"></a>Przejść głębiej

Krótki przewodnik tworzenia projektu ze zdalnego repozytorium Git, zobacz [Szybki Start: Klonuj repozytorium kodu języka Python w programie Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

Bardziej kompleksowy samouczek obsługi konflikty scalania, przeglądu kodu z żądań ściągnięcia, zmienianie bazy i pobrania tę zmiany między oddziałów, w tym temacie [wprowadzenie do korzystania z usługi Git i VSTS](/vsts/git/gitquickstart?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json&view=vsts&tabs=visual-studio).

## <a name="tutorial-review"></a>Przejrzyj samouczek

Gratulujemy wykonanie kroków tego samouczka na Python w programie Visual Studio. W tym samouczku znasz jak:

- Tworzenie projektów i wyświetlanie zawartości projektu.
- Edytor kodu i uruchamianie projektu.
- Okno interaktywne umożliwia tworzenie nowego kodu i łatwo skopiować ten kod do edytora.
- Uruchom program ukończone w debugerze programu Visual Studio.
- Zainstaluj pakiety i zarządzanie nimi środowiska Python
- Praca z kodem w repozytorium Git

W tym miejscu zapoznaj się z pojęciami i porad wskazówek, w tym następujące artykuły:

- [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilowanie](profiling-python-code-in-visual-studio.md)
- [Testowanie jednostek](unit-testing-python-in-visual-studio.md)
