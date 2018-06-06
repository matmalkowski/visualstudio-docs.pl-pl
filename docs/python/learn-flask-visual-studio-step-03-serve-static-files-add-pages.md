---
title: Samouczek — Dowiedz się Flask w programie Visual Studio, krok 3
description: Przewodnik podstawy Flask w kontekście projektów programu Visual Studio, w szczególności pokazująca, jak do obsługi plików statycznych, dodać stron aplikacji i używać szablonu dziedziczenia
ms.date: 06/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 384905370a16cbdcd9b4c9165f079bcbdf71a250
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752503"
---
# <a name="tutorial-step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Samouczek krok 3: obsługi plików statycznych, Dodaj strony i użyj szablonu dziedziczenia

**Poprzedni krok: [tworzenie aplikacji platformy Flask widoki i szablony strony](learn-flask-visual-studio-step-02-create-app.md)**

W poprzednich krokach tego samouczka kiedy znasz już tworzenie minimalnego aplikacji platformy Flask za pomocą pojedynczej strony HTML niezależne. Nowoczesne aplikacje web apps, jednak zwykle składają się z wielu stron i upewnij korzystanie z zasobów udostępnionych, takich jak pliki CSS i JavaScript, aby zapewnić spójne stylami i zachowania.

W tym kroku, możesz dowiedzieć się, jak:

> [!div class="checklist"]
> - Użyj szablony elementów Visual Studio, aby szybko nowe pliki o różnych typach wygodny schematyczny kod (krok 3 - 1)
> - Obsługiwać pliki statyczne z kodu (krok 3-2, opcjonalnie)
> - Dodawanie dodatkowych stron do aplikacji (krok 3-3)
> - Użyj szablonu dziedziczenia, aby utworzyć nagłówek i nav pasek, który jest używany na stronach (krok 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3 — 1: zapoznanie się z szablonów elementów

Podczas opracowywania aplikacji platformy Flask, zazwyczaj należy dodać wiele plików więcej Python, HTML, CSS i JavaScript. Dla każdego typu pliku (takich jak również inne pliki `web.config` potrzebne do wdrożenia), program Visual Studio oferuje wygodny [elementu szablony](python-item-templates.md) ułatwiających rozpoczęcie pracy.

Aby wyświetlić dostępne szablony, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder, w którym chcesz utworzyć element, wybierz opcję **Dodaj** > **nowy element**:

![Dodaj nowe okno dialogowe elementu w programie Visual Studio](media/flask/step03-add-new-item-dialog.png)

Aby użyć szablonu, wybierz żądany szablon, określ nazwę pliku i wybierz **OK**. Dodanie elementu w ten sposób automatycznie dodaje plik do projektu programu Visual Studio i oznacza zmiany do kontroli źródła.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Pytanie: jak Visual Studio sprawdzić, które elementu szablony do zaoferowania?

Odpowiedź: Visual Studio pliku projektu (`.pyproj`) zawiera identyfikator typu projektu, który oznacza je jako projekt języka Python. Visual Studio za pomocą tego identyfikatora typu do wyświetlenia tylko te szablony elementów, które są odpowiednie dla typu projektu. W ten sposób programu Visual Studio można podać bogaty zestaw szablonów elementów wielu projektu bez konieczności sortowania za ich pośrednictwem zawsze typów.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3-2: obsługiwać pliki statyczne z aplikacji

W aplikacji sieci web utworzona za pomocą języka Python (za pomocą dowolnej architektury) pliki Python zawsze uruchamiane na serwerze hosta sieci web i nigdy nie są przesyłane do komputera użytkownika. Inne pliki, takich jak CSS i JavaScript, są używane wyłącznie przez przeglądarkę, więc serwer hosta po prostu dostarcza je jako — jest zawsze, gdy są one wymagane. Takie pliki są określane jako "statyczny" pliki i platformy Flask zapewnia je automatycznie bez konieczności pisania kodu. W plikach HTML na przykład można po prostu odwołujesz się do plików statycznych przy użyciu ścieżki względnej w projekcie. Pierwsza sekcja, w tym kroku dodaje pliku CSS do istniejącego szablonu strony.

Gdy potrzebne do dostarczania plików statycznych z kodu, takie jak przez implementację interfejsu API punktu końcowego platformy Flask stanowi wygodną metodę umożliwiające odwołują się do plików za pomocą ścieżek względnych w folderze o nazwie `static` (w katalogu głównym projektu). Druga sekcja w tym kroku przedstawiono tej metody za pomocą pliku prostego danych statycznych.

W obu przypadkach można organizować pliki objęte `static` jednak chcesz.

### <a name="use-a-static-file-in-a-template"></a>Użyj plików statycznych w szablonie

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder "HelloFlask" w projekcie programu Visual Studio, wybierz **Dodaj** > **nowy folder**oraz nazwę folderu `static`.

1. Kliknij prawym przyciskiem myszy `static` i wybierz polecenie **Dodaj** > **nowy element**. W oknie dialogowym, wybierz szablon "Stylesheet", określ nazwę pliku `site.css`i wybierz **OK**. `site.css` Pliku pojawia się w projekcie i jest otwarty w edytorze. Struktury folderu powinna wyglądać podobnie do poniższej ilustracji:

    ![Struktura plików statycznych, jak pokazano w Eksploratorze rozwiązań](media/flask/step03-static-file-structure.png)

1. Zastąp zawartość `site.css` z następującym kodem, a następnie zapisz plik:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Zastąp zawartość aplikacji `templates/index.html` pliku następującym kodem, który zastępuje `<strong>` element używany w kroku 2 z `<span>` , która odwołuje się `message` stylu klasy. Przy użyciu klasy stylu w ten sposób zapewnia większą elastyczność w elemencie style.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Uruchom projekt, aby sprawdzić wyniki. Zatrzymaj aplikację po zakończeniu i zatwierdzić zmiany do kontroli źródła, jeśli chcesz (zgodnie z objaśnieniem w [krok 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)).

### <a name="serve-a-static-file-from-code"></a>Obsługi plików statycznych z kodu

Flask zawiera funkcji o nazwie `serve_static_file` którymi można się połączyć z kodu do odwoływania się do dowolnego pliku w projekcie `static` folderu. Następujący proces tworzy prosty punkt końcowy interfejsu API, która zwraca plik danych statycznych).

