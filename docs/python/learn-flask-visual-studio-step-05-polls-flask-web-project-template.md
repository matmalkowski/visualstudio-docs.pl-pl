---
title: Samouczek — Dowiedz się Flask w programie Visual Studio, krok 5
description: Wskazówki dotyczące podstawy Flask w kontekście projektów programu Visual Studio, w szczególności funkcje szablonów projektu sieci Web platformy Flask ankiety i projektu sieci Web platformy Flask/Jade ankiety.
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
ms.openlocfilehash: c99dea00506fa838a2bb5c800fa05b7d55af3844
ms.sourcegitcommit: 4e605891d0dfb3ab83150c17c074bb98dba29d15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36947105"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Krok 5: Należy użyć szablonu projektu sieci Web platformy Flask sond

**Poprzedni krok: [użyj pełnego szablonu projektu sieci Web platformy Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Po zrozumieniu szablon "Projektu sieci Web platformy Flask" programu Visual Studio można teraz przyjrzeć się trzeci szablonu platformy Flask, "Sond Flask projektu sieci Web", która na podstawie tego samego kodu.

W tym kroku możesz dowiedzieć się, jak:

> [!div class="checklist"]
> - Utwórz projekt z szablonu i zainicjuj bazę danych (krok 5 - 1)
> - Zrozumienie modeli danych (krok 5-2)
> - Tworzenie kopii zapasowych danych magazynów i (krok 5-3)
> - Zrozumienie widoków szczegółów i wyniki sondowania (krok 5-4)

Visual Studio również projekcję szablonu "Projektu sieci Web platformy Flask/Jade sond", który daje identyczne aplikacji, ale używa Jade rozszerzenia dla aparatu tworzenia szablonów Jinja. Aby uzyskać więcej informacji, zobacz [krok 4 — szablon projektu sieci Web platformy Flask/Jade](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Krok 5-1: Tworzenie projektu

1. W programie Visual Studio, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie "LearningFlask" utworzona we wcześniejszej części tego samouczka i wybierz **Dodaj** > **nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz **pliku** > **nowy** > **projektu** zamiast.)

1. W oknie dialogowym Nowy projekt Wyszukaj i wybierz szablon "Projektu sieci Web platformy Flask sond", wywołaj projektu "FlaskPolls" i wybierz **OK**.

1. Podobnie jak inne szablony projektów programu Visual Studio zawiera szablon "Projektu sieci Web platformy Flask sond" `requirements.txt` pliku monity Visual Studio zapyta, gdzie do zainstalowania tych zależności. Wybierz opcję **zainstalować w środowisku wirtualnym**i w **Dodawanie środowiska wirtualnego** oknie dialogowym wybierz pozycję **Utwórz** zaakceptować wartości domyślne. (Ten szablon wymaga platformy Flask, jak również pakiety usługi azure storage i pymongo; "Sond Flask/Jade projektu sieci Web" wymaga również pyjade).

1. Ustaw projekt "FlaskPolls", aby być domyślne dla rozwiązania Visual Studio, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając **Ustaw jako projekt startowy**. Projekt startowy, który jest wyświetlany w bold, to co program jest uruchamiany w przypadku, gdy uruchamiasz debuger.

1. Wybierz **Debuguj > Rozpocznij debugowanie** (F5) lub użyj **serwera sieci Web** przycisk na pasku narzędzi do uruchomienia serwera:

    ![Uruchom serwer sieci web przycisku paska narzędzi w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikacji utworzonej przez szablon ma trzy strony, Home około i skontaktuj się z, której możesz przechodzić między za pomocą paska nawigacji top. Potrwać minutę lub dwie sprawdzać różne części aplikacji (informacje i skontaktuj się z strony są bardzo podobne do "Projekt sieci Web platformy Flask" i nie są omówione w dalszych).

    ![Pełny widok projektu sieci Web platformy Flask sond aplikacji](media/flask/step06-full-app-view.png)

1. Na stronie głównej **tworzenie przykładowej ankiety** przycisk inicjuje magazynu danych aplikacji z trzech różnych sond, które zostały opisane w `models/samples.json` strony. Domyślnie aplikacja używa w pamięci bazy danych (jak pokazano na stronie informacje), który jest resetowany każdym uruchomieniu aplikacji. Ta aplikacja zawiera również kodu do pracy z usługą Azure Storage i Mongo bazy danych, zgodnie z opisem w dalszej części tego artykułu.

1. Gdy magazyn danych został zainicjowany, jak pokazano na stronie głównej (paska nawigacji i stopki zostały pominięte w celu jego skrócenia) do głosowania w różnych sond:

    ![Widok aplikacji sond po zainicjować magazynu danych](media/flask/step06-polls-initialized.png)

1. Wybranie sonda powoduje wyświetlenie jej określonych opcji:

    ![Głosowanie w ankiecie — interfejs](media/flask/step06-polls-voting-interface.png)

1. Po głosowanie, powoduje wyświetlenie strony wyników i umożliwia głosowanie ponownie aplikacji:

    ![Widok wyników po głosowanie](media/flask/step06-polls-results.png)

1. Możesz pozostawić aplikacja uruchomiona w kolejnych sekcjach.

    Jeśli chcesz zatrzymać aplikację i [Zatwierdź zmiany do kontroli źródła](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), najpierw otwórz **zmiany** strony **Team Explorer**, kliknij prawym przyciskiem myszy folder (środowiska wirtualnego prawdopodobnie `env`) i wybierz **ignorować te elementy lokalne**.

### <a name="examine-the-project-contents"></a>Sprawdź zawartość projektu

Jak wspomniano przed. Większość co znajduje się w projekcie utworzone na podstawie szablonu "Projektu sieci Web platformy Flask sond" (i szablon "Projektu sieci Web platformy Flask/Jade sond") należy się zapoznać, jeśli zostały przedstawione innych szablonów projektu w programie Visual Studio. Dodatkowe kroki opisane w tym artykule podsumowanie bardziej znaczących zmian i dodatków, czyli modeli danych i dodatkowe widoki.

## <a name="step-5-2-understand-the-data-models"></a>Krok 5-2: zrozumienie modeli danych

Modeli danych aplikacji są klasy Python o nazwie sondowania i wyboru, które są zdefiniowane w `models/__init__.py`. Sonda reprezentuje zapytania, dla którego kolekcja wystąpień Choice reprezentują dostępne odpowiedzi. Sonda zachowuje również liczba głosów (dla dowolnej wybór) i metodę obliczania statystyk, które są używane do generowania widoków:

    ```python
    class Poll(object):
        """A poll object for use in the application views and repository."""
        def __init__(self, key=u'', text=u''):
            """Initializes the poll."""
            self.key = key
            self.text = text
            self.choices = []
            self.total_votes = None

        def calculate_stats(self):
            """Calculates some statistics for use in the application views."""
            total = 0
            for choice in self.choices:
                total += choice.votes
            for choice in self.choices:
                choice.votes_percentage = choice.votes / float(total) * 100 \
                    if total > 0 else 0
            self.total_votes = total

    class Choice(object):
        """A poll choice object for use in the application views and repository."""
        def __init__(self, key=u'', text=u'', votes=0):
            """Initializes the poll choice."""
            self.key = key
            self.text = text
            self.votes = votes
            self.votes_percentage = None
    ```

Te modele danych są ogólnego obiektów abstrakcyjnych, które widoki aplikacji do pracy dla różnych typów kopii magazyny danych, które opisano w następnym kroku.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Krok 5 — 3: zrozumienie tworzenie kopii zapasowych magazynów danych

Aplikacji utworzonej przez szablon "Projektu sieci Web platformy Flask sond" można uruchomić dla magazynu danych w pamięci, magazynu tabel platformy Azure lub Mongo DB bazy danych.

Mechanizm przechowywania danych działa w następujący sposób:

1. Typ repozytorium jest określany za pośrednictwem `REPOSITORY_NAME` zmiennej środowiskowej, który może być ustawiony na "pamięci", "azuretablestore" lub "mongodb". Bit kodu w `settings.py` pobiera ją za pomocą "pamięci" jako domyślny. Jeśli chcesz zmienić magazynu zapasowego, należy ustawić zmiennej środowiskowej i uruchom ponownie aplikację.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. `settings.py` Kodu następnie inicjuje `REPOSITORY_SETTINGS` obiektu. Jeśli chcesz używać magazynu tabel Azure lub Mondo bazy danych, należy najpierw zainicjować magazyny tych danych w innym miejscu, a następnie ustaw zmienne środowiskowe to konieczne, określające sposób nawiązywania połączenia ze sklepem aplikacji:

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. W `views.py`, aplikacja wywołuje metodę fabryki zainicjować `Repository` przy użyciu nazwy magazynu danych i ustawienia:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. `factory.create_repository` Metoda znajduje się w `models\factory.py`, który właśnie importuje moduł odpowiednie repozytorium, a następnie tworzy `Repository` wystąpienie:

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. Implementacje `Repository` klasy, które są specyficzne dla każdego magazynu danych można znaleźć w `models\azuretablestorage.py`, `models\mongodb.py`, i `models\memory.py`. Implementacja usługi Azure storage korzysta z pakietu usługi azure storage; Implementacja Mongo DB korzysta z pakietu pymongo. Zgodnie z opisem w kroku 5-1, oba pakiety znajdują się w szablonie projektu `requirements.txt` pliku. Eksploracja szczegóły pozostaje wykonywania dla czytnika.

Krótko mówiąc `Repository` klasy abstracts szczegółowych informacji o magazynie danych, a aplikacja używa zmiennych środowiskowych w czasie wykonywania do wybierz i skonfiguruj którego trzy implementacje do użycia.

Poniższe kroki obsługę magazynu danych innego niż trzech dostarczone przez szablon projektu, jeśli zaistnieje taka potrzeba:

1. Kopiuj `memory.py` do nowego pliku tak, aby mieć podstawowy interfejs dla `Repository` klasy.
1. Zmodyfikuj Implementacja klasy jako pasujące do magazynu danych, którego używasz.
1. Modyfikowanie `factory.py` Aby dodać kolejne `elif` przypadek, który rozpoznaje nazwę dla magazynu danych dodany, a następnie importuje odpowiedniego modułu.
1. Modyfikowanie `settings.py` rozpoznawanie inną nazwę w `REPOSITORY_NAME` zmiennej środowiskowej i zainicjować `REPOSITORY_SETTINGS` odpowiednio.

### <a name="seed-the-data-store-from-samplesjson"></a>Magazyn danych z samples.json inicjatora

Początkowo dowolnego wybranego danych magazynu zawiera nie sond, strona główna aplikacji zawiera komunikat "Nie sond dostępne" wraz z programem **tworzenie przykładowej ankiety** przycisku. Po wybraniu przycisku, natomiast widok zmiany do wyświetlania ankiety dostępne. Ten przełącznik odbywa się w ramach warunkowego tagów w `templates\index.html` (niektóre puste wiersze pominąć w przypadku skrócenia):

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <h2>{{title}}.</h2>

    {% if polls %}
    <table class="table table-hover">
        <tbody>
            {% for poll in polls %}
            <tr>
                <td>
                    <a href="/poll/{{poll.key}}">{{poll.text}}</a>
                </td>
            </tr>
            {% endfor %}
        </tbody>
    </table>
    {% else %}
    <p>No polls available.</p>
    <br />
    <form action="/seed" method="post">
        <button class="btn btn-primary" type="submit">Create Sample Polls</button>
    </form>
    {% endif %}
    {% endblock %}
    ```

`polls` Zmiennej w szablonie pochodzi z wywołania `repository.get_polls`, która nie zwraca żadnego dopóki zainicjować magazynu danych.

Wybieranie **tworzenie przykładowej ankiety** przycisku powoduje przejście do adresu URL /seed. Program obsługi trasy, jest zdefiniowany w `views.py`:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

Wywołanie `repository.add_sample_polls()` kończy się w jednej z konkretnych `Repository` implementacje sklepu wybranych danych. Każda implementacja wywołuje `_load_samples_json` znaleziono metody w `models\__init__.py` załadować `models\samples.json` plików do pamięci, a następnie iteruje danych do utworzenia niezbędnych `Poll` i `Choice` obiektów w magazynie danych.

Po zakończeniu tego procesu `redirect('/')` instrukcji w `seed` metody nawiguje wstecz do strony głównej. Ponieważ `repository.get_polls` teraz zwraca obiekt danych warunkowego tagów w `templates\index.html` teraz renderuje tabelę zawierającą ankiety.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Pytanie: Jak jedną dodaje nowe sond do aplikacji?

Odpowiedź: Aplikacji zgodnie z szablonu projektu nie zawiera funkcje w celu dodawania lub edytowania ankiety. Można zmodyfikować `models\samples.json` Aby utworzyć nowe dane inicjowania, ale oznacza spowoduje zresetowanie magazynu danych. Aby zaimplementować funkcje edycji, należy rozszerzyć `Repository` interfejsu klasy z metod, aby utworzyć niezbędne `Choice` i `Poll` wystąpień, następnie implementacji interfejsu użytkownika w dodatkowych stron korzystających z tych metod.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Krok 5 — 4: zrozumienie sondowania widoków szczegółów i wyniki

Większość widoków generowane przez Szablony "Projektu sieci Web platformy Flask sond" i "Projektu sieci Web platformy Flask/Jade sond", takich jak widoki informacje i skontaktuj się z stron, są bardzo podobne do widoków tworzone przez szablon "Projekt sieci Web platformy Flask" (lub "Projekt sieci Web platformy Flask/Jade"), pracy z wcześniej w tym samouczku. W poprzedniej sekcji również znasz implementowania strony głównej pokazanie przycisk inicjowania lub listy sondowania.

Co pozostaje w tym miejscu jest zbadanie głosowania (szczegóły) oraz widok wyników poszczególnych sondowania.

Po wybraniu sonda ze strony głównej aplikacji przechodzi do adresu URL /poll/\<klucza\> gdzie *klucza* jest unikatowego identyfikatora w ankiecie. W `views.py` można stwierdzić, że `details` funkcji jest przypisany do obsługi tego adresu URL routingu żądań i GET. Możesz też sprawdzić, które używają `<key>` w adresie URL trasy zarówno mapuje żadnej trasy formularza na taką samą funkcję i generuje argument do funkcji o tej samej nazwie:

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

Pokazanie sondowania (żądania GET), funkcja ta po prostu wywołuje na `templates\details.html`, który przechodzi przez sondowania `choices` tablicy i tworzenia przycisku radiowego dla każdej.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

Ponieważ **głos** przycisk ma `type="submit"`, zaznaczając go generuje żądanie POST do tego samego adresu URL, który jest kierowany do `details` funkcji raz. Teraz, jednak wyodrębnia wybór z danych formularza i przekierowuje do /results/\<wybór\>.

/Results/\<klucza\> adres URL jest następnie przekierowywane do `results` działać w `views.py`, który następnie wywołuje sondowania `calculate_stats` — metoda i wymaga `templates\results.html` do renderowania:

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

`results.html` Szablonu ze swojej strony, po prostu iteruje opcji sondowania i generuje pasek postępu dla każdego:

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>Następne kroki

> [!Note]
> Jeśli do kontroli źródła w toku w tym samouczku zostały zostały zatwierdzania rozwiązania Visual Studio, teraz jest odpowiedni moment, aby czy innego zatwierdzania. Rozwiązanie powinno być zgodne kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowy — vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Teraz zostały przedstawione całości szablony "Pusty projekt sieci Web platformy Flask", "Projekt sieci Web platformy Flask [/Jade]" i "Sond projektu sieci Web platformy Flask [/Jade]" w programie Visual Studio. Samouczka podstawy platformy Flask, takich jak routing i korzystanie z widoków, szablony i jak już wspomniano sposób użycia tworzenie kopii zapasowych magazynów danych. Teraz można rozpocząć pracę w aplikacji sieci web własne z widoków i modeli, które są potrzebne.

Uruchamianie aplikacji sieci web na komputerze dewelopera jest tylko jeden krok w zakresie udostępniania aplikacji dla klientów. Następne kroki mogą obejmować następujące zadania:

- Wdrażanie aplikacji sieci web na serwerze produkcyjnym, takie jak usługi Azure App Service. Zobacz [publikowania w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md), która obejmuje zmiany wymagane dla aplikacji platformy Flask.

- Dodaj implementację repozytorium, który używa innego magazynu danych na poziomie produkcji, takich jak PostgreSQL, MySQL i SQL Server (które może być hostowana na platformie Azure). Można również użyć [zestaw Azure SDK for Python](azure-sdk-for-python.md) do pracy z usług magazynu Azure, takich jak tabele i obiekty BLOB, a także DB rozwiązania Cosmos.

- Skonfiguruj potok ciągłej integracji/ciągłego wdrażania od usługi, takie jak Visual Studio Team Services (VSTS). Oprócz pracy z kontroli źródła (na VSTS, GitHub lub gdziekolwiek indziej), może mieć VSTS automatycznie uruchom testy jednostkowe jako warunek wstępny dla wersji, a także skonfigurować do wdrożenia na serwerze tymczasowym dla dodatkowych testów przed wdrożeniem w potoku produkcji. VSTS, ponadto integruje się z monitorowania rozwiązań, takich jak usługi App Insights i zamyka cały cykl z elastyczne narzędzia planowania. Aby uzyskać więcej informacji, zobacz:

  - [Tworzenie potoku CI/CD dla języka Python z projektem Azure DevOps](/vsts/build-release/apps/cd/azure/azure-devops-project-python?view=vsts)
  - [Programowanie Python w platformie Azure za pomocą programu Visual Studio Team Services (11m wideo, 21s)](https://azure.microsoft.com/resources/videos/connect-2017-python-development-in-azure-with-visual-studio-team-services/).
