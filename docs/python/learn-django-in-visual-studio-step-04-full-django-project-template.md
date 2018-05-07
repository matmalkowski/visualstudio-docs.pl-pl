---
title: Samouczek — Dowiedz się Django w programie Visual Studio, krok 4
description: Wskazówki dotyczące podstawy Django w kontekście projektów programu Visual Studio, w szczególności funkcje oferowane przez szablon projektu sieci Web Django.
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
ms.openlocfilehash: 387077f8845d4e070d4ad0a07f6549a97552a233
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tutorial-step-4-use-the-full-django-web-project-template"></a>Samouczek krok 4: Użyj pełnego szablonu projektu sieci Web Django

**Poprzedni krok: [obsługi plików statycznych, Dodaj strony i użyj szablonu dziedziczenia](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Teraz, gdy zostały wyczerpane podstawy Django tworzenie aplikacji na szablon "Pusty projekt aplikacji Django" w programie Visual Studio, można łatwo zrozumieć pełniejsze aplikację, która jest generowany przez szablon "Projektu sieci Web Django".

W tym kroku możesz teraz:

> [!div class="checklist"]
> - Tworzenie przy użyciu szablonu "Projekt sieci Web Django" pełniejsze aplikacji sieci web Django i sprawdź, czy struktury projektu (krok 4 - 1)
> - Zrozumienie widoki i szablony strony utworzone przez szablon projektu, które składają się z trzech stron, które dziedziczą z szablonu strony podstawowej, a które stosuje biblioteki statyczne JavaScript, jQuery i ładowania początkowego (krok 4-2)
> - Zrozumienie routingu adresów URL podany w szablonie (krok 4: 3)

Szablon zawiera również uwierzytelnianiem podstawowym, co zostało opisane w kroku 5.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4 — 1: Tworzenie projektu z szablonu

1. W programie Visual Studio, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie "LearningDjango" utworzona we wcześniejszej części tego samouczka i wybierz **Dodaj** > **nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz **pliku** > **nowy** > **projektu** zamiast.)

1. W oknie dialogowym Nowy projekt Wyszukaj i wybierz szablon "Projekt sieci Web Django" Wywołaj projektu "DjangoWeb" i wybierz **OK**.

1. Ponieważ szablon ponownie zawiera `requirements.txt` pliku, Visual Studio prosi o miejscu instalacji tych zależności. Wybierz opcję **zainstalować w środowisku wirtualnym**i w **Dodawanie środowiska wirtualnego** oknie dialogowym wybierz pozycję **Utwórz** zaakceptować wartości domyślne.

1. Po zakończeniu konfigurowania środowiska wirtualnego Python postępuj zgodnie z instrukcjami wyświetlone `readme.html` utworzyć Django użytkownika nadrzędnego (administrator). Po prostu kliknij prawym przyciskiem myszy projekt programu Visual Studio i wybierz **Python** > **Django utworzyć administratora** polecenia, a następnie postępuj zgodnie z monitami. Upewnij się zarejestrować nazwę użytkownika i hasło, jak można użyć podczas wykonywania funkcji uwierzytelniania aplikacji.

