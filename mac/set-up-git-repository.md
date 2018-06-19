---
title: Konfigurowanie repozytorium Git
description: Przy użyciu usługi Git i Podwersją w programie Visual Studio dla komputerów Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: c30659ad3fecd3f33b5e072b0c42d958d7eb0665
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33884341"
---
# <a name="setting-up-a-git-repository"></a>Konfigurowanie repozytorium Git

Git to system kontroli wersji rozproszonej, który umożliwia zespołom jednocześnie pracować na tym samym dokumentów. Oznacza to, istnieje pojedynczy serwer, który zawiera wszystkie pliki, ale zawsze, gdy repozytorium jest wyewidencjonowany z tego źródła centralnej, całe repozytorium został sklonowany lokalnie na komputerze.

Istnieje wiele hostów zdalnych, które umożliwiają pracę z usługą Git kontroli wersji, jednak najczęściej hosta jest GitHub. W poniższym przykładzie użyto hosta GitHub, ale można użyć dowolnego hosta Git kontroli wersji w programie Visual Studio dla komputerów Mac.

Jeśli chcesz używać usługi GitHub, upewnij się, że masz konto utworzone i skonfigurowane przed wykonaniem kroków w tym artykule. 

## <a name="creating-a-remote-repo-on-github"></a>Tworzenie repozytorium zdalnego w serwisie GitHub

W poniższym przykładzie użyto hosta GitHub, ale można użyć dowolnego hosta Git kontroli wersji w programie Visual Studio dla komputerów Mac.

Aby skonfigurować repozytorium Git, wykonaj następujące czynności:

1. Tworzenie nowego repozytorium Git w witrynie github.com:

    ![Tworzenie nowego repozytorium git](media/version-control-git1-sml.png)

2. Ustaw nazwę repozytorium, opis i ochrony prywatności. Czy **nie** zainicjować repozytorium. Ustaw .gitignore i licencji na Brak:

    ![Szczegóły zestawu z repozytorium git](media/version-control-git2.png)

3. Następnej strony daje możliwość wyświetlenia i skopiuj adres HTTPS lub SSH do repozytorium, które zostały utworzone:

    ![Wyświetlanie i kopiowanie adresu](media/version-control-git3.png)

  Adres HTTPS do punktu Visual Studio dla komputerów Mac należy do tego repozytorium.


## <a name="publishing-an-existing-project"></a>Publikowanie istniejącego projektu

Jeśli masz istniejący projekt, który _nie jest_ już w kontroli wersji, wykonaj następujące kroki, aby skonfigurować ją w usłudze Git:

4.  Wybierz nazwę rozwiązania z konsoli do rozwiązania w programie Visual Studio dla komputerów Mac. 

5. Na pasku Menu wybierz **kontrolą wersji > Publikuj w kontroli wersji...** Aby wyświetlić **wybierz repozytorium** okna dialogowego:

    ![Uruchom wyewidencjonowania w programie Visual Studio dla komputerów Mac](media/version-control-git4-sml.png)

    Jeśli ten element menu zostanie wyświetlone szarym w menu, upewnij się, że wybrana nazwa rozwiązania.  

6. Wybierz **zarejestrowany repozytoria** kartę i naciśnij klawisz **Dodaj** przycisk:

    ![](media/version-control-git5.png)

7. Wprowadź nazwę repozytorium, ponieważ chcesz, aby wyświetlić lokalnie, a następnie wklej w adresie URL w kroku #3. Twoje okno dialogowe konfiguracji repozytorium powinien wyglądać podobnie do następującego. Naciśnij przycisk OK: 

    ![Wprowadź szczegóły git w oknie dialogowym](media/version-control-git6.png)

    Należy pamiętać, że istnieje również możliwość użycia SSH do nawiązania połączenia Git.

8. Próba do publikowania aplikacji Git, wybierz repozytorium, a następnie upewnij się, że zarówno **nazwy modułu** i **komunikat** pól tekstowych zostały zakończone:

    ![Próba opublikować projektu git](media/version-control-git7.png)

