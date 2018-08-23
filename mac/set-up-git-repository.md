---
title: Konfigurowanie repozytorium Git
description: Przy użyciu narzędzia Git i Subversion w programie Visual Studio dla komputerów Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: 6898fb890828a01f286f321f14de3999fdf1ca64
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42624265"
---
# <a name="setting-up-a-git-repository"></a>Konfigurowanie repozytorium Git

Git to Rozproszony system kontroli wersji umożliwiający zespoły mogą pracować na tym samym dokumentach jednocześnie. Oznacza to, jest jednym serwerze, który zawiera wszystkie pliki, ale zawsze wtedy, gdy repozytorium jest wyewidencjonowany z tego źródła centralnej, całe repozytorium został sklonowany lokalnie na komputerze.

Istnieje wiele hostów zdalnych, które umożliwiają pracę przy użyciu narzędzia Git do kontroli wersji, jednak najczęściej host jest GitHub. W poniższym przykładzie użyto hosta usługi GitHub, ale można użyć dowolnego hosta usługi Git do kontroli wersji w programie Visual Studio dla komputerów Mac.

Jeśli chcesz korzystać z usługi GitHub, upewnij się, że masz konto utworzone i skonfigurowane przed wykonaniem kroków opisanych w tym artykule. 

## <a name="creating-a-remote-repo-on-github"></a>Tworzenie repozytorium zdalnego w serwisie GitHub

W poniższym przykładzie użyto hosta usługi GitHub, ale można użyć dowolnego hosta usługi Git do kontroli wersji w programie Visual Studio dla komputerów Mac.

Aby skonfigurować repozytorium Git, wykonaj następujące czynności:

1. Utwórz nowe repozytorium Git w github.com:

    ![Tworzenie nowego repozytorium git](media/version-control-git1-sml.png)

2. Ustaw nazwę repozytorium, opis i ochrony prywatności. Czy **nie** Zainicjuj repozytorium. Ustaw pliki .gitignore i licencji na Brak:

    ![Szczegóły zestawu z repozytorium git](media/version-control-git2.png)

3. Następnej strony daje możliwość wyświetlenia, a następnie skopiuj adres HTTPS lub protokołu SSH do repozytorium, które zostały utworzone:

    ![Wyświetl i skopiuj adres](media/version-control-git3.png)

  Konieczne będzie z adresu HTTPS do punktu, Visual Studio dla komputerów Mac w tym repozytorium.


## <a name="publishing-an-existing-project"></a>Publikowanie istniejący projekt

Jeśli masz istniejący projekt, który _nie_ już w kontroli wersji, wykonaj następujące kroki, aby skonfigurować w usłudze Git:

4.  Wybierz nazwę rozwiązania z konsoli rozwiązania w programie Visual Studio dla komputerów Mac. 

5. Na pasku Menu wybierz **kontroli wersji > Publikuj w kontroli wersji...** Aby wyświetlić **wybierz repozytorium** okno dialogowe:

    ![Rozpocznij wyewidencjonowania w programie Visual Studio dla komputerów Mac](media/version-control-git4-sml.png)

    Jeśli ten element menu pojawia się wyszarzonym w menu, upewnij się, że wybrana nazwa rozwiązania.  

6. Wybierz **zarejestrowane repozytoria** kartę, a następnie naciśnij klawisz **Dodaj** przycisku:

    ![](media/version-control-git5.png)

7. Wprowadź nazwę repozytorium, jak chcesz, aby wyświetlić lokalnie, a następnie wklej w adresie URL w kroku #3. Konfiguracja repozytorium okna dialogowego powinny wyglądać podobnie do następującego. Naciśnij przycisk OK: 

    ![Wprowadź szczegóły git w oknie dialogowym](media/version-control-git6.png)

    Należy pamiętać, że istnieje również możliwość łączenia do usługi Git za pomocą protokołu SSH.

8. Próby publikowanie aplikacji w usłudze Git, wybierz repozytorium i upewnij się, że oba **Nazwa modułu** i **komunikat** odbywa się pól tekstowych:

    ![Próba opublikowania projektu do usługi git](media/version-control-git7.png)

