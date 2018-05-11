---
title: 'Szybki Start: tworzenie aplikacji sieci web języka Python za pomocą programu Visual Studio'
description: W tego przewodnika Szybki Start możesz użyć programu Visual Studio i platformy Flask do tworzenia aplikacji sieci web proste w języku Python.
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9a62dfc6cfe5cef21cc2198dd90867a7960312f9
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Szybki Start: Tworzenie pierwszej aplikacji sieci web platformy Python za pomocą programu Visual Studio

To 5 – 10 min wprowadzenie do programu Visual Studio jako IDE języka Python utworzysz prostą aplikację sieci web języka Python w ramach struktury platformy Flask. Tworzenie projektu za pomocą odrębny kroki, które ułatwiają Dowiedz się więcej o podstawowych funkcji programu Visual Studio.

Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) bezpłatnie go zainstalować. W Instalatorze, upewnij się wybrać **programowania Python** obciążenia.

## <a name="create-the-project"></a>Utwórz projekt

Poniższe kroki, Utwórz pusty projekt, który służy jako kontener dla aplikacji:

1. Otwórz program Visual Studio 2017 r.

1. Na pasku menu u góry wybierz **Plik > Nowy > Projekt**.

1. W **nowy projekt** oknie dialogowym wpisz "Python projekt sieci Web" w polu wyszukiwania w prawym górnym rogu, wybierz **projektu sieci Web** na liście środkowej nadaj nazwę, takie jak "HelloPython" projektu, a następnie wybierz **OK**.

    ![Okno dialogowe nowego projektu z projektu sieci Web języka Python wybrane](media/quickstart-python-00-web-project.png)

    Jeśli nie widzisz szablony projektów języka Python, Anuluj poza **nowy projekt** okna dialogowego polu, a na pasku menu u góry wybierz pozycję **Narzędzia > Pobierz narzędzia i funkcje** otworzyć **programu Visual Studio Instalator**. Wybierz **programowania Python** obciążenia, a następnie wybierz **Modyfikuj**.

    ![Obciążenie programowania Python w Instalatorze programu Visual Studio](../python/media/installation-python-workload.png)

1. Nowy projekt zostanie otwarty w **Eksploratora rozwiązań** w okienku po prawej stronie. Projekt jest pusta, w tym momencie ponieważ nie zawiera on innych plików.

    ![Eksploratora rozwiązań przedstawiający nowo utworzony pusty projekt](media/quickstart-python-01-empty-project.png)

**Pytanie: Jakie są zalety tworzenia projektu w programie Visual Studio dla aplikacji Python?**

**Odpowiedzi**: Python aplikacje są zazwyczaj definiowane przy użyciu tylko plików i folderów, ale to prostą strukturę może być uciążliwe, jak aplikacje większy i może obejmować automatycznie generowanej pliki JavaScript dla aplikacji sieci web i tak dalej. Projektu programu Visual Studio pomaga zarządzać tym złożoności. Projekt ( *.pyproj* pliku) identyfikuje źródła i pliki zawartości skojarzonej z projektem, zawiera informacje o kompilacji dla każdego pliku przechowuje informacje o integracji z systemami kontroli źródła i pomaga organizowanie na logiczne składniki aplikacji.

**Pytanie: Co to jest "Rozwiązanie" wyświetlany w Eksploratorze rozwiązań?**

**Odpowiedzi**: rozwiązanie programu Visual Studio jest kontenerem, który ułatwia zarządzanie dla jednego lub więcej projektów powiązanych jako grupa i przechowuje ustawienia konfiguracji, które nie są specyficzne dla projektu. Projekty w rozwiązaniu można także odwoływać siebie, tak, aby uruchamiania jednego projektu (aplikacji Python) automatycznie tworzy drugi projektu (takiej jak rozszerzenie C++ używane w aplikacji Python).

## <a name="install-the-flask-library"></a>Zainstaluj biblioteki platformy Flask

