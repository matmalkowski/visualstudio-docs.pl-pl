---
title: Samouczek — Dowiedz się Flask w programie Visual Studio, krok 4
description: Wskazówki dotyczące podstawy Flask w kontekście projektów programu Visual Studio, w szczególności funkcje oferowane przez Szablony projektów sieci Web platformy Flask i projektu sieci Web platformy Flask/Jade.
ms.date: 05/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: a4c50a7b6e3fe14f27bfd78e6814f9e120864d60
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752505"
---
# <a name="tutorial-step-4-use-the-full-flask-web-project-template"></a>Samouczek krok 4: Użyj pełnego szablonu projektu sieci Web platformy Flask

**Poprzedni krok: [obsługi plików statycznych, Dodaj strony i użyj szablonu dziedziczenia](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Teraz, gdy zostały wyczerpane podstawy Flask tworzenie aplikacji na szablon "Pusty projekt aplikacji platformy Flask" w programie Visual Studio, można łatwo zrozumieć pełniejsze aplikację, która jest generowany przez szablon "Projektu sieci Web platformy Flask".

W tym kroku możesz teraz:

> [!div class="checklist"]
> - Tworzenie przy użyciu szablonu "Projekt sieci Web platformy Flask" pełniejsze aplikacji sieci web platformy Flask i sprawdź, czy struktury projektu (krok 4 - 1)
> - Zrozumienie widoki i szablony strony utworzone przez szablon projektu, które składają się z trzech stron, które dziedziczą z szablonu strony podstawowej, a które stosuje biblioteki statyczne JavaScript, jQuery i ładowania początkowego (krok 4-2)
> - Zrozumienie routingu adresów URL podany w szablonie (krok 4: 3)

Ten artykuł dotyczy również szablonu "Projekt sieci Web platformy Flask/Jade", który tworzy aplikację, która jest identyczna jak "Projektu sieci Web platformy Flask" zamiast Jinja przy użyciu aparatu Jade tworzenia szablonów. Dodatkowe informacje znajdują się na końcu tego artykułu.

## <a name="step-4-1-create-a-project-from-the-template"></a>Krok 4 — 1: Tworzenie projektu z szablonu

1. W programie Visual Studio, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie "LearningFlask" utworzona we wcześniejszej części tego samouczka i wybierz **Dodaj** > **nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz **pliku** > **nowy** > **projektu** zamiast.)

1. W oknie dialogowym Nowy projekt Wyszukaj i wybierz szablon "Projekt sieci Web platformy Flask" Wywołaj projektu "FlaskWeb" i wybierz **OK**.

1. Ponieważ szablon ponownie zawiera `requirements.txt` pliku, Visual Studio prosi o miejscu instalacji tych zależności. Wybierz opcję **zainstalować w środowisku wirtualnym**i w **Dodawanie środowiska wirtualnego** oknie dialogowym wybierz pozycję **Utwórz** zaakceptować wartości domyślne.