9. Kliknij przycisk **OK**, a następnie **publikowania** z okna dialogowego alertu.

10. Jeśli nie zostały już wprowadzone poświadczenia Git w programie Visual Studio dla Preferencje systemu Mac, wprowadź je teraz. Najpierw należy utworzyć Token dostępu, który jest używany zamiast hasła. Jeśli nie utworzono token dostępu, postępuj zgodnie z instrukcjami Git [Token dostępu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) dokumentacji.

11. Wprowadź nazwę użytkownika i osobisty Token dostępu i naciśnij klawisz **OK**:

    ![Wprowadź nazwę użytkownika i hasło dla git](media/version-control-git9-sml.png)

12. Po kilku sekundach rozwiązania powinny być publikowane z jego zatwierdzeniem początkowej. Upewnij się, że została opublikowana przez element menu kontroli wersji, który teraz powinny zostać wypełnione wiele opcji przeglądania: 

    ![Menu kontroli wersji](media/version-control-git10.png)

13. Po uruchomieniu wprowadzić dodatkowe zmiany, wybierz **Push zmian...**  aby wypchnąć zmiany do **zdalnego** repozytorium. Pozwoli to wszystkich odpowiednich użytkowników go wyświetlić w witrynie github.com: 

    ![Wypchnij zmiany do repozytorium zdalnego](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publikowanie nowego projektu

Okno dialogowe nowego projektu może być używana do publikowania nowego projektu przy użyciu narzędzia git. Aby go włączyć, wybierz **Użyj kontroli wersji git.** pole wyboru, jak pokazano na poniższym zrzucie ekranu. Spowoduje to zainicjować Twojego repozytorium i Dodaj plik .gitignore opcjonalne:

![Wypchnij zmiany do repozytorium zdalnego](media/version-control-git12.png)

## <a name="checkout-an-existing-repository"></a>Wyewidencjonowanie istniejące repozytorium

Jest bardzo prawdopodobne, że będziesz mieć do pracy z repozytorium GitHub, że istnieje tylko w zdalnej, nie na komputerze lokalnym. Visual Studio for Mac umożliwia wyewidencjonowanie tym repozytorium szybko. Wykonaj poniższe kroki, aby ją sklonować na komputerze:

1. Na pasku Menu wybierz **kontrolą wersji > wyewidencjonowania...** :

2. Spowoduje to wyświetlenie **Połącz z repozytorium** karty:

    ![Uzyskuj dostęp do repozytorium karty Szczegóły wprowadzona](media/version-control-git13.png)

3. Na stronie GitHub zdalnego repozytorium, naciśnij klawisz **klonowania lub pobrać** przycisk i skopiuj adres URL, pod warunkiem:

    ![wyświetlany adres url usługi github](media/version-control-git14.png)

4. Zastąp cały tekst w **adres URL** pola w **Połącz z repozytorium** kartę. Spowoduje to wypełnić większość pozostałych pól na tej karcie, zgodnie z opisami w obrazie w kroku #2.

5. Wprowadź katalog, który chcesz sklonować repozytorium do, a następnie naciśnij klawisz **wyewidencjonowania**.

> [!NOTE]
Jeśli repozytorium jest ponad 4GB, mogą wystąpić problemy.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli masz problemy z inicjowanie projektu za pomocą pustego repozytorium zdalnego, możesz spróbować następujące czynności:

- Przejdź do folderu rozwiązania.
- Naciśnij klawisz `Command + Shift + . ` Aby wyświetlić ukryte pliki i foldery.
- W przypadku **.git** folderu, usuń go.
- W przypadku **gitignore** pliku, usuń go.
- Naciśnij klawisz `Command + Shift + . ` Aby ukryć pliki i foldery.
- Otwórz rozwiązanie w programie VS dla komputerów Mac.
- W konsoli rozwiązanie wybierz węzeł rozwiązania.
- Przejdź do menu kontroli wersji, a następnie wybierz **publikowania w kontroli wersji**.
- Wykonaj kroki opisane powyżej samouczka, zaczynając od kroku 6.