---
title: Samouczek — Dowiedz się Django w programie Visual Studio, krok 6
description: Wskazówki dotyczące podstawy Django w kontekście projektów programu Visual Studio, w szczególności funkcje szablonu projektu sieci Web Django ankiety, takich jak administracyjne dostosowywania.
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
ms.openlocfilehash: 78cb5f54994c24fcf79f81fd6eff31eedd884908
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691449"
---
# <a name="tutorial-step-6-use-the-polls-django-web-project-template"></a>Samouczek krok 6: należy użyć szablonu projektu sieci Web Django sond

**Poprzedni krok: [uwierzytelniania użytkowników w Django](learn-django-in-visual-studio-step-05-django-authentication.md)**

Po zrozumieniu szablon "Projektu sieci Web Django" programu Visual Studio można teraz przyjrzeć się trzeci szablon Django, "Sond Django projektu sieci Web", który bazując na podstawie tego samego kodu i pokazuje pracy z bazą danych.

W tym kroku możesz dowiedzieć się, jak:

> [!div class="checklist"]
> - Utwórz projekt z szablonu i zainicjuj bazę danych (krok 6 - 1)
> - Zrozumienie modeli danych (krok 6-2)
> - Zastosuj migracje (krok 6-3)
> - Widoki i szablony strony utworzone przez szablon projektu (krok 6-4)
> - Tworzenie niestandardowych administracji interfejsu (krok 6-5)

Projekt utworzony przy użyciu tego szablonu jest podobny do pobrania, postępując [pisanie pierwszej aplikacji Django](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) samouczka w Django docs. Aplikacja sieci web składa się z witryną publiczną, informując wyświetlania ankiety i głosu, wraz z niestandardowego interfejsu administracyjnego za pomocą którego można zarządzać ankiety. Używa tego samego systemu uwierzytelniania jako szablon "Projektu sieci Web Django", a wykorzystuje więcej bazy danych dzięki implementacji modele Django jako eksplorowanych w poniższych sekcjach.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Krok 6 — 1: Tworzenie projektu i zainicjuj bazę danych

1. W programie Visual Studio, przejdź do **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie "LearningDjango" utworzona we wcześniejszej części tego samouczka i wybierz **Dodaj** > **nowy projekt**. (Alternatywnie, jeśli chcesz użyć nowego rozwiązania, wybierz **pliku** > **nowy** > **projektu** zamiast.)

1. W oknie dialogowym Nowy projekt Wyszukaj i wybierz szablon "Projektu sieci Web Django sond", wywołaj projektu "DjangoPolls" i wybierz **OK**.

1. Podobnie jak inne szablony projektów programu Visual Studio zawiera szablon "Projektu sieci Web Django sond" `requirements.txt` pliku monity Visual Studio zapyta, gdzie do zainstalowania tych zależności. Wybierz opcję **zainstalować w środowisku wirtualnym**i w **Dodawanie środowiska wirtualnego** oknie dialogowym wybierz pozycję **Utwórz** zaakceptować wartości domyślne.

1. Po zakończeniu konfigurowania środowiska wirtualnego Python postępuj zgodnie z instrukcjami wyświetlone `readme.html` do inicjowania bazy danych i Utwórz użytkownika super Django (administrator). Kroki są najpierw kliknij prawym przyciskiem myszy projekt "DjangoPolls" w **Eksploratora rozwiązań**, wybierz pozycję **Python** > **Django migracji** polecenia następnie ponownie kliknij projekt prawym przyciskiem myszy, wybierz **Python** > **Django utworzyć administratora** polecenia, a następnie postępuj zgodnie z monitami. (Jeśli spróbujesz się najpierw Utwórz użytkownika nadrzędnego, zobaczysz wystąpił błąd, ponieważ baza danych nie została zainicjowana.)

1. Ustaw projekt "DjangoPolls", aby być domyślne dla rozwiązania Visual Studio, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając **Ustaw jako projekt startowy**. Projekt startowy, który jest wyświetlany w bold, to co program jest uruchamiany w przypadku, gdy uruchamiasz debuger.