1. Po zakończeniu konfigurowania środowiska wirtualnego programu Visual Studio Ustaw projekt "FlaskWeb", aby być domyślne dla rozwiązania Visual Studio, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając **Ustaw jako Projekt startowy**. Projekt startowy, który jest wyświetlany w bold, to co program jest uruchamiany w przypadku, gdy uruchamiasz debuger.

    ![Eksploratora rozwiązań przedstawiający FlaskWeb projekt jako projekt startowy](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Wybierz **debugowania** > **Rozpocznij debugowanie** (F5) lub użyj **serwera sieci Web** przycisk na pasku narzędzi do uruchomienia serwera:

    ![Uruchom serwer sieci web przycisku paska narzędzi w programie Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. Utworzona przez szablon aplikacja ma trzy strony, Home około i skontaktuj się z pomocą, które można przechodzić między za pomocą paska nawigacji. Potrwać minutę lub dwie sprawdzać różne części aplikacji. Do uwierzytelniania za pomocą aplikacji za pomocą **Zaloguj** polecenia, Użyj poświadczeń administratora utworzony wcześniej.

    ![Widok przeglądarki pełnej aplikacji platformy Flask projektu sieci Web](media/flask/step04-full-app-desktop-view.png)

1. Utworzona przez szablon "Projekt sieci Web platformy Flask" aplikacja używa ładowania początkowego elastyczny Układ uwzględniający przenośnych rozmiarach. Aby wyświetlić ten reakcji, rozmiarów przeglądarki wąskie widoku, aby zawartość renderuje w pionie i paska nawigacyjnego zmieni się w ikonę menu:

    ![Widok aplikacji projektu sieci Web platformy Flask Mobile (wąskie)](media/flask/step04-full-app-mobile-view.png)

1. Możesz pozostawić aplikacja uruchomiona w kolejnych sekcjach.

    Jeśli chcesz zatrzymać aplikację i [Zatwierdź zmiany do kontroli źródła](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), najpierw otwórz **zmiany** strony **Team Explorer**, kliknij prawym przyciskiem myszy folder (środowiska wirtualnego prawdopodobnie `env`) i wybierz **ignorować te elementy lokalne**.

### <a name="examine-what-the-template-creates"></a>Sprawdź, co powoduje utworzenie szablonu

Szablon "Projekt sieci Web platformy Flask" tworzy struktury poniżej. Zawartość jest bardzo podobny do utworzone w poprzednich krokach. Różnica polega na to, że szablon "Projekt sieci Web platformy Flask" zawiera więcej struktury w `static` folderu, ponieważ zawiera jQuery i ładowania początkowego dla elastyczny projekt. Szablon dodaje również strony kontaktu. Ogólne Jeśli poprzednie kroki zostały wykonane w tym samouczku, wszystko z szablonu należy znać.

- Pliki w katalogu głównym projektu:
  - `runserver.py`, skrypt do uruchomienia aplikacji w development server.
  - `requirements.txt` zawierający zależności Flask postaci 0.x.
- `FlaskWeb` Folder zawiera pliki aplikacji:
  - `__init.py__` oznacza kod aplikacji jako moduł Python, tworzy obiekt Flask i importuje widoków aplikacji.
  - `views.py` zawiera kod służący do renderowania stron.
  - `static` Folder zawiera podfoldery o nazwach `content` (pliki CSS), `fonts` (pliki czcionki) i `scripts` (pliki JavaScript).
  - `templates` Folder zawiera `layout.html` szablonu podstawowego wraz z `about.html`, `contact.html`, i `index.html` dla określonych stron każdy rozszerzyć `layout.html`.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Pytanie: Jest można udostępniać między projektami Visual Studio środowiska wirtualnego?

Odpowiedź: Tak, ale zrobić z funkcją rozpoznawanie różnych projektów, które mogą używać różnych pakietów wraz z upływem czasu, czy w związku z tym udostępnionego środowisko wirtualne musi zawierać wszystkie pakiety dla wszystkich projektów, które go używają.

Niemniej jednak aby użyć istniejącego środowiska wirtualnego, wykonaj następujące czynności:

1. Po wyświetleniu monitu, aby zainstalować zależności w programie Visual Studio, wybierz **będzie zainstalować je samodzielnie** opcji.
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **środowiska Python** a następnie wybierz węzeł **Dodawanie istniejącego środowiska wirtualnego**.
1. Przejdź do i wybierz folder zawierający środowiska wirtualnego, a następnie wybierz **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 4-2: omówienie widoki i szablony utworzone przez szablon projektu strony

Jak można zaobserwować, po uruchomieniu projektu, ta aplikacja zawiera trzy widoki: Home około i skontaktuj się z pomocą. Kod dla tych widoków znajduje się w `FlaskWeb/views.py`. Wywołuje po prostu każdej funkcji widoku `flask.render_template` ze ścieżką do szablonu i listy zmiennych argumentów dla wartości, które ma zostać przypisany do szablonu. Na przykład strony informacje jest obsługiwany przez `about` — funkcja (których dekoratora zapewnia routingu adresów URL):

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

`home` i `contact` funkcji są niemal identyczne z podobnych elementów decorator i argumenty nieco inne.

Szablony znajdują się w aplikacji `templates` folderu. Szablon podstawowy `layout.html`, jest najbardziej rozbudowana. On odwołuje się do wszystkie niezbędne pliki statyczne (JavaScript i CSS), określa blok o nazwie "zawartość" innych stron zastąpienie, a także innego bloku o nazwie "skrypty". Następujące adnotacji fragmenty z `layout.html` Pokaż tych określonych obszarach:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
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

## <a name="the-flaskjade-web-project-template"></a>Szablon projektu sieci Web platformy Flask/Jade

Jak wspomniano na początku tego artykułu, Visual Studio Podaj szablonu "Projekt sieci Web platformy Flask/Jade", który tworzy aplikację, która jest identyczna wizualnie co to jest generowany przez "Projekt sieci Web platformy Flask". Podstawowa różnica polega na korzysta z aparat Jade tworzenia szablonów, który jest rozszerzeniem Jinja implementujący tego samego pojęcia bardziej zwięzły języka. W szczególności Jade używa słowa kluczowe zamiast tagów w {filtr ograniczników, na przykład i umożliwia odwołujesz się do stylów CSS oraz elementów HTML za pomocą słów kluczowych.

Aby włączyć Jade, szablon projektu zawiera najpierw pakiet pyjade w `requirements.txt`. 

Aplikacja `__init__.py` plik zawiera wiersz do

    ```python
    app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
    ```
W `templates` folderu, zobacz `.jade` plików zamiast `.html` szablonów i widoków `views.py` odwoływać się do tych plików w ich wywołania `flask.render_template`. W przeciwnym razie kod widoków jest taki sam.

Otwarcie jednej z `.jade` pliki, widać więcej zwięzły wyrażenie szablonu. Na przykład, w tym miejscu jest zawartość `templates/layout.jade` utworzonym przez szablon "Projekt sieci Web platformy Flask/Jade":

    ```jade
    doctype html
    html
      head
        meta(charset='utf-8')
        meta(name='viewport', content='width=device-width, initial-scale=1.0')
        title #{title} - My Flask/Jade Application
        link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
        link(rel='stylesheet', type='text/css', href='/static/content/site.css')
        script(src='/static/scripts/modernizr-2.6.2.js')
      body
        .navbar.navbar-inverse.navbar-fixed-top
          .container
            .navbar-header
              button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
                span.icon-bar
                span.icon-bar
                span.icon-bar
              a.navbar-brand(href='/') Application name
            .navbar-collapse.collapse
              ul.nav.navbar-nav
                li
                  a(href='/') Home
                li
                  a(href='/about') About
                li
                  a(href='/contact') Contact
        .container.body-content
          block content
          hr
          footer
            p &copy; #{year} - My Flask/Jade Application

        script(src='/static/scripts/jquery-1.10.2.js')
        script(src='/static/scripts/bootstrap.js')
        script(src='/static/scripts/respond.js')

        block scripts
    ```

A Oto zawartość `templates/about.jade`, przedstawiający zastosowanie `#{ <name>}` symboli zastępczych:

    ```jade
    extends layout

    block content
      h2 #{title}.
      h3 #{message}
      p Use this area to provide additional information.
    ```

Możesz eksperymentować zarówno Jinja i Jade składni, aby zobaczyć, która z nich działa najlepiej dla Ciebie.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Szablon projektu sieci Web platformy Flask sond](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- [Pisanie pierwszej aplikacji platformy Flask, część 4 - formularzy i rodzajowy widoków](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade na GitHib (dokumentacja)](https://github.com/liuliqiang/pyjade) (witrynie github.com)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python próbki vs — Dowiedz się flask](https://github.com/Microsoft/python-sample-vs-learn-flask)