Aplikacje sieci Web w języku Python prawie zawsze używa jednego z wielu dostępnych bibliotek języka Python do obsługi szczegółów niskiego poziomu, takich jak routing żądań sieci web i kształtowania odpowiedzi. W tym celu program Visual Studio oferuje różne szablony dla aplikacji sieci web, z których jedna używasz w dalszej części tego przewodnika Szybki Start.

W tym miejscu umożliwia następujące kroki instalowania biblioteki platformy Flask do domyślnego "globalnego środowiska" używającej dla tego projektu programu Visual Studio.

1. Rozwiń węzeł **środowiska Python** węzła w projekcie domyślnym środowisku projektu.

    ![Eksploratora rozwiązań przedstawiający domyślnego środowiska](media/quickstart-python-02-default-environment.png)

1. Kliknij prawym przyciskiem myszy środowisko i wybierz **zainstaluj pakiet języka Python**. To polecenie powoduje otwarcie **środowiska Python** okno na **pakiety** kartę.

1. W polu wyszukiwania wprowadź "flask" i wybierz **pip zainstalować flask z PyPI**. Zaakceptuj wszystkie wyświetla monit o uprawnienia administratora i obserwować **dane wyjściowe** okna w programie Visual Studio dla postępu. (Monit podniesienia uprawnień spowodowany folder pakietów globalnego środowiska znajduje się w obszarze chronionym jak *C:\Program Files*.)

    ![Instalowanie biblioteki platformy Flask](media/quickstart-python-03-install-package.png)

1. Po zainstalowaniu biblioteki pojawia się w środowisku w **Eksploratora rozwiązań**, co oznacza, że można wprowadzać z niego korzystać w kodzie języka Python.

    ![Biblioteka flask zainstalowany](media/quickstart-python-04-package-installed.png)