9. Kliknij przycisk **OK**, a następnie **Publikuj** z okna dialogowego alertu.

10. Jeśli użytkownik jeszcze nie wprowadzono poświadczeń Git w programie Visual Studio dla Preferencje systemu Mac, należy wprowadzić je teraz. Najpierw musisz utworzyć Token dostępu, który jest używany zamiast hasła. Jeśli token dostępu nie została utworzona, wykonaj kroki w Git [Token dostępu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) dokumentacji.

11. Wprowadź nazwę użytkownika i osobisty Token dostępu i naciśnij klawisz **OK**:

    ![Wprowadź nazwę użytkownika i hasło dla usługi git](media/version-control-git9-sml.png)

12. Po kilku sekundach rozwiązania powinny być publikowane z jego początkowe zatwierdzenie. Upewnij się, że został opublikowany, przechodząc elementu menu kontroli wersji, który powinien zostać wypełniony wiele opcji: 

    ![Menu Kontrola wersji](media/version-control-git10.png)

13. Po rozpoczęciu wprowadzania dodatkowych zmian, wybierz **wypychanie zmian...**  wypychania zmian do **zdalnego** repozytorium. Zezwalaj na wszystkich odpowiednich użytkowników go wyświetlić w witrynie github.com: 

    ![Wypchnij zmiany do repozytorium zdalnego](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publikowanie nowego projektu

Okno dialogowe nowego projektu może służyć do opublikowania nowego projektu przy użyciu narzędzia git. Aby ją włączyć, wybierz **za pomocą narzędzia git do kontroli wersji.** Zaznacz pole wyboru, jak pokazano na poniższym zrzucie ekranu. Spowoduje to zainicjowanie repozytorium i Dodaj plik gitignore opcjonalne:

![Wypchnij zmiany do repozytorium zdalnego](media/version-control-git12.png)

## <a name="checkout-an-existing-repository"></a>Wyewidencjonuj istniejącego repozytorium

Jest bardzo prawdopodobne, że musisz pracować z repozytorium GitHub, która istnieje tylko w lokalizacji zdalnej, nie na komputerze lokalnym. Program Visual Studio for Mac umożliwia wyewidencjonowanie tego repozytorium szybko. Wykonaj poniższe kroki, aby sklonować ten projekt do komputera:

1. Na pasku Menu wybierz **kontroli wersji > wyewidencjonowanie...** :

2. Spowoduje to wyświetlenie **nawiązywanie połączenia z repozytorium** karty:

    ![Połącz kartę repozytorium ze szczegółami podanymi](media/version-control-git13.png)

3. Na stronie GitHub repozytorium zdalnego, naciśnij klawisz **Klonuj lub Pobierz** przycisk i skopiuj adres URL podany:

    ![wyświetlany adres url usługi github](media/version-control-git14.png)

4. Zastąp cały tekst w **adresu URL** pola wpisu w **nawiązywanie połączenia z repozytorium** kartę. Spowoduje to wypełnienie większości innych pól na tej karcie, jak pokazano na ilustracji w kroku #2.

5. Wprowadź katalog, który chcesz sklonować repozytorium do, a następnie naciśnij klawisz **wyewidencjonowania**.

> [!NOTE]
Mogą wystąpić problemy, jeśli repozytorium jest ponad 4GB.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli masz problemy z inicjowanie projektu za pomocą puste repozytorium zdalnego, możesz spróbować następujące czynności:

- Przejdź do folderu rozwiązania.
- Naciśnij klawisz `Command + Shift + . ` aby pokazać ukryte pliki i foldery.
- W przypadku **.git** folder, usuń go.
- W przypadku **gitignore** , usuń go.
- Naciśnij klawisz `Command + Shift + . ` ukryć pliki i foldery.
- Otwórz swoje rozwiązanie w programie VS dla komputerów Mac.
- W konsoli rozwiązania wybierz węzeł rozwiązania.
- Przejdź do menu kontroli wersji, a następnie wybierz **publikowania w systemie kontroli wersji**.
- Wykonaj kroki samouczka powyżej, zaczynając od kroku 6.