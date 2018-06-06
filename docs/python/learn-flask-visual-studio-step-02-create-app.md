---
title: Samouczek — Dowiedz się Flask w programie Visual Studio, krok 2
description: Wskazówki dotyczące podstawy Flask w kontekście projektów programu Visual Studio, w szczególności kroki tworzenia aplikacji i przy użyciu widoków i szablonów.
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
ms.openlocfilehash: 9aeba681e1a4ab7bae77197d8af10a90f49a40d0
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752504"
---
# <a name="tutorial-step-2-create-a-flask-app-with-views-and-page-templates"></a>Samouczek krok 2: tworzenie aplikacji platformy Flask widoki i szablony strony

**Poprzedni krok: [tworzenia projektu Visual Studio i rozwiązania](learn-flask-visual-studio-step-01-project-solution.md)**

Masz z kroku 1 w tym samouczku jest aplikacja platformy Flask z jednej strony, a cały kod w jednym pliku. Aby umożliwić przyszłego rozwoju, najlepiej zrefaktoryzuj kod i Utwórz strukturę strony szablonów. W szczególności należy oddzielić kodu dla widoków aplikacji od innych aspektów, takich jak kod uruchomienia.

W tym kroku teraz dowiesz się, jak:

> [!div class="checklist"]
> - Refaktoryzuj kodu aplikacji do oddzielania widoków z kodu uruchamiania (krok 2 - 1)
> - Renderowania widoku, używając szablonu strony (krok 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Krok 2 — 1: Refaktoryzuj projektu do dalszego obsługuje programowanie

W kodzie utworzonej przez szablon "Pusty projekt sieci Web platformy Flask", należy mieć pojedynczy `app.py` pliku, który zawiera kod uruchomienia obok jednego widoku. Aby zezwolić na dalszy rozwój aplikacji z wielu widoków i szablony, najlepiej do oddzielania tych problemów.

1. W folderze projektu, należy utworzyć folder aplikacji o nazwie `HelloFlask` (kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj** > **nowy Folder** .)

1. W `HelloFlask` folderu, Utwórz plik o nazwie `__init.py__` z następującą zawartość, które tworzy `Flask` wystąpienia i ładuje widoków aplikacji (tworzonych w następnym kroku):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

1. W `HelloFlask` folderu, Utwórz plik o nazwie `views.py` z następującą zawartość. Nazwa `views.py` jest ważne, ponieważ użyto `import HelloFlask.views` w `__init__.py`; zostanie wyświetlony błąd w czasie wykonywania, jeśli nazwy nie są zgodne.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Oprócz zmiana nazwy funkcji i trasy do `home`, ten kod zawiera kod renderowania strony z app.py i importuje `app` obiekt, który jest zadeklarowana w `__init__.py`.

1. Utwórz podfolder w `HelloFlask` o nazwie `templates`, pozostaje pusta teraz.

1. W folderze głównym projektu, Zmień nazwę `app.py` do `runserver.py`i ich zawartość odpowiada następujący kod:

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```
1. Struktury projektu powinien wyglądać podobnie jak na poniższej ilustracji:

    ![Struktury projektu po refaktoryzacji kodu](media/flask/step02-project-structure.png)

1. Wybierz **debugowania** > **Rozpocznij debugowanie** (F5) lub użyj **serwera sieci Web** przycisk na pasku narzędzi (przeglądarka Zobacz może się różnić) do uruchamiania aplikacji i Otwórz w przeglądarce. Spróbuj zarówno / i/home tras adresów URL.

1. Można również ustawić punkty przerwania w różnych części kodu i uruchom ponownie aplikację do wykonania sekwencji uruchamiania. Na przykład ustawić punkt przerwania w pierwszym wierszach `runserver.py` i `HelloFlask\__init__.py`i na `return "Hello Flask!"` wiersz w `views.py`. Następnie ponownie uruchom aplikację (**debugowania** > **ponowne uruchomienie**, Ctrl + F5 lub przycisku paska narzędzi, pokazano poniżej) krokowo (F10) kod i uruchomić w każdym punkcie przerwania za pomocą F5.

    ![Uruchom ponownie przycisk na pasku narzędzi debugowania w programie Visual Studio](media/debugging-restart-toolbar-button.png)

1. Gdy wszystko będzie gotowe, Zatrzymaj aplikację.

### <a name="commit-to-source-control"></a>Zatwierdź do kontroli źródła

Ponieważ wprowadzono zmiany w kodzie i zostały one przetestowane pomyślnie, obecnie jest to doskonały moment, aby przejrzeć i zatwierdź zmiany do kontroli źródła. Wykonania kolejnych kroków tego samouczka przypomnienia o odpowiedni czas zatwierdzenia ponownie do kontroli źródła i odwołują się w tej sekcji.

1. Wybierz przycisk zmiany wzdłuż dolnej części programu Visual Studio (zaznaczona kółkiem poniżej), który przechodzi do **Team Explorer**.

    ![Przycisk zmiany kontroli źródła na pasku stanu programu Visual Studio](media/flask/step02-source-control-changes-button.png)

1. W **Team Explorer**, wprowadź komunikat zatwierdzenia, takie jak "Zrefaktoryzuj kod" i wybierz **zatwierdzania wszystkich**. Po zakończeniu zatwierdzenia, zostanie wyświetlony komunikat "Commit <hash> utworzony lokalnie. Przycisk Synchronizuj, aby udostępnić zmiany na serwerze. Jeśli chcesz wypchnąć zmiany do repozytorium zdalnego, wybierz opcję **synchronizacji**, a następnie wybierz pozycję **wypychania** w obszarze **wychodzących zatwierdzeń**. Można również gromadzone wielu zatwierdzeń lokalnej przed wypchnięciem zdalne.

    ![Wypychanie zatwierdzeń do zdalnego w programie Team Explorer](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Pytanie: jak często należy jedną zatwierdzenia do kontroli źródła?

Odpowiedź: Zatwierdzanie zmian do kontroli źródła tworzy rekord w dzienniku zmian, a punkt, do której można przywrócić repozytorium, w razie potrzeby. Każdym zatwierdzeniu może również sprawdzić w jego określonych zmian. Ponieważ niedrogich zatwierdzeń w usłudze Git, warto częste zatwierdzeń niż aby gromadzone dużej liczby zmian do jednego zatwierdzenia. Wyraźnie widać nie trzeba przekazać każdej zmiany mały do poszczególnych plików. Zazwyczaj należy zatwierdzenie podczas dodawania funkcji zmiana struktury, tak jak została wykonana w tym kroku lub wykonać niektóre refaktoryzacji kodu. Również sprawdzić z innymi osobami w zespół stopień szczegółowości zatwierdzeń, które najlepiej dla wszystkich użytkowników.

Jak często należy zatwierdzić i jak często wypychanie zatwierdzeń do repozytorium zdalnego są dwa różne problemy. Można zebrać wiele zatwierdzeń w lokalnym repozytorium przed wypchnięciem je do repozytorium zdalnego. Ponownie jak często zatwierdzić zależy od jak zespół chce zarządzać repozytorium.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Krok 2-2: Użyj szablonu do renderowania strony

`home` Funkcji, które należy do tej pory w `views.py` nie więcej niż odpowiedzi HTTP zwykłego tekstu dla strony. Jednak większość stron sieci web rzeczywistych odpowiadać, podając sformatowanego stron HTML, często zawierające dane na żywo. Podstawowym powodem zdefiniować widok przy użyciu funkcji jest w rzeczywistości dynamiczne generowanie zawartości.

Wartość zwracana dla widoku jest po prostu określonym ciągiem, można utworzyć zapasowej chcesz ciągu, przy użyciu zawartości dynamicznej kodu HTML. Jednak ponieważ najlepiej można oddzielić od danych znaczników, jest znacznie poprawia umieścić znaczniki w szablonie i przechowywać dane w kodzie.

1. Po pierwsze, Edytuj `views.py` zawiera następujący kod, który używa wbudowanego kodu HTML dla strony z niektórych dynamiczną zawartością:

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. Uruchom aplikację i Odśwież stronę za kilka razy czy daty/godziny jest aktualizowany. Gdy wszystko będzie gotowe, Zatrzymaj aplikację.

1. Aby przekonwertować renderowania strony, aby użyć szablonu, Utwórz plik o nazwie `index.html` w `templates` folderu o następującej zawartości, gdzie `{{ content }}` jest symbolu zastępczego lub zastąpienie tokenu (skrót *szablonu zmiennej*) dla której zostanie podana wartość w kodzie:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Modyfikowanie `home` funkcji należy użyć `render_template` do załadowania szablonu i podać wartość "zawartość", która jest wykonywane przy użyciu nazwanego argumentu pasującego do nazwy symbolu zastępczego. Flask automatycznie wyszukuje szablony w `templates` folderu, więc oath do szablonu jest określana względem tego folderu:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Uruchamianie aplikacji, zobacz wyników oraz że wbudowanego kodu HTML w `content` nie renderowania wartości *jako* HTML, ponieważ tworzenia szablonów aparat (Jinja) automatycznie specjalne zawartość HTML. Automatyczne anulowanie zapobiec przypadkowym luk w zabezpieczeniach na ataki iniekcji: deweloperów często zebranie danych wejściowych z jednej strony i używać go jako wartość w innym za pośrednictwem symbol zastępczy szablonu. Anulowanie służy również jako monitu, że jest ponownie najlepiej przechowywać poza kod HTML.

    W związku z tym Przejrzyj `templates\index.html` zawierać różne elementy zastępcze dla każdego elementu danych w ramach kod znaczników:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Następnie zaktualizuj `home` funkcji wartości dla wszystkich symboli zastępczych:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. Uruchom aplikację ponownie, aby zobaczyć dane wyjściowe odtwarzane poprawnie.

    ![Uruchomionej aplikacji przy użyciu szablonu](media/flask/step02-result.png)

1. Zatwierdź zmiany do kontroli źródła i zaktualizować zdalnego repozytorium, w razie potrzeby, zgodnie z opisem w [krok 2-1](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pytanie: czy szablony stron muszą być w oddzielnym pliku?

Odpowiedź: Mimo że szablony są zazwyczaj obsługiwane w oddzielnych plików HTML, umożliwia także szablonem wbudowanego. Użycie osobnego pliku jest zalecane, jednak do obsługi czyste rozdzielenie znaczników i kodu.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pytanie: szablony korzystać tylko z rozszerzeniem pliku HTML?

Odpowiedź: `.html` rozszerzeń plików szablonu strony jest opcjonalna, ponieważ zawsze zidentyfikować dokładną ścieżkę względną do pliku w pierwszy argument `render_template` funkcji. Jednak program Visual Studio (i innych edytory) zazwyczaj zapewnia funkcje, takie jak uzupełnianie i składni zabarwienie kodu z `.html` pliki, które przeważa nad fakt, że strona szablony nie są ściśle HTML.

W rzeczywistości podczas pracy z projektem Django, Visual Studio automatycznie wykrywa plik HTML, który jest edytowany jest rzeczywiście szablonu Django i zawiera pewnych funkcji automatycznego zakończenia. Na przykład po rozpoczęciu wprowadzania komentarz Django strony szablonu `{#`, Visual Studio automatycznie umożliwia zamknięcie `#}` znaków. **Zaznaczanie komentarzy** i **usuń znaczniki komentarza wybór** polecenia (na **Edytuj** > **zaawansowane** menu i na pasku narzędzi) komentarze szablonu należy również użyć zamiast komentarze HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Pytanie: Uruchomienie projektu, wyświetlany błąd, którego nie można odnaleźć szablonu. Co jest nie tak?

Odpowiedź: Jeśli wyświetlane błędy, których nie można znaleźć szablonu, upewnij się, dodaniu aplikacji do projektu Django `settings.py` w `INSTALLED_APPS` listy. Bez tego wpisu Django nie będzie wiedzieć do wyszukiwania w aplikacji `templates` folderu.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Pytanie: szablonów można podzielić na dalsze podfoldery?

Odpowiedź: Tak, można użyć podfoldery i odwoływać się do ścieżki względnej w obszarze `templates` w wywołaniach `render_template`. Jest to dobry sposób na efektywne tworzenie przestrzeni nazw dla szablonów.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Obsługi plików statycznych, Dodaj strony i użyj szablonu dziedziczenia](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- [Szybki Start flask - renderowania szablonów](http://flask.pocoo.org/docs/1.0/quickstart/#rendering-templates) (flask.pocoo.org)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowy — vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)