> [!Note]
> Zamiast instalowania bibliotek w środowisku globalnych, deweloperzy zazwyczaj tworzenia "środowisk wirtualnych" w którym chcesz zainstalować biblioteki dla określonego projektu. Szablony Visual Studio oferują zwykle tę opcję, zgodnie z opisem w [Szybki Start — tworzenie za pomocą szablonu projektu języka Python](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Pytanie: Gdzie dowiedzieć się więcej na temat innych dostępnych pakietów języka Python?**

**Odpowiedzi**: odwiedź [indeksu pakietów języka Python](https://pypi.org/).

## <a name="add-a-code-file"></a>Dodawanie plików kodu

Teraz możesz dodać bitowego kodu języka Python do wdrożenia aplikacji sieci web minimalny.

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj > Nowy element**.

1. W wyświetlonym oknie dialogowym wybierz **pusty plik Python**, nadaj jej nazwę *app.py*i wybierz **Dodaj**. Visual Studio automatycznie otwiera plik w oknie edytora.

1. Skopiuj poniższy kod i wklej ją do *app.py*:

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```

1. Można zauważyć, że **Dodaj > Nowy element** wiele innych typów plików, które można dodać do projektu języka Python, takich jak klasy języka Python, pakiet języka Python, testu jednostkowego języka Python, wyświetla okno dialogowe *web.config* pliki i inne. Ogólnie rzecz biorąc te szablony elementów, jak są nazywane, są to dobry sposób na szybkie tworzenie plików przydatne schematyczny kod.

**Pytanie: Gdzie można dowiedzieć się więcej na temat platformy Flask?**

**Odpowiedzi**: można znaleźć w dokumentacji platformy Flask, począwszy od [szybkiego startu Flask](http://flask.pocoo.org/docs/0.12/quickstart/#quickstart).

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij prawym przyciskiem myszy *app.py* w **Eksploratora rozwiązań** i wybierz **Ustaw jako plik uruchamiania**. To polecenie Określa plik kodu, można uruchomić w języku Python podczas uruchamiania aplikacji.

    ![Ustawienie pliku uruchomienia projektu w Eksploratorze rozwiązań](media/quickstart-python-05-set-as-startup-file.png)

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**. Następnie wybierz **debugowania** kartę i ustawić **numer portu** właściwości `4449`. Ten krok zapewnia, że Visual Studio spowoduje uruchomienie przeglądarki z `localhost:4449` odpowiadające `app.run` argumenty w kodzie.

1. Wybierz **Debuguj > Uruchom bez debugowania** (**Ctrl**+**F5**), który zapisuje zmiany do plików i aplikacji.

1. Okno polecenia pojawi się komunikat o "* uruchomionych w https://localhost:4449/", a oknie przeglądarki powinien zostać otwarty do `localhost:4449` w przypadku, gdy zostanie wyświetlony komunikat "Hello, Python!" Żądanie GET jest także wyświetlany w oknie wiersza polecenia z stanu 200.

    Jeśli przeglądarce nie zostanie uruchomiony automatycznie, uruchom wybraną przeglądarkę i przejdź do `localhost:4449`.

    Jeśli zostanie wyświetlony tylko Python interakcyjne powłoki w oknie wiersza polecenia lub okno miga na ekranie krótko, upewnij się, że ustawiona *app.py* jako plik uruchamiania w kroku 1.

1. Przejdź do `localhost:4449/hello` do przetestowania, czy dekoratora dla `/hello` działa także zasobów. Żądanie GET zostanie wyświetlony ponownie, w oknie wiersza polecenia ze stanem 200. Możesz spróbować niektóre inne również adres URL, aby sprawdzić, czy przedstawiają 404 kodów stanu w oknie wiersza polecenia.

1. Zamknij okno wiersza poleceń, aby zatrzymać aplikację, a następnie zamknij okno przeglądarki.

**Pytanie: Jaka jest różnica między polecenia Uruchom bez debugowania i Rozpocznij debugowanie?**

**Odpowiedzi**: możesz użyć **Rozpocznij debugowanie** do uruchomienia aplikacji w kontekście [debuger programu Visual Studio](../python/debugging-python-in-visual-studio.md), dzięki czemu można ustawić punktów przerwania, Sprawdź zmienne i wykonywać krokowo kodu wiersz po wierszu. Aplikacje mogą być wykonywane wolniej debugera z powodu różnych punkty zaczepienia, które umożliwiają debugowania. **Uruchom bez debugowania**, natomiast bezpośrednio uruchamia aplikację tak, jakby korzystania z wiersza polecenia, bez debugowania kontekstu i automatycznie spowoduje uruchomienie przeglądarki i przechodzi do adresu URL określonego we właściwościach projektu  **Debugowanie** kartę.

## <a name="next-steps"></a>Następne kroki

Gratulujemy programem pierwszej aplikacji Python z programu Visual Studio, w których znasz nieco jako IDE języka Python za pomocą programu Visual Studio!

Ponieważ kroki, które należy przestrzegać w tego przewodnika Szybki Start są dość ogólny, prawdopodobnie zostały odgadnąć może i powinno zostać zautomatyzowane. Takie automatyzacji jest rola szablony projektu Visual Studio. Kliknij przycisk poniżej do pokazania, która tworzy aplikację sieci web podobny do tego, który został utworzony w tym artykule, ale przy użyciu mniejszej liczby kroków.

> [!div class="nextstepaction"]
> [Szybki Start — tworzenie za pomocą szablonu projektu języka Python](../python/quickstart-02-python-in-visual-studio-project-from-template.md)

Aby kontynuować pełniejsze samouczek dotyczący Python w programie Visual Studio, w tym za pomocą okna interaktywnego debugowania wizualizacji danych i Praca z usługą Git, kliknij przycisk poniżej.

> [!div class="nextstepaction"]
> [Samouczek: Wprowadzenie do języka Python w programie Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

Aby zapoznać się z bardziej Visual Studio ma oferty, zaznacz poniższe łącza.

- Dowiedz się więcej o [szablonów aplikacji w programie Visual Studio web języka Python](../python/python-web-application-project-templates.md).
- Dowiedz się więcej o [debugowania języka Python](../python/debugging-python-in-visual-studio.md)
- Dowiedz się więcej o [programu Visual Studio IDE](../ide/visual-studio-ide.md) ogólnie.