1. Wybierz **Debuguj > Rozpocznij debugowanie** (F5) lub użyj **serwera sieci Web** przycisk na pasku narzędzi do uruchomienia serwera:

    ![Uruchom serwer sieci web przycisku paska narzędzi w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikacji utworzonej przez szablon ma trzy strony, Home około i skontaktuj się z, której możesz przechodzić między za pomocą paska nawigacji top. Potrwać minutę lub dwie sprawdzać różne części aplikacji (informacje i skontaktuj się z strony są bardzo podobne do "Projekt sieci Web Django" i nie są omówione w dalszych).

    ![Widok przeglądarki pełnej aplikacji projektu sieci Web Django sond](media/django/step06-full-app-view.png)

1. Wybierz również **administracji** łącze w pasku nawigacyjnym, który wyświetla ekran logowania, aby pokazać, że interfejsu administracyjnego jest tylko do autoryzowanych uwierzytelniony Administratorzy. Użyj poświadczeń administratora i są kierowane do "/ admin" strony, która jest włączona domyślnie w przypadku korzystania z tego szablonu projektu.

    ![Administracyjne widok projektu sieci Web Django sond aplikacji](media/django/step06-polls-administrative-interface.png)

1. Możesz pozostawić aplikacja uruchomiona w kolejnych sekcjach.

    Jeśli chcesz zatrzymać aplikację i [Zatwierdź zmiany do kontroli źródła](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), najpierw otwórz **zmiany** strony **Team Explorer**, kliknij prawym przyciskiem myszy folder (środowiska wirtualnego prawdopodobnie `env`) i wybierz **ignorować te elementy lokalne**.

### <a name="examine-the-project-contents"></a>Sprawdź zawartość projektu

Jak wspomniano przed. Większość co znajduje się w projekcie utworzone na podstawie szablonu "Projektu sieci Web Django sond" należy się zapoznać, jeśli zostały przedstawione innych szablonów projektu w programie Visual Studio. Dodatkowe kroki opisane w tym artykule podsumowanie bardziej znaczących zmian i dodatków, czyli modeli danych i dodatkowe widoki.

### <a name="question-what-does-the-django-migrate-command-do"></a>Pytanie: czego polecenia Django migracji?

Odpowiedź: **migracji Django** polecenia w szczególności `manage.py migrate` polecenia, które uruchamia wszystkie skrypty w `app/migrations` folderów, które nie zostały wcześniej uruchomione. W takim przypadku polecenie jest uruchamiane `0001_initial.py` skryptu w tym folderze, aby skonfigurować wymagane schematu w bazie danych.

Sam skrypt migracji jest tworzony przez `manage.py makemigrations` polecenia, które skanuje aplikacji `models.py` pliku, porównuje go do bieżącego stanu bazy danych, a następnie generuje skrypty niezbędne do migracji schematu bazy danych do dopasowania bieżących modeli. Ta funkcja Django jest bardzo zaawansowaną jako aktualizacji i zmodyfikować modeli wraz z upływem czasu. Generowanie i uruchamiając migracji, możesz synchronizowania modeli i bazy danych w niewielkim nakładem pracy.

Możesz pracować z migracji w kroku 6-3 w dalszej części tego artykułu.

## <a name="step-6-2-understand-data-models"></a>Krok 6-2: zrozumienie modeli danych

Modele dla aplikacji o nazwie sondowania i wyboru, są zdefiniowane w `app/models.py`. Każdy z nich jest klasa Python, która pochodzi z `django.db.models.Model` i używa metody `models` klas takich jak `CharField` i `IntegerField` do definiowania pola w modelu, które mapują kolumny bazy danych.

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

Jak widać, sonda przechowuje opis w jego `text` pola i publikacji Data w `pub_date`. Te pola są tylko onesields, który istnieje dla sondowania w bazie danych. `total_votes` pola jest obliczane w czasie wykonywania.

Wybór jest powiązany z sondowania za pośrednictwem `poll` pola, zawiera opis `text`i obsługuje liczba dla tej opcji w `votes`. `votes_percentage` Pola jest obliczane w czasie wykonywania i nie można odnaleźć w bazie danych.

Pełna lista typów pól jest `CharField` (ograniczoną tekst) `TextField` (nieograniczone tekst), `EmailField`, `URLField`, `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, `ForeignKey`, i `ManyToMany`. Każde pole ma niektóre atrybuty, takie jak `max_length`. `blank=True` Atrybut oznacza, że pole jest opcjonalne; `null=true` oznacza, że wartość jest opcjonalna. Istnieje również `choices` atrybut, który ogranicza wartości do wartości w tablicy krotek wartość wartość/wyświetlania danych. (Zobacz [modelu odwołania pola](https://docs.djangoproject.com/en/2.0/ref/models/fields/) w dokumentacji Django.)

Można potwierdzić dokładnie co to są przechowywane w bazie danych, sprawdzając `db.sqlite3` plik w projekcie przy użyciu narzędzia, takiego jak [przeglądarki SQLite](http://sqlitebrowser.org/). W bazie danych, zobaczysz, że pole klucza obcego, takich jak `poll` w wyborze modelu jest przechowywana jako `poll_id`; Mapowanie programu obsługi Django automatycznie.

Ogólnie rzecz biorąc pracy z bazy danych w Django oznacza, że działa wyłącznie za pośrednictwem modeli tak, aby zarządzać Django podstawowej bazy danych w Twoim imieniu.

### <a name="seed-the-database-from-samplesjson"></a>Inicjatora bazy danych z samples.json

Baza danych zawiera początkowo nie ankiety. Można użyć interfejsu administracyjnego w "/ admin" adres URL, aby dodać sonduje ręcznie, a można też odwiedź stronę "/ nasion" w uruchomionej lokacji można dodać inicjatora bazy danych z sond zdefiniowanych w aplikacji `samples.json` pliku.

Projekt Django `urls.py` został dodany wzorzec URL `url(r'^seed$', app.views.seed, name='seed'),`. `seed` Wyświetlić w `app/views.py` ładuje `samples.json` plików i tworzy obiekty niezbędne modelu. Django następnie automatycznie tworzy pasujące rekordy w bazie danych.

Zwróć uwagę na użycie `@login_required` dekoratora, aby wskazać poziom dostępu dla widoku.

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

Aby zobaczyć efekt, uruchom aplikację, aby dowiedzieć się, że nie sond jeszcze istnieje. Następnie odwiedź adres URL "/ nasion", i gdy aplikacja powróci do strony głównej należy sprawdzić, czy sond stały się dostępne. Ponownie, możesz także zbadać nieprzetworzonego `db.sqlite3` pliku z narzędzia, takiego jak [przeglądarki SQLite](http://sqlitebrowser.org/).

![Ankiety aplikacji projektu sieci Web Django z wprowadzonych bazy danych](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Pytanie: czy można zainicjować bazy danych wykorzystuje narzędzia administracyjnego Django?

Odpowiedź: Tak, można użyć [polecenia metody loaddata django admin](https://docs.djangoproject.com/en/1.9/ref/django-admin/#loaddata) do wykonania tych samych zadań rozmieszczania strony w aplikacji. Podczas pracy w aplikacji sieci web pełną, można użyć kombinacji dwóch metod: Zainicjuj bazę danych w wierszu polecenia, a następnie przekonwertować stronie inicjatora tutaj do interfejsu API, który możesz wysłać innych dowolnego JSON, a nie jednostki uzależnionej w pliku ustalony.

## <a name="step-6-3-use-migrations"></a>Krok 6-3: Użyj migracji

Po uruchomieniu `manage.py makemigrations` poleceń (przy użyciu menu kontekstowego w programie Visual Studio) po utworzeniu projektu, Django utworzony plik `app/migrations/0001_initial.py` pliku. Ten plik zawiera skrypt, który tworzy tabele początkowej bazy danych.

Ponieważ będzie natychmiastową wprowadzania zmian w modelach w czasie program Django ułatwia aktualności podstawowy schemat bazy danych z tych modeli. Ogólny przepływ pracy jest następujący:

1. Wprowadź zmiany do modeli w Twojej `models.py` pliku.
1. W programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Python** > **Django dokonać migracji** polecenia. Jak opisano wcześniej, to polecenie generuje skryptów w `app/migrations` do migracji bazy danych z bieżącego stanu na nowy stan.
1. Aby zastosować skrypty rzeczywistej bazy danych, ponownie kliknij prawym przyciskiem myszy projekt i wybierz **Python** > **migracji Django**.

Django śledzi migracji, które zostały zastosowane do każdej danego bazy danych tak, aby po uruchomieniu polecenia migracji ma zastosowanie Django, niezależnie od migracji są potrzebne. Jeśli tworzysz nową, pustą bazę danych, na przykład uruchomienie polecenia migracji aktualizuje na bieżąco z modelami bieżącego użytkownika, stosując każdego skryptu migracji. Podobnie jeśli wiele zmian modelu i generowanie migracje na komputerze dewelopera, aby potem stosować je zbiorczą migracje do bazy danych produkcyjnej, uruchamiając polecenie migracji na serwerze produkcyjnym. Django ponownie dotyczy tylko te skrypty migracji, które zostały wygenerowane od czasu ostatniej migracji w produkcyjnej bazie danych.

Aby zobaczyć efekt zmian modelu, spróbuj wykonać następujące kroki:

1. Dodaj pole opcjonalne autora do modelu sondowania w `app/models.py` , dodając następujący wiersz po `pub_date` pole, aby dodać opcjonalne `author` pola:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Zapisz plik, a następnie kliknij prawym przyciskiem myszy projekt "DjangoPolls" w **Eksploratora rozwiązań** i wybierz **Python** > **Django dokonać migracji** polecenia.
1. Wybierz **projektu** > **Pokaż wszystkie pliki** polecenie, aby wyświetlić nowo wygenerowany skrypt w `migrations` folder, w których nazwa rozpoczyna się od `002_auto_`. Kliknij prawym przyciskiem myszy, tego pliku, a następnie wybierz **załącz do projektu**. Następnie możesz wybrać **projektu** > **Pokaż wszystkie pliki** ponownie w celu przywrócenia oryginalnego widoku. (Zobacz drugie pytanie poniżej, aby uzyskać więcej informacji na ten krok).
1. W razie potrzeby otwórz ten plik, aby sprawdzić, jak Django skrypty zmian z poprzedniego stanu modelu do nowego stanu.
1. Ponownie kliknij prawym przyciskiem myszy projekt programu Visual Studio i wybierz **Python** > **Django migracji** zastosować zmiany wprowadzone w bazie danych.
1. W razie potrzeby można otworzyć bazy danych w odpowiednich podglądu, aby potwierdzić zmianę.

Ogólnie funkcji migracji w Django oznacza, że nigdy nie należy zarządzać schemat bazy danych ręcznie. Wystarczy wprowadzić zmiany w modelach, generowania skryptów migracji i zastosować je przy użyciu polecenia migracji.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Pytanie: co się stanie w przypadku zapomnienia o uruchomienie polecenia migracji po wprowadzeniu zmian w modelach?

Odpowiedź: Jeśli modele nie są zgodne, co znajduje się w bazie danych, Django zakończy się niepowodzeniem w czasie wykonywania odpowiednich wyjątków. Na przykład, Jeśli zapomnisz migracji zmiany modelu w poprzedniej sekcji, zostanie wyświetlony błąd "nie takich kolumn: app_poll.author":

![Błąd wyświetlany, gdy nie wykonano migracji zmiany modelu](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Pytanie: Dlaczego skrypty Pokaż nowo wygenerowane Eksplorator rozwiązań po zakończeniu migracji należy Django?

Odpowiedź: Mimo że nowo wygenerowanych skryptów istnieje w `app/migrations` folderu i są stosowane podczas uruchamiania **migracji Django** poleceń, nie pojawiają się automatycznie w **Eksploratora rozwiązań** ponieważ nie zostali dodani do projektu programu Visual Studio. Aby je wyświetlić, najpierw wybierz **projektu** > **Pokaż wszystkie pliki** polecenia menu lub przycisku paska narzędzi przedstawione na poniższej ilustracji. To polecenie powoduje **Eksploratora rozwiązań** Aby wyświetlić wszystkie pliki w folderze projektu przy użyciu ikony kropkowanej konspektu dla elementów, które nie zostały dodane do projektu. Kliknij prawym przyciskiem myszy pliki chcesz dodać, a następnie wybierz **załącz do projektu**, który zawiera również je w kontroli źródła z Twoje następne zatwierdzenie.

![Dołączenie polecenia Projekt w Eksploratorze rozwiązań](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Pytanie: czy można wyświetlić migracji, które mają zostać zastosowane przed uruchomieniem polecenia migracji?

Odpowiedź: Tak, [django — administrator showmigrations polecenia](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 6 — 4: omówienie widoki i szablony utworzone przez szablon projektu strony

Większość widoków generowane przez szablon "Projektu sieci Web Django sond", takich jak widoki informacje i skontaktuj się z stron, są bardzo podobne do widoków tworzone przez szablon "Projekt sieci Web Django" doświadczenie z wcześniej w tym samouczku. Co to jest inna w sond aplikacja jest, że jego strony głównej korzysta z modeli, jak kilka dodać stron do głosowania i wyświetlania wyników ankiety.

Najpierw pierwszy wiersz w projekcie Django `urlpatterns` tablicy w `urls.py` plik jest więcej niż tylko proste routing do widoku aplikacji. Zamiast tego ściągania w własnych aplikacji `urls.py` pliku:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

`app/urls.py` Plik zawiera następnie niektórych bardziej interesującego rozliczeniowy (dodać komentarze wyjaśniające):

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

Jeśli nie masz doświadczenia w obsłudze bardziej złożonych wyrażeń regularnych używane w tym miejscu, można wkleić wyrażenia w [regex101.com](https://regex101.com/) wyjaśnienie przy użyciu prostego języka. (Należy wprowadzić kreskami ukośnymi `/` przez dodanie kreski ułamkowej odwróconej `\` poprzedzających; anulowanie nie jest konieczne w języku Python z powodu `r` prefiks na ciąg, co oznacza "nieprzetworzonej").

W Django, składnia `?P<name>pattern` tworzy grupę o nazwie `name`, które jest przekazywane jako argumenty do widoków w kolejności ich występowania. W kodzie przedstawiona wcześniej `PollsDetailView` i `PollsResultsView` odbierania argument o nazwie `pk` i `app.views.vote` odbiera argument o nazwie `poll_id`.

Możesz również sprawdzić, czy większość widoków nie są po prostu bezpośrednie odwołania do funkcji widoku w `app/views.py`. Jednak większość odwoływać się do klasy, w tym samym pliku, który pochodzi z `django.views.generic.ListView` lub `django.views.generic.DetailView`. Klasy podstawowe podaj `as_view` metod, które biorą `template_name` argumentu, aby zidentyfikować szablon. `ListView` Klasy podstawowej jako przeznaczoną do strony głównej również oczekuje `queryset` Właściwość zawierająca dane i `context_object_name` właściwość o nazwie zmiennej, przez którą ma odwoływać się do danych w szablonie, w tym przypadku `latest_poll_list`.

Teraz możesz zbadać `PollListView` strony głównej, która jest zdefiniowana w następujący sposób `app/views.py`:

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

Wszystkie punkty, które ma wykonać w tym miejscu jest zidentyfikowanie model, widok współpracuje z (sondowania), która zastępuje `get_context_data` metody w celu dodania `title` i `year` wartości w kontekście.

Podstawowe szablonu (`templates/app/index.html`) wygląda następująco:

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

Po prostu umieść, szablon otrzymuje listę obiektów sondowania w `latest_poll_list`, a następnie wykonuje iterację tej listy, aby utworzyć wiersza tabeli, która zawiera link do każdego sondowania przy użyciu sondowania `text` wartość. W `{% url %}` tagu "app:detail" odwołuje się do wzorca adresu url w `app/urls.py` o nazwie "szczegóły", przy użyciu `poll.id` jako argument. W rezultacie jest Django tworzy adres URL przy użyciu odpowiednich wzorca oraz użyty dla łącza. Ten bit oznacza sprawdzające w przyszłości, można zmienić tego wzorca adresu URL w dowolnym momencie i linki wygenerowany automatycznie zaktualizować do dopasowania.

`PollDetailView` i `PollResultsView` klas w `app/views.py` (nie jest tutaj widoczny) Szukaj niemal identyczny `PollListView` z tą różnicą, że pochodzą one od `DetailView` zamiast tego. Ich odpowiednich szablony `app/templates/details.html` i `app/templates/results.html` umieścić odpowiednie pola z modeli w różnych kontrolek HTML. Jeden unikatowy zestaw w `details.html` jest, że wyborów w ankiecie są zawarte w tworzą kodu HTML, który po zatwierdzeniu jest POST na adres URL /vote. Jak pokazano wcześniej, że wzorzec URL jest kierowany do `app.views.vote`, która jest zaimplementowana w następujący sposób (Uwaga `poll_id` argumentu, który jest ponownie nazwaną grupę w wyrażeniu regularnym używany podczas routingu dla tego widoku):

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

W tym miejscu widoku nie ma własną odpowiedniego szablonu, takie jak innych stron. Zamiast tego jest sprawdzane wybrane sondowania, przedstawiający 404, jeśli sondowania nie istnieje (tylko w przypadku, gdy ktoś wpisze adres URL takich jak "głos/1a2b3c"). Następnie pozwala sprawdzić wybór voted jest prawidłowe dla sondowania. Jeśli nie, `except` blok po prostu renderuje strony szczegółów ponownie z komunikatem o błędzie. Jeśli opcja jest prawidłowa, widok zlicza głosowania i przekierowuje do strony wyników.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Krok 6-5: Tworzenie interfejsu niestandardowe administracji

Ostatniej części szablonu "Projektu sieci Web Django sond" są rozszerzenia niestandardowe dla domyślnego Django interfejsu administracyjnego, jak pokazano wcześniej w tym artykule w kroku 6-1. Udostępnia domyślny interfejs dla użytkowników i grupy zarządzania, ale nic więcej. Szablon projektu sond dodaje funkcje, które umożliwiają zarządzanie również ankiety.

Po pierwsze, adres URL wzorce w projekcie Django `urls.py` ma `url(r'^admin/', include(admin.site.urls)),` uwzględnione domyślnie; wzorzec "admin/doc" znajduje się również przez oznaczone jako komentarz.

Ta aplikacja zawiera następnie plik `admin.py`, Django uruchamiany automatycznie podczas odwiedzania interfejs administracyjny dzięki użyciu włączenia `django.contrib.admin` w `INSTALLED_APPS` tablicę `settings.py`. Kod w tym pliku, dostarczone przez szablon projektu jest następujący:

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

Jak widać, `PollAdmin` pochodną klasy `django.contrib.admin.ModelAdmin` i dostosowuje liczbę pól przy użyciu nazwy z `Poll` modelu, który zarządza. Te pola są opisane na [opcje ModelAdmin](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) w dokumentacji Django.

Wywołanie `admin.site.register` tej klasy łączy się następnie z modelu (`Poll`) i dołącza go w interfejsie administratora. Poniżej przedstawiono wynik ogólny:

![Administracyjne widok projektu sieci Web Django sond aplikacji](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Następne kroki

> [!Note]
> Jeśli do kontroli źródła w toku w tym samouczku zostały zostały zatwierdzania rozwiązania Visual Studio, teraz jest odpowiedni moment, aby czy innego zatwierdzania. Rozwiązanie powinno być zgodne kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowy — vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Teraz zostały przedstawione całości "Pusty projekt sieci Web Django", "Projekt sieci Web Django" i "Projektu sieci Web Django sond" szablonów w programie Visual Studio. Samouczka podstawy Django, takich jak przy użyciu widoków i szablonów i zostały przedstawione routingu, uwierzytelnianie i przy użyciu modelu bazy danych. Teraz można utworzyć aplikację sieci web własny z widoków i modeli, które są potrzebne.

Uruchamianie aplikacji sieci web na komputerze dewelopera jest tylko jeden krok w zakresie udostępniania aplikacji dla klientów. Następne kroki mogą obejmować następujące zadania:

- Dostosowywanie strony 404, tworząc szablon o nazwie `templates/404.html`. Jeśli jest obecny, Django korzysta z tego szablonu zamiast jego domyślny. Aby uzyskać więcej informacji, zobacz [widoków błąd](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) w dokumentacji Django.

- Pisanie testów jednostkowych `tests.py`; szablony projektu Visual Studio stanowią punkt wyjścia dla tych i więcej informacji można znaleźć w [pisanie pierwszej aplikacji Django, część 5 - testowania](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) i [testowania w Django](https://docs.djangoproject.com/en/2.0/topics/testing/) w dokumentacji Django.

- Wdrażanie aplikacji sieci web na serwerze produkcyjnym, takie jak usługi Azure App Service. Zobacz [publikowania w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md), która obejmuje zmiany wymagane dla aplikacji Django.

- Zmień aplikacji z bazy danych SQLite w magazynie danych poziom produkcji, takich jak PostgreSQL, MySQL i SQL Server (które może być hostowana na platformie Azure). Zgodnie z opisem na [użycie SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org), SQLite działa prawidłowo, do małej witryn średnia ruchu z mniej niż 100 KB trafień/dzień, ale nie jest zalecane w przypadku większej ilości. Istnieje również ograniczone do jednego komputera, więc nie można w jakimkolwiek scenariuszu wielu serwerów, takie jak Równoważenie obciążenia i replikację geograficzną. Informacji na temat obsługi Django w innych baz danych, zobacz [konfiguracji bazy danych](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Można również użyć [zestaw Azure SDK for Python](azure-sdk-for-python.md) do pracy z usług magazynu Azure, takich jak tabele i obiektów blob.

- Skonfiguruj potok ciągłej integracji/ciągłego wdrażania od usługi, takie jak Visual Studio Team Services (VSTS). Oprócz pracy z kontroli źródła (na VSTS, GitHub lub gdziekolwiek indziej), może mieć VSTS automatycznie uruchom testy jednostkowe jako warunek wstępny dla wersji, a także skonfigurować do wdrożenia na serwerze tymczasowym dla dodatkowych testów przed wdrożeniem w potoku produkcji. VSTS, ponadto integruje się z monitorowania rozwiązań, takich jak usługi App Insights i zamyka cały cykl z elastyczne narzędzia planowania. Aby uzyskać więcej informacji, zobacz:

  - [Tworzenie potoku CI/CD dla języka Python z projektem Azure DevOps](/vsts/build-release/apps/cd/azure/azure-devops-project-python?view=vsts)
  - [Programowanie Python w platformie Azure za pomocą programu Visual Studio Team Services (11m wideo, 21s)](https://azure.microsoft.com/resources/videos/connect-2017-python-development-in-azure-with-visual-studio-team-services/).

