---
title: Tworzenie środowiska programowania .NET Core z kontenerami przy użyciu Kubernetes w chmurze za pomocą programu Visual Studio — krok 6 — więcej informacji na temat tworzenia zespołu | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 04/05/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: d8d81afbe4fbf99c52107c8afc6f1eb9938de792
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Rozpoczynanie pracy w środowisku połączonych z platformy .NET Core i Visual Studio

Poprzedni krok: [wywołanie innego kontenera](get-started-netcore-visualstudio-05.md)

## <a name="learn-about-team-development"></a>Dowiedz się więcej o programowanie zespołowe

Do tej pory został wcześniej uruchomiony kod naszej aplikacji tak, jakby możemy używająca tylko w aplikacji. W tej sekcji możemy dowiesz się, jak połączone środowiska upraszcza programowanie zespołowe:
* Włącz zespół deweloperów do pracy w tym samym środowisku programistycznym.
* Obsługuje wszystkich deweloperów iteracja na kodzie w izolacji i bez obawy złamanie innych użytkowników.
* Testowanie kodu na całej trasie, przed zatwierdzania kodu bez konieczności tworzenia mocks lub symulować zależności.

## <a name="challenges-with-developing-microservices"></a>Problemy z opracowywanie mikrousług
Nasze przykładowej aplikacji nie jest bardzo skomplikowane, w tej chwili. Jednak w rozwoju rzeczywistych wyzwania wyłonić wkrótce miarę dodawania więcej usług oraz rozwoju zespół deweloperów.

Obraz użytkownika pracy z usługą, która współdziała z wielu innych usług.

1. Może stać się wypadku do uruchomienia wszystkich lokalnie na rozwój rozwiązań. Komputerze deweloperskim może nie mieć wystarczającej ilości zasobów, aby uruchomić całej aplikacji. Lub, być może aplikacja ma punkty końcowe, które muszą być publicznie dostępny (na przykład aplikację odpowiada elementu webhook z aplikacji SaaS).
1. Będzie można uruchamiać tylko zależne od usług, ale oznacza to, że konieczne będzie wiedzieć pełne zamknięcie zależności (na przykład zależności zależności). Lub jest to kwestia nie otrzymuje informacji o tym jak skompilować i uruchomić zależności, ponieważ nie działa na nich.
1. Niektórzy deweloperzy odwołać się do symulowania lub mocking się wiele zależności usługi. Może to ułatwić czasami, ale zarządzanie tymi mocks może szybko przybrać wysiłków programowanie. Ponadto prowadzi to do deweloperów środowiska wyszukiwania bardzo różnią się w środowisku produkcyjnym, a subtelnych błędów można pełzanie.
1. Wynika, że dowolnego typu end-to-end testowania czynności staje się trudny. Testowanie integracji tylko realistycznie możliwe po zatwierdzania, co oznacza, że widzimy problemów później w cyklu tworzenia.

    ![](media/microservices-challenges.png)

## <a name="work-in-a-shared-development-environment"></a>Praca w środowisku projektowym udostępnionego
W środowiskach połączone, można skonfigurować *udostępnionego* środowisko projektowe na platformie Azure. Każdy deweloper może skupić się na ich części aplikacji i wielokrotnie powtarzane można programować *wstępnie zatwierdzisz kod* w środowisku, które zawiera już wszystkie usługi i które ich scenariusze są zależne od zasobów w chmurze. Zależności są zawsze aktualne i deweloperów pracuje w taki sposób, który odzwierciedla produkcji.

## <a name="work-in-your-own-space"></a>Praca w swoim obszarze
Opracuj kodu dla usługi, a przed możesz przystąpić do sprawdzenia w kodzie często nie będzie w dobrym stanie. Nadal wielokrotnie powtarzane Cię, kształtowania, przetestowaniu i wykorzystywanie rozwiązania. Środowisko połączonych wprowadza pojęcie **miejsca**, który umożliwia pracę w izolacji i bez obawy złamanie członków zespołu.

Wykonaj następujące czynności, aby upewnić się, zarówno naszych `webfrontend` i `mywebapi` usługi są uruchomione w naszym środowisku programistycznym **i `mainline` miejsca**.
1. Zamknij wszystkie sesje F5/debugowania dla obu usług, ale nie zamykaj projektów w systemie windows ich Visual Studio.
2. Przełącz do okna programu Visual Studio z `mywebapi` projektu, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić usługę bez w debugerze
3. Przełącz do okna programu Visual Studio z `webfrontend` projektu, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić ją również.

> [!Note]
Czasami zachodzi konieczność Odświeżaj okna przeglądarki po nim wyświetlania strony sieci web jest początkowo po Ctrl + F5.

