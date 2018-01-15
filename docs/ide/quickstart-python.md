---
title: "Szybki Start: tworzenie pierwszej aplikacji sieci web platformy Python za pomocą programu Visual Studio | Dokumentacja firmy Microsoft"
description: "Krótkie wprowadzenie do programu Visual Studio, która tworzy aplikację sieci web proste przy użyciu platformy Falcon przy użyciu języka Python."
ms.custom: 
ms.date: 01/08/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: python
author: kraigb
ms.author: kraigb
manager: ghogen
dev_langs: python
ms.workload:
- python
- data-science
ms.openlocfilehash: 684cbe21a7f6454549d2e014682533697306152b
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>Szybki Start: tworzenie pierwszej aplikacji sieci web platformy Python za pomocą programu Visual Studio

To 5 – 10 min wprowadzenie do programu Visual Studio zintegrowane środowisko programistyczne (IDE) utworzysz prostą aplikację sieci web języka Python. Jeśli program Visual Studio nie został już zainstalowany, zainstaluj go bezpłatnie [tutaj](http://www.visualstudio.com).

## <a name="create-the-project"></a>Utwórz projekt

1. Otwórz program Visual Studio 2017 r.

1. Na pasku menu u góry wybierz **Plik > Nowy > Projekt...** .

1. W **nowy projekt** okno dialogowe, w lewym okienku rozwiń **zainstalowana**, a następnie wybierz pozycję **Python**.

1. W środkowym okienku wybierz **projektu sieci Web**, nadaj nazwę, takie jak "HelloPython" projektu, a następnie wybierz **OK**.

    ![Okno dialogowe nowego projektu z projektu sieci Web języka Python wybrane](media/quickstart-python-00-web-project.png)

    Jeśli nie widzisz szablony projektów języka Python, Anuluj poza **nowy projekt** okna dialogowego polu, a następnie na pasku menu u góry wybierz **Narzędzia > Pobierz narzędzia i funkcje...**  otworzyć Instalator programu Visual Studio. Wybierz **programowania Python** obciążenia, a następnie wybierz **Modyfikuj**.

    ![Obciążenie programowania Python w Instalatorze programu Visual Studio](../python/media/installation-python-workload.png)

1. Nowy projekt zostanie otwarty w **Eksploratora rozwiązań** w okienku po prawej stronie. Projekt jest pusta, w tym momencie ponieważ nie zawiera on innych plików.

    ![Eksploratora rozwiązań przedstawiający nowo utworzony pusty projekt](media/quickstart-python-01-empty-project.png)

**Pytanie, jakie są zalety tworzenia projektu w programie Visual Studio dla aplikacji Python?**

Odpowiedź: Python aplikacje są zazwyczaj definiowane przy użyciu tylko plików i folderów, ale ta struktura może stać się złożona jako aplikacje większy i może obejmować automatycznie generowanej pliki JavaScript dla aplikacji sieci web i tak dalej. Projektu programu Visual Studio pomaga zarządzać tym złożoności. Projekt ( `.pyproj` pliku) identyfikuje źródła i pliki zawartości skojarzonej z projektem, zawiera informacje o kompilacji dla każdego pliku przechowuje informacje o integracji z systemami kontroli źródła i pomaga organizować aplikacji do składników logicznych.

## <a name="install-the-falcon-library"></a>Zainstaluj biblioteki Falcon

Aplikacje sieci Web w języku Python prawie zawsze używa jednego z wielu dostępnych bibliotek języka Python do obsługi szczegółów niskiego poziomu, takich jak routing żądań sieci web i kształtowania odpowiedzi. W tym celu programu Visual Studio udostępnia wiele szablonów dla aplikacji sieci web przy użyciu struktury Bottle, Flask i Django.

W tym szybkiego startu jednak, przy użyciu biblioteki Falcon zgłaszać proces instalowania pakietu i tworzenia aplikacji sieci web od podstaw. (Visual Studio obecnie obejmuje szablony specyficzne dla Falcon). Dla uproszczenia następujące kroki instalowania Falcon w domyślnym środowisku globalnego.

1. Rozwiń węzeł **środowiska Python** węzła w projekcie domyślnym środowisku projektu.

    ![Eksploratora rozwiązań przedstawiający domyślnego środowiska](media/quickstart-python-02-default-environment.png)

1. Kliknij prawym przyciskiem myszy środowisko i wybierz **zainstaluj pakiet języka Python...** . To polecenie powoduje otwarcie **środowiska Python** okno na **pakiety** kartę. W polu wyszukiwania wprowadź "falcon" i wybierz **"pip zainstalować falcon" z PyPI**. Zaakceptuj wszystkie wyświetla monit o uprawnienia administratora i obserwować **dane wyjściowe** okna w programie Visual Studio dla postępu. (Monit podniesienia uprawnień spowodowany folder pakietów globalnego środowiska znajduje się w obszarze chronionym jak `c:\program files`.)

    ![Instalowanie biblioteki Falcon](media/quickstart-python-03-install-package.png)

1. Po zainstalowaniu biblioteki pojawia się w środowisku w **Eksploratora rozwiązań**, co oznacza, że można wprowadzać z niego korzystać w kodzie języka Python.

    ![Biblioteka falcon zainstalowany](media/quickstart-python-04-package-installed.png)

Aby uzyskać więcej informacji na temat Falcon, odwiedź stronę [falconframework.org](https://falconframework.org/).

Należy pamiętać, zamiast instalowania bibliotek w środowisku globalnych, deweloperzy zazwyczaj utworzyć "środowisko wirtualne", w którym chcesz zainstalować biblioteki dla określonego projektu. Wiele szablonów projektu języka Python w programie Visual Studio `requirements.txt` plik zawierający listę bibliotek, od których zależy ten szablon. Tworzenie projektu z jednego z tych szablonów wyzwala tworzenie środowiska wirtualnego, w którym są zainstalowane biblioteki. Aby uzyskać więcej informacji, zobacz [środowiska Python - środowisk wirtualnych](../python/python-environments.md#creating-virtual-environments).

## <a name="add-a-code-file"></a>Dodawanie plików kodu

Teraz możesz dodać bitowego kodu języka Python do wdrożenia aplikacji sieci web minimalny.

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj > Nowy element...** .

1. W wyświetlonym oknie dialogowym wybierz **pusty plik Python**, nadaj jej nazwę `hello.py`i wybierz **Dodaj**. Visual Studio automatycznie otwiera plik w oknie edytora. (Zazwyczaj **Dodaj > Nowy element...**  polecenia jest to dobry sposób na dodawanie różnych typów plików do projektu, szablony elementów często stanowi przydatne schematyczny kod.)

1. Skopiuj poniższy kod i wklej ją do `hello.py`:

    ```python
    import falcon

    # In Falcon, define a class for each resource and define on_* methods
    # where * is any standard HTTP methods in lowercase, such as on_get.

    class HelloResource:
        # In this application, the single HelloResource responds to only GET
        # requests, so it has only an on_get method.

        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to HelloResource. If you add
    # other resources, use api.add_route to define the desired
    # resource locators for them.
    api = falcon.API()
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        # Use Python's built-in WSGI reference implementation to run
        # a web server for the application.
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

1. Po wklejeniu tego kodu programu Visual Studio może pokazywać wężyk poniżej `falcon` w pierwszym wierszu, a także poniżej `wsgiref.simple.server` wierszu 20. Wskaźniki te są wyświetlane, gdy program Visual Studio jest wciąż tworzenia bazy danych IntelliSense dla tych modułów.

Aby uzyskać więcej informacji o Falcon, zobacz [szybkiego startu Falcon](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (falcon.readthedocs.io).

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij prawym przyciskiem myszy `hello.py` w **Eksploratora rozwiązań** i wybierz **Ustaw jako plik uruchamiania**. Polecenie wskazywany jest plik kodu do uruchomienia w języku Python podczas uruchamiania aplikacji.

    ![Ustawienie pliku uruchomienia projektu w Eksploratorze rozwiązań](media/quickstart-python-05-set-as-startup-file.png)

1. Kliknij prawym przyciskiem myszy projekt "Hello Python" w **Eksploratora rozwiązań** i wybierz **właściwości**. Następnie wybierz **debugowania** kartę i ustawić **numer portu** właściwości `8080`. Ten krok zapewnia, że Visual Studio spowoduje uruchomienie przeglądarki z `localhost:8080` zamiast przy użyciu losowego portu.

1. Wybierz **Debuguj > Uruchom bez debugowania** (Ctrl + F5), aby zapisać zmiany do plików i uruchom aplikację.

1. Polecenie Okno z komunikatem "Uruchamianie serwera aplikacji sieci web", a następnie okno przeglądarki, należy otworzyć do `localhost:8080` w przypadku, gdy zostanie wyświetlony komunikat "Hello, Python!" Żądania GET są również wyświetlane w oknie wiersza polecenia.

    Jeśli przeglądarce nie zostanie uruchomiony automatycznie, uruchom wybraną przeglądarkę i przejdź do `localhost:8080`.)

    Jeśli zostanie wyświetlony tylko Python interakcyjne powłoki w oknie wiersza polecenia lub okno miga na ekranie krótko, upewnij się, że ustawiona `hello.py` jako plik uruchamiania w kroku 1.

1. Zamknij okno wiersza poleceń, aby zatrzymać aplikację, a następnie zamknij okno przeglądarki.

## <a name="next-steps"></a>Następne kroki

Gratulujemy Kończenie pracy tego przewodnika Szybki Start, w którym znasz nieco programu Visual Studio IDE języka Python. Aby kontynuować pełniejsze samouczek dotyczący Python w programie Visual Studio, w tym za pomocą okna interaktywnego debugowania wizualizacji danych i Praca z usługą Git, kliknij przycisk poniżej.

> [!div class="nextstepaction"]
> [Samouczek: Wprowadzenie do języka Python w programie Visual Studio](../python/vs-tutorial-01-01.md).

- Dowiedz się więcej o [szablonów aplikacji w programie Visual Studio web języka Python](../python/template-web.md)
- Dowiedz się więcej o [debugowania języka Python](../python/debugging.md)
- Dowiedz się więcej o [programu Visual Studio IDE](../ide/visual-studio-ide.md)