1. Ustaw projekt "DjangoWeb", aby być domyślne dla rozwiązania Visual Studio, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając **Ustaw jako projekt startowy**. Projekt startowy, który jest wyświetlany w bold, to co program jest uruchamiany w przypadku, gdy uruchamiasz debuger.

    ![Eksploratora rozwiązań przedstawiający DjangoWeb projekt jako projekt startowy](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Wybierz **debugowania** > **Rozpocznij debugowanie** (F5) lub użyj **serwera sieci Web** przycisk na pasku narzędzi do uruchomienia serwera:

    ![Uruchom serwer sieci web przycisku paska narzędzi w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Utworzona przez szablon aplikacja ma trzy strony, Home około i skontaktuj się z pomocą, które można przechodzić między za pomocą paska nawigacji. Potrwać minutę lub dwie sprawdzać różne części aplikacji. Do uwierzytelniania za pomocą aplikacji za pomocą **Zaloguj** polecenia, Użyj poświadczeń administratora utworzony wcześniej.

    ![Widok przeglądarki pełnej aplikacji projektu sieci Web Django](media/django/step04-full-app-desktop-view.png)

1. Utworzona przez szablon "Projekt sieci Web Django" aplikacja używa ładowania początkowego elastyczny Układ uwzględniający przenośnych rozmiarach. Aby wyświetlić ten reakcji, rozmiarów przeglądarki wąskie widoku, aby zawartość renderuje w pionie i paska nawigacyjnego zmieni się w ikonę menu:

    ![Widok Mobile (wąskie) aplikacji projektu sieci Web Django](media/django/step04-full-app-mobile-view.png)

1. Możesz pozostawić aplikacja uruchomiona w kolejnych sekcjach.

    Jeśli chcesz zatrzymać aplikację i [Zatwierdź zmiany do kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), najpierw otwórz **zmiany** strony **Team Explorer**, kliknij prawym przyciskiem myszy folder (środowiska wirtualnego prawdopodobnie `env`) i wybierz **ignorować te elementy lokalne**.

### <a name="examine-what-the-template-creates"></a>Sprawdź, co powoduje utworzenie szablonu

Na poziomie najszerszych szablonu "Projekt sieci Web Django" tworzy następującą strukturę:

- Pliki w katalogu głównym projektu:
  - `manage.py`, narzędzia administracyjnego Django.
  - `db.sqlite3`, domyślnej bazy danych SQLite.
  - `requirements.txt` zawierający zależności Django 1.x.
  - `readme.html`, pliku, który jest wyświetlany w programie Visual Studio po utworzeniu projektu. Jak wspomniano w poprzedniej sekcji, postępuj zgodnie z instrukcjami w tym miejscu można utworzyć konta administratora (administrator) dla aplikacji.
- `app` Folder zawiera wszystkie pliki aplikacji, łącznie z widoków, modeli testów, formularzy, szablony i pliki statyczne (zobacz krok 4-2). Zwykle Zmień nazwę tego folderu do używania więcej charakterystyczne nazwy aplikacji.
- `DjangoWeb` Folder (Django projekt) zawiera typowe pliki projektu Django: `__init.py__`, `settings.py`, `urls.py`, i `wsgi.py`. Za pomocą szablonu projektu `settings.py` został już skonfigurowany dla pliku bazy danych i aplikacji oraz `urls.py` jest już skonfigurowana przy użyciu tras dla wszystkich stron aplikacji, w tym formularz logowania.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Pytanie: Jest można udostępniać między projektami Visual Studio środowiska wirtualnego?

Odpowiedź: Tak, ale zrobić z funkcją rozpoznawanie różnych projektów, które mogą używać różnych pakietów wraz z upływem czasu, czy w związku z tym udostępnionego środowisko wirtualne musi zawierać wszystkie pakiety dla wszystkich projektów, które go używają.

Niemniej jednak aby użyć istniejącego środowiska wirtualnego, wykonaj następujące czynności:

1. Po wyświetleniu monitu, aby zainstalować zależności w programie Visual Studio, wybierz **będzie zainstalować je samodzielnie** opcji.
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **środowiska Python** a następnie wybierz węzeł **Dodawanie istniejącego środowiska wirtualnego**.
1. Przejdź do i wybierz folder zawierający środowiska wirtualnego, a następnie wybierz **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4-2: omówienie widoki i szablony utworzone przez szablon projektu strony

Jak można zaobserwować, po uruchomieniu projektu, ta aplikacja zawiera trzy widoki: Home około i skontaktuj się z pomocą. Kod dla tych widoków znajduje się w `app/views` folderu. Wywołuje po prostu każdej funkcji widoku `django.shortcuts.render` ze ścieżką do szablonu, a obiekt słownika prostego. Na przykład strony informacje jest obsługiwany przez `about` funkcji:

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

Szablony znajdują się w aplikacji `templates/app` folder (i chcesz zmienić zwykle `app` na nazwę aplikacji rzeczywistych). Szablon podstawowy `layout.html`, jest najbardziej rozbudowana. On odwołuje się do wszystkie niezbędne pliki statyczne (JavaScript i CSS), określa blok o nazwie "zawartość" innych stron zastąpienie, a także innego bloku o nazwie "skrypty". Następujące adnotacji fragmenty z `layout.html` Pokaż tych określonych obszarach:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
{% block scripts %}{% endblock %}

</body>
</html>
```

Szablony pojedynczej strony `about.html`, `contact.html`, i `index.html`, rozszerzanie każdego szablonu podstawowego `layout.html`. `about.html` to najprostszy i przedstawia `{% extends %}` i `{% block content %}` tagów:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

`index.html` i `contact.html` korzystania z tej samej struktury i przekazywania dłuższy zawartości w bloku "zawartość".

W `templates/app` folder jest również czwartej stronie `login.html`, wraz z `loginpartial.html` przenoszona do `layout.html` przy użyciu `{% include %}`. Te pliki szablonów omówiono w kroku 5 na uwierzytelniania.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Pytanie: może {% zablokować %} i {% endblock %} wcięcia w szablonie strony Django?

Odpowiedź: Tak, szablony stron Django działają prawidłowo Jeśli wcięcie bloku tagów, być może dostosować je w ich elementach elementu nadrzędnego. Nie są one wcięty w szablony stron wygenerowanych przez szablon projektu Visual Studio, aby wyraźnie widać, gdzie są umieszczone.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Krok 4: 3: zrozumienie routingu adresów URL utworzonej przez szablon

Projekt Django `urls.py` plik tworzony przez szablon "Projektu sieci Web Django" zawiera następujący kod:

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

Pierwsze trzy wzorce adres URL mapy bezpośrednio do `home`, `contact`, i `about` widoków w aplikacji `views.py` pliku. Wzorce `^login/$` i `^logout$`, w drugim ręcznie, za pomocą wbudowanych widoków Django zamiast widoki zdefiniowane w aplikacji. Wywołania `url` metoda również zawierać dodatkowe dane w celu dostosowania wyświetlania. Krok 5 Eksploruje te wywołania.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Pytanie: w projekt został utworzony, dlaczego "o" wzorzec URL używa ' ^ o "zamiast" ^ o$ "w sposób pokazany poniżej?

Odpowiedź: Brak końcowe "$" w wyrażeniu regularnym został proste nadzoru wiele wersji szablonu projektu. Wzorzec URL działa dobrze dla strony o nazwie "temat", ale bez końcowych $ wzorzec URL zgodny adresy URL takich jak "około = django", "about09876", "aboutoflaughter" i dlatego na. Końcowego znaku "$" znajduje się tutaj do tworzenia wzorca adresu URL, który odpowiada *tylko* "o".

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Uwierzytelnianie użytkowników w Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- [Pisanie pierwszej aplikacji Django, część 4 - formularzy i rodzajowy widoków](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowy — vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)