Każdy, kto otwiera publiczny adres URL i przechodzi do aplikacji sieci web wywoła ścieżkę kodu, możemy napisano której działa program za pomocą obu usług przy użyciu domyślnego `mainline` miejsca. Teraz załóżmy, że chcemy, aby kontynuować tworzenie `mywebapi` — jak możemy tym i nie przerywają pracy innych deweloperów, którzy korzystają z środowiska programowania? Aby to zrobić, skonfigurujemy Twoje własne miejsca.

### <a name="create-a-new-space"></a>Utwórz nowe miejsce
W programie Visual Studio możesz utworzyć dodatkowe spacje, które będą używane podczas F5 lub Ctrl + F5 usługi. Miejsce można wywołać coś, co chcesz i może być elastyczne o znaczeniu (np. `sprint4` lub `demo`).

Wykonaj następujące polecenie, aby utworzyć nowe miejsce:
1. Przełącz do okna programu Visual Studio z `mywebapi` projektu.
2. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**.
3. Wybierz **debugowania** karcie po lewej stronie, aby wyświetlić ustawienia połączenia środowiska.
4. W tym miejscu możesz zmienić lub utworzyć połączony środowiska i/lub miejsca, które będzie używane podczas F5 lub Ctrl + F5. *Upewnij się, że wybrano środowisko połączone utworzoną wcześniej*.
5. W **miejsca** listy rozwijanej wybierz **< Utwórz nowe miejsce... >**.

    ![](images/Settings.png)

6. W **Dodaj miejsce** oknie dialogowym wpisz nazwę miejsca i kliknij **OK**. Tak, aby zidentyfikować Moje partnerom jakiego miejsca pracy w nazwie ("scott") dla nowego obszaru wcześniej używanych.

    ![](images/AddSpace.png)

7. Powinien zostać wyświetlony Środowisko deweloperskie, a nowe miejsce do wybranej na stronie właściwości projektu.

    ![](images/Settings2.png)

### <a name="update-code-for-mywebapi"></a>Zaktualizuj kod dla *mywebapi*

1. W `mywebapi` projektu należy zmienić kod `string Get(int id)` metody w pliku `ValuesController.cs` w następujący sposób:
 
    ```csharp
    [HttpGet("{id}")]
    public string Get(int id)
    {
        return "mywebapi now says something new";
    }
    ```

2. Ustaw punkt przerwania w tym zaktualizowane bloku kodu (może masz już konto przed ustawić z).
3. Naciśnij klawisz F5, aby uruchomić `mywebapi` usługi. To spowoduje rozpoczęcie usługę w środowisku projektowania przy użyciu wybranego miejsca, czyli w przypadku mojej `scott`.

Poniżej przedstawiono diagram, który pomoże Ci zrozumieć, jak działają różne spacje. Niebieski ścieżka zawiera żądanie za pośrednictwem `mainline` miejsca, czyli domyślna ścieżka używane, gdy miejsce nie jest dołączany na początku do adresu URL. Zielony ścieżka zawiera żądanie za pośrednictwem `scott` miejsca.

![](media/Space-Routing.png)

Tej wbudowane możliwości środowiska połączony umożliwia testowanie kodu end-to-end w udostępnionym evironment bez konieczności wszystkich deweloperów ponownie utworzyć pełnego stosu usług w ich miejscu. Należy pamiętać, że marszruty wymaga nagłówki propagacji przekazywanych w kodzie aplikacji, zgodnie z opisami w poprzednim kroku w tym przewodniku.

## <a name="test-code-running-in-the-scott-space"></a>Testowanie kodu uruchamianego w `scott` miejsca
Aby przetestować naszej nowej wersji `mywebapi` w połączeniu z `webfrontend`, Otwórz w przeglądarce adres URL punktu dostępu publicznego dla `webfrontend` (np. https://webfrontend-teamenv.vsce.io) i przejdź do strony informacje. Pierwotny komunikat "Hello z webfrontend i Hello z mywebapi" powinna zostać wyświetlona.

Teraz Dodaj "scott" części do adresu URL, aby przypominać odczytuje https://scott-webfrontend-teamenv.vsce.io i odświeżyć przeglądarkę. Punkt przerwania ustawiony w Twojej `mywebapi` projektu należy pobrać trafień. Kliknij przycisk F5, aby kontynuować, a w przeglądarce powinien zostać wyświetlony nowy komunikat "Hello webfrontend i mywebapi teraz mówi nowy". Jest to spowodowane ścieżkę do zaktualizowanych kodu w `mywebapi` działa w `scott` miejsca.

> [!div class="nextstepaction"]
> [Podsumowanie](get-started-netcore-visualstudio-07.md)