1. Jeśli jeszcze tego nie zrobiono tego wcześniej, Utwórz `static` folder: w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder "HelloFlask" w projekcie programu Visual Studio, wybierz **Dodaj**  >  **Nowy folder**i nadaj mu nazwę `static`.

1. W `static` folderu, Utwórz plik statyczny danych JSON o nazwie `data.json` z następującą zawartość (które są bez znaczenia przykładowe dane):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. W `views.py`, dodać trasy/api/danych zwraca plików statycznych danych przy użyciu funkcji `send_static_file` metody:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Uruchom aplikację i przejdź do końcowego danych/api/aby zobaczyć, zwracany jest plików statycznych. Gdy wszystko będzie gotowe, Zatrzymaj aplikację.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Pytanie: czy istnieją Konwencji służący do organizowania pliki statyczne?

Odpowiedź: Można dodać inne pliki CSS, JavaScript i HTML w Twojej `static` folderu jednak ma. Typowy sposób organizowania pliki statyczne jest utworzenie podfoldery o nazwach `fonts`, `scripts`, i `content` (dla arkusze stylów i inne pliki).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Pytanie: jak I obsługuje adresu URL zmiennych i parametrów zapytania w interfejsie API?

Odpowiedź: Zobacz odpowiedzi w kroku 1-4 dla [pytanie: jak Flask pracy zmiennej trasy adresu URL i parametry zapytania?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Dodaj stronę aplikacji

Dodawanie do aplikacji innej strony oznacza:

- Dodawanie funkcji języka Python, która określa widok.
- Dodaj szablon dla danej strony znacznika.
- Dodaj niezbędne routingu do projektu Django `urls.py` pliku.

Poniższe kroki Dodaj stronę "Temat" do projektu "HelloFlask" i łącza do tej strony, na stronie głównej:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `templates` folderu, wybierz opcję **Dodaj** > **nowy element**, wybierz szablon elementu "Strony HTML", określ nazwę pliku `about.html`i wybierz **OK**.

    > [!Tip]
    > Jeśli **nowy element** polecenia nie jest wyświetlany na **Dodaj** menu, upewnij się, że została zatrzymana aplikacji tak, aby program Visual Studio opuszcza tryb debugowania.

1. Zastąp zawartość `about.html` z następujący kod znaczników (musisz zastąpić jawne łącze do strony głównej paska nawigacyjnego proste w kroku 3-4):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Otwórz aplikację `views.py` plik i dodać funkcję o nazwie `about` używający szablonu:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Otwórz `templates/index.html` pliku i Dodaj następujący wiersz bezpośrednio w ramach `<body>` elementu, aby utworzyć łącze do strony informacje (ponownie, należy zamiast tego łącza paska nawigacji, w kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Zapisz wszystkie pliki przy użyciu **pliku** > **Zapisz wszystko** polecenia menu lub po prostu naciśnij lub Ctrl + Shift + S. (Technicznie, ten krok nie jest wymagany, ponieważ uruchamiania projektu w programie Visual Studio automatycznie zapisuje pliki. Niemniej jednak jest dobrym polecenie się dowiedzieć!)

1. Uruchom projekt obserwować wyniki i sprawdzić nawigacji między stronami. Zatrzymaj aplikację po zakończeniu.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Pytanie: Nazwą funkcji strony ma znaczenia, aby Flask?

Odpowiedź: No, ponieważ jest on `@app.route` dekoratora, który określa adresy URL, dla których Flask wywołuje funkcję do generowania odpowiedzi. Deweloperzy zazwyczaj zgodna z nazwą funkcji do trasy, ale takie dopasowywania nie jest wymagane.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3 — 4: umożliwia tworzenie nagłówka i nav pasek dziedziczenia szablonu

Zamiast łącza nawigacji jawne na każdej stronie, aplikacje sieci web nowoczesnych zwykle korzystać znakowania nagłówka i pasek nawigacyjny, który zawiera najważniejsze łączy strony, menu podręcznego i tak dalej. Aby upewnić się, że nagłówek i paska nawigacyjnego są takie same na wszystkich stronach, jednak nie chcesz powtarzać ten sam kod w każdym szablonie strony. Zamiast tego chcesz zdefiniować typowych części wszystkich stron w jednym miejscu.

System tworzenia szablonów dla platformy flask (Jinja domyślnie) zapewnia dwóch oznacza, że ponowne użycie określonych elementów w wielu szablonów: zawiera i dziedziczenia.

- *Obejmuje* są inne szablony stron, które wstawiają w określonym miejscu w szablonie odwołujący się przy użyciu składni `{% include <template_path> %}`. Można również użyć zmiennej, jeśli chcesz zmienić ścieżkę dynamicznie w kodzie. Obejmuje są zazwyczaj używane w treści strony do ściągnięcia w szablonie udostępnionych z określonej lokalizacji na stronie.

- *Dziedziczenie* używa `{% extends <template_path> %}` szablon strony, aby określić szablon podstawowy udostępnionego szablonów odwołujących się następnie bazując na początku. Dziedziczenie często jest używana do definiowania układu udostępnionego, pasek nawigacji i innych struktury dla stron aplikacji w taki sposób, że odwołujących się szablony muszą dodać lub zmodyfikować tylko określonej części szablonu bazowego, o nazwie *bloków*.

W obu przypadkach `<template_path>` jest określana względem aplikacji `templates` folder (`../` lub `./` również są dozwolone).

Szablon podstawowy wyznacza *bloków* przy użyciu `{% block <block_name> %}` i `{% endblock %}` tagów. Jeśli szablon odwołujący się następnie używa tagi o takiej samej nazwie bloku, jego zawartości bloku zastępuj podstawowego szablonu.

Poniższe kroki prezentują dziedziczenia:

1. W aplikacji `templates` folderu, Utwórz nowy plik HTML (przy użyciu **Dodaj** > **nowy element** menu kontekstowego lub **Dodaj**  >   **Strona HTML**) o nazwie `layout.html`i zastąp jego zawartość znacznika poniżej. Aby sprawdzić, czy ten szablon zawiera blok o nazwie "zawartość", który jest całkowicie zastąpić odwołujący się potrzeba stron:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="/static/site.css" />
    </head>

    <body>
        <div class="navbar">
            <a href="/" class="navbar-brand">Hello Flask</a>
            <a href="{{ url_for('home') }}" class="navbar-item">Home</a>
            <a href="{{ url_for('about') }}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
            {% block content %}
            {% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Dodaj następujące style w aplikacji `static/site.css` plików (w tym przewodniku nie jest próby pokazują tutaj elastyczny projekt; te style są po prostu wygenerował wyniku interesujące):

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. Modyfikowanie `templates/index.html` odwoływać się do szablonu podstawowego i zastępowania zawartości bloku. Aby sprawdzić, czy za pomocą dziedziczenia, ten szablon staje się proste:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Modyfikowanie `templates/about.html` także odwoływać się do szablonu podstawowego i zastępowania bloku zawartości:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Uruchom serwer obserwować wyniki. Zamknij serwer po zakończeniu.

    ![Uruchomionej aplikacji wyświetlanie paska nawigacji](media/flask/step03-nav-bar.png)

1. Ponieważ istotne zmiany są wprowadzane do aplikacji, jest ponownie odpowiedni moment, aby [Zatwierdź zmiany do kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Szablon projektu sieci Web platformy Flask pełny](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- Aby uzyskać więcej możliwości Jinja szablonów, takich jak przepływu sterowania, zobacz [Jinja szablon projektanta dokumentacji](http://jinja.pocoo.org/docs/2.10/templates) (jinja.pocoo.org)
- Aby uzyskać więcej informacji na temat używania `url_for`, zobacz [url_for](http://flask.pocoo.org/docs/1.0/api/?highlight=url_for#flask.url_for) w dokumentacji obiektu aplikacji platformy Flask (flask.pocoo.org)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowy — vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)