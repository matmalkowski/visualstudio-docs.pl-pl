---
title: Samouczek — Dowiedz się Django w programie Visual Studio, krok 3
description: Przewodnik podstawy Django w kontekście projektów programu Visual Studio, w szczególności pokazująca, jak do obsługi plików statycznych, dodać stron aplikacji i używać szablonu dziedziczenia
ms.date: 04/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: d94ef95b8ba50f4cf9359bb925d41243ea58df7d
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750337"
---
# <a name="tutorial-step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Samouczek krok 3: obsługi plików statycznych, Dodaj strony i użyj szablonu dziedziczenia

**Poprzedni krok: [tworzenie aplikacji Django z widokami i strony szablonów](learn-django-in-visual-studio-step-02-create-an-app.md)**

W poprzednich krokach tego samouczka kiedy znasz już tworzenie minimalnego aplikacji Django za pomocą pojedynczej strony HTML niezależne. Nowoczesne aplikacje web apps, jednak zwykle składają się z wielu stron i upewnij korzystanie z zasobów udostępnionych, takich jak pliki CSS i JavaScript, aby zapewnić spójne stylami i zachowania.

W tym kroku, możesz dowiedzieć się, jak:

> [!div class="checklist"]
> - Użyj szablony elementów Visual Studio, aby szybko nowe pliki o różnych typach wygodny schematyczny kod (krok 3 - 1)
> - Konfigurowanie projektu Django do obsługi plików statycznych (krok 3-2)
> - Dodawanie dodatkowych stron do aplikacji (krok 3-3)
> - Użyj szablonu dziedziczenia, aby utworzyć nagłówek i nav pasek, który jest używany na stronach (krok 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Krok 3 — 1: zapoznanie się z szablonów elementów

Podczas opracowywania aplikacji Django, zazwyczaj należy dodać wiele plików więcej Python, HTML, CSS i JavaScript. Dla każdego typu pliku (takich jak również inne pliki `web.config` potrzebne do wdrożenia), program Visual Studio oferuje wygodny [elementu szablony](python-item-templates.md) ułatwiających rozpoczęcie pracy.

Aby wyświetlić dostępne szablony, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder, w którym chcesz utworzyć element, wybierz opcję **Dodaj** > **nowy element**:

![Dodaj nowe okno dialogowe elementu w programie Visual Studio](media/django/step03-add-new-item-dialog.png)

Aby użyć szablonu, wybierz żądany szablon, określ nazwę pliku i wybierz **OK**. Dodanie elementu w ten sposób automatycznie dodaje plik do projektu programu Visual Studio i oznacza zmiany do kontroli źródła.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Pytanie: jak Visual Studio sprawdzić, które elementu szablony do zaoferowania?

Odpowiedź: Visual Studio pliku projektu (`.pyproj`) zawiera identyfikator typu projektu, który oznacza je jako projekt języka Python. Visual Studio za pomocą tego identyfikatora typu do wyświetlenia tylko te szablony elementów, które są odpowiednie dla typu projektu. W ten sposób programu Visual Studio można podać bogaty zestaw szablonów elementów wielu projektu bez konieczności sortowania za ich pośrednictwem zawsze typów.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Krok 3-2: obsługiwać pliki statyczne z aplikacji

W aplikacji sieci web utworzona za pomocą języka Python (za pomocą dowolnej architektury) pliki Python zawsze uruchamiane na serwerze hosta sieci web i nigdy nie są przesyłane do komputera użytkownika. Inne pliki, takich jak CSS i JavaScript, są używane wyłącznie przez przeglądarkę, więc serwer hosta po prostu dostarcza je jako — jest zawsze, gdy są one wymagane. Takie pliki są określane jako "statyczny" pliki i Django zapewnia je automatycznie bez konieczności pisania kodu.

Projekt Django jest domyślnie skonfigurowany do obsługi plików statycznych przy użyciu aplikacji `static` folderu dzięki użyciu tych wierszy w projekcie Django `settings.py`:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Można organizować pliki przy użyciu dowolnej struktury folderów w ramach `static` , a następnie użyć ścieżek względnych w tym folderze, aby odwołać się do plików. Aby zademonstrować ten proces, następujące kroki dodawania pliku CSS do aplikacji, a następnie użyj tego arkusza stylów w `index.html` szablonu:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder "HelloDjangoApp" w projekcie programu Visual Studio, wybierz **Dodaj** > **nowy folder**oraz nazwę folderu `static`.

1. Kliknij prawym przyciskiem myszy `static` i wybierz polecenie **Dodaj** > **nowy element**. W oknie dialogowym, wybierz szablon "Stylesheet", określ nazwę pliku `site.css`i wybierz **OK**. `site.css` Pliku pojawia się w projekcie i jest otwarty w edytorze. Struktury folderu powinna wyglądać podobnie do poniższej ilustracji:

    ![Struktura plików statycznych, jak pokazano w Eksploratorze rozwiązań](media/django/step03-static-file-structure.png)

1. Zastąp zawartość `site.css` z następującym kodem, a następnie zapisz plik:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Zastąp zawartość aplikacji `templates/HelloDjangoApp/index.html` pliku następującym kodem, który zastępuje `<strong>` element używany w kroku 2 z `<span>` , która odwołuje się `message` stylu klasy. Przy użyciu klasy stylu w ten sposób zapewnia większą elastyczność w elemencie style. (Jeśli nie zostało przeniesione `index.html` do podfolderu w `templates`, zapoznaj się [namespacing szablonu](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) w kroku 2.)

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Uruchom projekt, aby sprawdzić wyniki. Zatrzymaj serwer po zakończeniu i zatwierdzić zmiany do kontroli źródła, jeśli chcesz (zgodnie z objaśnieniem w [krok 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-purpose-of-the--load-staticfiles--tag"></a>Pytanie: co to jest celem {% równoważyć obciążenie staticfiles %} tagu?

Odpowiedź: `{% load staticfiles %}` wiersza jest wymagana przed zapoznaniem się plików statycznych elementów, takich jak `<head>` i `<body>`. W przykładzie przedstawionym w tej sekcji, "staticfiles" odwołuje się do niestandardowego Django szablonu tag zestawu, czyli, co pozwala na stosowanie `{% static %}` składni, aby odwołać się do plików statycznych.  Bez `{% load staticfiles %}`, zobaczysz wyjątek po uruchomieniu aplikacji.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Pytanie: czy istnieją Konwencji służący do organizowania pliki statyczne?

Odpowiedź: Można dodać inne pliki CSS, JavaScript i HTML w Twojej `static` folderu jednak ma. Typowy sposób organizowania pliki statyczne jest utworzenie podfoldery o nazwach `fonts`, `scripts`, i `content` (dla arkusze stylów i inne pliki). W każdym przypadku Pamiętaj, aby uwzględnić te foldery ścieżki względnej do pliku w `{% static %}` odwołania.

## <a name="step-3-3-add-a-page-to-the-app"></a>Krok 3-3: Dodaj stronę aplikacji

Dodawanie do aplikacji innej strony oznacza:

- Dodawanie funkcji języka Python, która określa widok.
- Dodaj szablon dla danej strony znacznika.
- Dodaj niezbędne routingu do projektu Django `urls.py` pliku.

Poniższe kroki Dodaj stronę "Temat" do projektu "HelloDjangoApp" i łącza do tej strony, na stronie głównej:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `templates/HelloDjangoApp` folderu, wybierz opcję **Dodaj** > **nowy element**, wybierz szablon elementu "Strony HTML", określ nazwę pliku `about.html`i wybierz **OK**.

    > [!Tip]
    > Jeśli **nowy element** polecenia nie jest wyświetlany na **Dodaj** menu, upewnij się, że została zatrzymana serwer tak, aby program Visual Studio opuszcza tryb debugowania.

1. Zastąp zawartość `about.html` z następujący kod znaczników (musisz zastąpić jawne łącze do strony głównej paska nawigacyjnego proste w kroku 3-4):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Otwórz aplikację `views.py` plik i dodać funkcję o nazwie `about` używający szablonu:

    ```python
    def about(request):
        return render(
            request,
            "HelloDjangoApp/about.html",
            {
                'title' : "About HelloDjangoApp",
                'content' : "Example app page for Django."
            }
        )
    ```

1. Otwórz projekt Django `urls.py` i Dodaj następujący wiersz do `urlPatterns` tablicy:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Otwórz `templates/HelloDjangoApp/index.html` pliku i Dodaj następujący wiersz poniżej `<body>` elementu, aby utworzyć łącze do strony informacje (ponownie, należy zamiast tego łącza paska nawigacji, w kroku 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Zapisz wszystkie pliki przy użyciu **pliku** > **Zapisz wszystko** polecenia menu lub po prostu naciśnij lub Ctrl + Shift + S. (Technicznie, ten krok nie jest wymagany, ponieważ uruchamiania projektu w programie Visual Studio automatycznie zapisuje pliki. Niemniej jednak jest dobrym polecenie się dowiedzieć!)

1. Uruchom projekt obserwować wyniki i sprawdzić nawigacji między stronami. Zamknij serwer po zakończeniu.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Pytanie: próbuję jako łącze do strony głównej przy użyciu "index", ale go nie działa. Dlaczego?

Odpowiedź: Mimo że widoku funkcji w `views.py` nosi nazwę `index`, adres URL routingu wzorce w projekcie Django `urls.py` plik nie zawiera wyrażenia regularnego pasującej do ciągu "index". Aby dopasować tego ciągu, należy dodać innego hasła dla wzorca `^index$`.

Jak pokazano w następnej sekcji, jest znacznie lepiej jest użyć `{% url '<pattern_name>' %}` tag szablonu strony, aby odwoływać się do *nazwa* wzorca, w którym Django przypadków tworzy prawidłowego adresu URL. Na przykład zastąpić `<div><a href="home">Home</a></div>` w `about.html` z `<div><a href="{% url 'index' %}">Home</a></div>`. Użycie "index" działa w tym miejscu, ponieważ pierwszy adres URL wzorca w `urls.py` w rzeczywistości o nazwie "index" (na mocy niniejszej `name='index'` argument). Umożliwia także "home" w odwołaniu do drugi wzorzec.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Krok 3 — 4: umożliwia tworzenie nagłówka i nav pasek dziedziczenia szablonu

Zamiast łącza nawigacji jawne na każdej stronie, aplikacje sieci web nowoczesnych zwykle korzystać znakowania nagłówka i pasek nawigacyjny, który zawiera najważniejsze łączy strony, menu podręcznego i tak dalej. Aby upewnić się, że nagłówek i paska nawigacyjnego są takie same na wszystkich stronach, jednak nie chcesz powtarzać ten sam kod w każdym szablonie strony. Zamiast tego chcesz zdefiniować typowych części wszystkich stron w jednym miejscu.

System tworzenia szablonów w Django zapewnia dwa oznacza, że ponowne użycie określonych elementów w różnych szablonach: zawiera i dziedziczenia.

- *Obejmuje* są inne szablony stron, które wstawiają w określonym miejscu w szablonie odwołujący się przy użyciu składni `{% include <template_path> %}`. Można również użyć zmiennej, jeśli chcesz zmienić ścieżkę dynamicznie w kodzie. Obejmuje są zazwyczaj używane w treści strony do ściągnięcia w szablonie udostępnionych z określonej lokalizacji na stronie.

- *Dziedziczenie* używa `{% extends <template_path> %}` szablon strony, aby określić szablon podstawowy udostępnionego szablonów odwołujących się następnie bazując na początku. Dziedziczenie często jest używana do definiowania układu udostępnionego, pasek nawigacji i innych struktury dla stron aplikacji w taki sposób, że odwołujących się szablony muszą dodać lub zmodyfikować tylko określonej części szablonu bazowego, o nazwie *bloków*.

W obu przypadkach `<template_path>` jest określana względem aplikacji `templates` folder (`../` lub `./` również są dozwolone).

Szablon podstawowy wyznacza blokach, używając `{% block <block_name> %}` i `{% endblock %}` tagów. Jeśli szablon odwołujący się następnie używa tagi o takiej samej nazwie bloku, jego zawartości bloku zastępuj podstawowego szablonu.

Poniższe kroki prezentują dziedziczenia:

1. W aplikacji `templates/HelloDjangoApp` folderu, Utwórz nowy plik HTML (przy użyciu **Dodaj** > **nowy element** menu kontekstowego lub **Dodaj**  >   **Strona HTML**) o nazwie `layout.html`i zastąp jego ze znacznikami poniżej. Aby sprawdzić, czy ten szablon zawiera blok o nazwie "zawartość", który jest całkowicie zastąpić odwołujący się potrzeba stron:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load staticfiles %}
        <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
    </head>

    <body>
        <div class="navbar">
           <a href="/" class="navbar-brand">Hello Django</a>
           <a href="{% url 'home' %}" class="navbar-item">Home</a>
           <a href="{% url 'about' %}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
    {% block content %}{% endblock %}
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

1. Modyfikowanie `templates/HelloDjangoApp/index.html` odwoływać się do szablonu podstawowego i zastępowania zawartości bloku. Aby sprawdzić, czy za pomocą dziedziczenia, ten szablon staje się proste:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Modyfikowanie `templates/HelloDjangoApp/about.html` także odwoływać się do szablonu podstawowego i zastępowania bloku zawartości:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Uruchom serwer obserwować wyniki. Zamknij serwer po zakończeniu.

    ![Uruchomionej aplikacji wyświetlanie paska nawigacji](media/django/step03-nav-bar.png)

1. Ponieważ istotne zmiany było skierowane do aplikacji, jest ponownie odpowiedni moment, aby [Zatwierdź zmiany do kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Użyj pełnego szablonu projektu sieci Web Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- [Pisanie pierwszej aplikacji Django, część 3 (widoki)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Aby uzyskać więcej możliwości szablonów Django, takich jak przepływu sterowania, zobacz [język szablonu Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Aby uzyskać szczegółowe informacje na temat używania `{% url %}` tagów, zobacz [adres url](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) w [tagi wbudowanych szablonów i filtry dla odwołania szablonów Django](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (docs.djangoproject.com)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowy — vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)