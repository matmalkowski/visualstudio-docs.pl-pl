---
title: Samouczek — Dowiedz się Django w programie Visual Studio, krok 2
description: Wskazówki dotyczące podstawy Django w kontekście projektów programu Visual Studio, w szczególności kroki tworzenia aplikacji i przy użyciu widoków i szablonów.
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
ms.openlocfilehash: 1a9d878ee8b5384784ba77cb6de2d9eee1289d0c
ms.sourcegitcommit: cc88ccc6aacebe497899fab05d243a65053e194c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="tutorial-step-2-create-a-django-app-with-views-and-page-templates"></a>Samouczek krok 2: tworzenie aplikacji Django z widokami i strony szablonów

**Poprzedni krok: [tworzenia projektu Visual Studio i rozwiązania](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Co masz wykonanej do tej pory w projekt programu Visual Studio są tylko składniki poziomie witryny Django *projektu*, który można uruchomić co najmniej jeden Django *aplikacji*. Następnym krokiem jest tworzenie pierwszej aplikacji za pomocą pojedynczej strony.

W tym kroku teraz dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie aplikacji Django za pomocą pojedynczej strony (krok 2 - 1)
> - Uruchamianie aplikacji z projektu Django (krok 2-2)
> - Renderowania widoku przy użyciu języka HTML (krok 2 – 3)
> - Renderowania widoku, używając szablonu strony Django (krok 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Krok 2 — 1: tworzenie aplikacji z domyślnej struktury

Aplikacja Django jest oddzielny pakiet języka Python, zawierający zestaw plików powiązanych z określonym przeznaczeniem. Projekt Django może zawierać dowolną liczbę aplikacji, która odzwierciedla fakt, że host sieci web może być dowolną liczbę punktów wejścia oddzielne z pojedynczą nazwę domeny. Na przykład projekt Django dla domeny, takich jak contoso.com może zawierać jedną aplikację dla www.contoso.com, drugi aplikacji dla support.contoso.com i trzeci aplikacji dla docs.contoso.com. W takim przypadku projektu Django obsługuje routingu adresów URL na poziomie witryny i ustawień (w jego `urls.py` i `settings.py` plików), a każda aplikacja ma własny różne stylami i zachowanie za pośrednictwem jego routingu wewnętrznym, widoki, modeli, pliki statyczne i administracyjnych interfejs.

Aplikacja Django zazwyczaj rozpoczyna się od standardowego zestawu plików. Program Visual Studio udostępnia szablony elementów, aby zainicjować aplikację Django, w ramach projektu Django, wraz ze zintegrowanym polecenie, która pełni tę samą funkcję:

- Szablony: W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy element**. W **Dodaj nowy element** okna dialogowego, szablon wybierz opcję "Django 1.9 aplikacji", określ nazwę aplikacji na **nazwa** pola i wybierz pozycję **OK**.

- Polecenie zintegrowane: W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **aplikacji Django**. To polecenie wyświetla monit o podanie nazwy i tworzy aplikację Django 1.9.

    ![Polecenia menu dodawania aplikacji Django](media/django/step02-add-django-app-command.png)

Przy użyciu jednej z metod, Utwórz aplikację o nazwie "HelloDjangoApp". Wynik jest folderem w projekcie o tej nazwie zawierającej elementy, zgodnie z opisem w tabeli poniżej.

![Pliki aplikacji Django w Eksploratorze rozwiązań](media/django/step02-django-app-in-solution-explorer.png)

| Element | Opis |
| --- | --- |
| `__init.py__` | Plik, który identyfikuje aplikację jako pakiet. |
| `migrations` | Folder, w którym Django przechowuje skrypty, które aktualizują bazę danych, aby były wyrównane z zmiany do modeli. Narzędzia migracji w Django następnie dotyczą niezbędne zmiany wszelkie wcześniejsze wersje bazy danych, aby był zgodny z bieżącym modeli. Przy użyciu migracji, skup na modeli i umożliwić Django obsługi podstawowy schemat bazy danych. Migracje zostały omówione w kroku 6. teraz, po prostu zawiera folder `__init.py__` pliku (co oznacza, że folder definiuje własny pakiet języka Python). |
| `templates` | Folder zawierający pojedynczy plik szablony stron Django `index.html`. Szablony są bloki kodu HTML, do którego widoków można dodać informacje do dynamicznego renderowania strony. Takie jak strona "zmiennych szablonu," `{{ content }}` w `index.html`, są symbole zastępcze wartości dynamiczne zgodnie z objaśnieniem w dalszej części tego artykułu (krok 2). Zwykle aplikacji Django tworzenie przestrzeni nazw dla ich szablonów przez umieszczenie ich w podfolderze, która jest zgodna z nazwą aplikacji. |
| `admin.py` | Plik Python, w którym można rozszerzyć aplikacji użytkownika administracyjnego interfejsu (zobacz krok 6), który służy do wyświetlania i edycji danych w bazie danych. Początkowo ten plik zawiera tylko instrukcja `from django.contrib import admin`. Domyślnie Django obejmuje standardowych interfejsu administracyjnego za pomocą wpisów w projekcie Django `settings.py` pliku, który można włączyć Trwa usuwanie komentarza istniejących wpisów `urls.py`. |
| `apps.py` | Plik języka Python, który definiuje klasę konfiguracji dla aplikacji (zobacz poniżej, pod tą tabelą). |
| `models.py` | Obiekty danych, identyfikowany przez funkcje, za pomocą których widoków interakcji z podstawowej bazy danych aplikacji są modeli (zobacz krok 6). Django zapewnia warstwę połączenia bazy danych, dzięki czemu nie trzeba zajmować się te szczegóły aplikacji. `models.py` Plików to domyślne miejsce, w którym można utworzyć modeli i początkowo zawiera tylko instrukcję `from django.db import models`. |
| `tests.py` | Plik języka Python, który zawiera podstawową strukturę testów jednostkowych. |
| `views.py` | Widoki są zwykle opinią z jako stron sieci web, które przyjmować żądania HTTP i zwracać odpowiedzi HTTP. Widoki zwykle renderowane jako kodu HTML, który sposób wyświetlania przeglądarki sieci web, ale widoku nie zawsze musi być widoczne (na przykład formularz pośrednich). Widok jest zdefiniowany przez funkcję języka Python, którego zadaniem jest do renderowania elementów HTML do wysłania do przeglądarki. `views.py` Plików to domyślne miejsce, w którym można tworzyć widoki i początkowo zawiera tylko instrukcję `from django.shortcuts import render`. |

Zawartość `app.py` wygląda następująco przy użyciu nazwy "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Pytanie: Tworzy aplikację Django w programie Visual Studio any różni się od tworzenia aplikacji w wierszu polecenia?

Odpowiedź: Systemem **Dodaj** > **aplikacji Django** polecenia lub przy użyciu **Dodaj** > **nowy element** z aplikacji Django szablon tworzy tych samych plików w ramach polecenia Django `manage.py startapp <app_name>`. Korzyści do tworzenia aplikacji w programie Visual Studio jest aplikacji folder i wszystkie jego pliki są automatycznie zintegrowane w projekcie. Tego samego polecenia programu Visual Studio umożliwia utworzenie dowolnej liczby aplikacji w projekcie.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Krok 2-2: uruchamianie aplikacji z projektu Django

W tym punkcie ponownie uruchomić projekt w programie Visual Studio (przy użyciu przycisku paska narzędzi lub **debugowania** > **Rozpocznij debugowanie**), nadal wyświetlona domyślna strona. Brak zawartości aplikacji pojawia się, ponieważ należy zdefiniować stronę specyficzny dla aplikacji i dodać do projektu Django aplikację:

1. W `HelloDjangoApp` folder, Modyfikuj `views.py` odpowiadające poniższy kod, który definiuje widok o nazwie "index":

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. W `BasicProject` folder (utworzonego w kroku 1), zmodyfikuj `urls.py` co najmniej odpowiadające następujący kod (można zachować instruktażowy komentarze Jeśli chcesz):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Widoki, do których Django kieruje określonych adresów URL względem lokacji zawiera opis każdego wzorca adresu URL (czyli część znajdujący się "https://www.domain.com/"). Pierwszy wpis `urlPatterns` który rozpoczyna się od wyrażenia regularnego `^$` jest routingu dla katalogu głównego witryny "/". Drugi wpis `^home$` specjalnie trasy "/ Strona główna". Może mieć dowolną liczbę marszrut do tego samego widoku.

1. Uruchom projekt ponownie, aby wyświetlić komunikat "Hello, Django!" zgodnie z definicją widoku. Gdy wszystko będzie gotowe, należy zatrzymać serwer.

### <a name="commit-to-source-control"></a>Zatwierdź do kontroli źródła

Ponieważ wprowadzono zmiany w kodzie i zostały one przetestowane pomyślnie, obecnie jest to doskonały moment, aby przejrzeć i zatwierdź zmiany do kontroli źródła. Wykonania kolejnych kroków tego samouczka przypomnienia o odpowiedni czas zatwierdzenia ponownie do kontroli źródła i odwołują się w tej sekcji.

1. Wybierz przycisk zmiany wzdłuż dolnej części programu Visual Studio (okręgi poniżej), który przechodzi do **Team Explorer**.

    ![Przycisk zmiany kontroli źródła na pasku stanu programu Visual Studio](media/django/step02-source-control-changes-button.png)

1. W **Team Explorer**, wprowadź komunikat zatwierdzenia, takie jak "Utworzyć początkową aplikację Django" i wybierz **zatwierdzania wszystkich**. Po zakończeniu zatwierdzenia, zostanie wyświetlony komunikat "Commit <hash> utworzony lokalnie. Przycisk Synchronizuj, aby udostępnić zmiany na serwerze. Jeśli chcesz wypchnąć zmiany do repozytorium zdalnego, wybierz opcję **synchronizacji**, a następnie wybierz pozycję **wypychania** w obszarze **wychodzących zatwierdzeń**. Można również gromadzone wielu zatwierdzeń lokalnej przed wypchnięciem zdalne.

    ![Wypychanie zatwierdzeń do zdalnego w programie Team Explorer](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Pytanie: co to jest przed routingu ciągów dla prefiksu "r"?

Odpowiedź: Prefiks "r" na ciąg w języku Python oznacza "nieprzetworzonej," który powoduje, że nie Usuń wszelkie znaki w ciągu języka Python. Wyrażenia regularne używają wielu znaków specjalnych, używając prefiksu "r" sprawia, że te ciągi czytelność niż jeśli one zawiera szereg "\' Usuń znaki.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Pytanie: co zrobić ^ i znaków $ oznacza wpisów routingu adresów URL?

Odpowiedź: W wyrażeniach regularnych, które definiują wzorców adresów URL ^ "początku wiersza" oznacza i oznacza $ "końca wiersza," gdzie ponownie adresy URL są względem katalogu głównego witryny (częścią znajdującą się `https://www.domain.com/`). Wyrażenie regularne `^$` oznacza "blank", dlatego odpowiada pełny adres URL `https://www.domain.com/` (nothing dodane do katalogu głównego witryny). Wzorzec `^home$` dokładnie `https://www.domain.com/home/`. (Django nie używa końcowy / w dopasowanie wzorca).

Jeśli nie jest używany w wyrażeniu regularnym końcowe $ jak `^home`, dopasowania wzorca adresu URL, a następnie *żadnych* adres URL rozpoczynający się od "home", "home", "domową", "homestead" i "home192837".

Do eksperymentów z różnych wyrażeń regularnych, spróbuj online narzędzi takich jak [regex101.com](https://regex101.com) w [pythex.org](http://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Krok 2 – 3: renderowania widoku przy użyciu języka HTML

`index` Funkcji, które należy do tej pory w `views.py` nie więcej niż odpowiedzi HTTP zwykłego tekstu dla strony. Większość stron sieci web rzeczywistych oczywiście odpowiadać, podając sformatowanego stron HTML, często zawierające dane na żywo. W rzeczywistości głównej przyczyny do definiowania widoku jest używana funkcja jest tak tej zawartości może być generowany dynamicznie.

Ponieważ argument `HttpResponse` jest po prostu określonym ciągiem, można tworzyć w górę ciągu, takich jak kodu HTML. Prosty przykład zastąpić `index` funkcja następującym kodem (zachowuje istniejące `from` instrukcje), generująca odpowiedzi HTML przy użyciu zawartość dynamiczną, która jest aktualizowana każdorazowo po odświeżeniu strony:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Uruchom projekt ponownie, aby wyświetlić komunikat typu "**Django Witaj!** w poniedziałek, 16 kwietnia, 2018 przy 16:28:10 ". Odśwież stronę, aby zaktualizować czas i upewnij się, że zawartość jest generowany z każdym żądaniem. Gdy wszystko będzie gotowe, należy zatrzymać serwer.

> [!Tip]
> Skrót do zatrzymania i ponownego uruchomienia projektu jest użycie **debugowania** > **ponowne uruchomienie** polecenia menu (Ctrl + Shift + F5) lub przycisk Uruchom ponownie na pasku narzędzi debugowania:
>
> ![Uruchom ponownie przycisk na pasku narzędzi debugowania w programie Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Krok 2-4: renderowania widoku, używając szablonu strony

Generowanie kodu HTML w kodzie działa dobrze w bardzo małych stron, ale jako strony uzyskać dokładniejsze zwykle chcesz zachować statycznych elementów HTML na stronie (wraz z odwołaniami do plików CSS i JavaScript) jako "strony Szablony", w których następnie wstawiania dynamiczny, wygenerowany kod zawartość. W poprzedniej sekcji, tylko datę i godzinę z `now.strftime` wywołanie jest dynamiczny, co oznacza, innej zawartości można umieścić w szablonie strony.

Szablon strony Django to blok kodu HTML, który może zawierać dowolną liczbę tokenów zastąpienia o nazwie "zmiennych" które przez użytkownika są umieszczone `{{` i `}}`, jak w `{{ content }}`. Moduł tworzenia szablonów w Django następnie zamienia zmienne zawartość dynamiczną, które zapewniają w kodzie.

Poniższe kroki przedstawiają sposób używania szablony stron:

1. W obszarze `BasicProject` folder, który zawiera Django projektu, otwórz `settings.py` pliku, a następnie dodaj nazwę aplikacji, "HelloDjangoApp", do `INSTALLED_APPS` listy. Dodawanie aplikacji do listy zawiera projekt Django czy istnieje folder o tej nazwie zawierający aplikację:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Również w `settings.py`, upewnij się, że `TEMPLATES` obiekt zawiera następujący wiersz (domyślnie włączone), która powoduje, że Django do wyszukania szablonów w zainstalowaną aplikację `templates` folderu:

    ```json
    'APP_DIRS': True,
    ```

1. W `HelloDjangoApp` folder, otwórz `templates/index.html` pliku szablonu strony, aby sprawdzić, czy zawiera on jedną zmienną `{{ content }}`:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. W `HelloDjangoApp` folder, otwórz `views.py` i Zastąp `index` funkcja następującym kodem, który używa `django.shortcuts.render` funkcji pomocnika. `render` Pomocnika oferuje uproszczony interfejs do pracy z szablonami strony. Pamiętaj zachować wszystkie istniejące `from` instrukcje.

    ```python
    from django.shortcuts import render   # Added for this step

    def index(request):
        now = datetime.now()

        return render(
            request,
            "index.html",  # Relative path from the 'templates' folder to the template file
            {
                'content': "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

    Pierwszy argument `render`, jak widać, jest obiektem żądanie, oraz ścieżkę względną do pliku szablonu w aplikacji `templates` folderu. Plik szablonu nosi nazwę dla widoku, który ją obsługuje, w razie potrzeby. Trzeci argument `render` jest następnie słownika zmiennych, które dotyczą szablonu. Może zawierać obiekty w słowniku, w którym to przypadku zmiennej w szablonie mogą odwoływać się do `{{ object.property }}`.

1. Uruchom projekt i sprawdź dane wyjściowe. Powinien zostać wyświetlony komunikat podobny do tego wyświetlonego kroku 2-2, co oznacza, że szablon działania.

    Obserwować, jednak, że kod HTML, można użyć w `content` właściwości renderuje tylko w postaci zwykłego tekstu, ponieważ `render` funkcja automatycznie specjalne tego HTML. Mimo że można uzyskać wokół anulowanie, najlepiej należy unikać wbudowanego kodu HTML w pierwszej kolejności. Formatowanie i style najlepiej pozostawić w szablonie strony nie znajduje się w kodzie, i jest proste sprawa można utworzyć dodatkowe zmienne w razie potrzeby.

    Na przykład zmienić `templates/index.html` odpowiadające następujący kod, który dodaje tytuł strony i przechowuje wszystkie formatowania w szablonie strony:

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

    Następnie wpisz `index` widok, funkcji, podaj wartości wszystkich zmiennych w szablonie strony:

    ```python
    def index(request):
        now = datetime.now()

        return render(
            request,
            "index.html",  # Relative path from the 'templates' folder to the template file
            {
                'title' : "Hello Django",
                'message' : "Hello Django!",
                'content' : " on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

1. Zatrzymaj serwer ponownego uruchomienia projektu i sprawdź, czy strona teraz renderuje prawidłowo:

    ![Uruchomionej aplikacji przy użyciu szablonu](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Jako ostatni krok Przenieś szablonów do podfolderu o nazwie takiej jak aplikacji, która tworzy przestrzeń nazw i pozwala uniknąć potencjalnych konfliktów w innych aplikacjach, które można dodać do projektu. Oznacza to, utwórz podfolder w `templates` o nazwie `HelloDjangoApp`, Przenieś `index.html` do tego podfolderu i zmodyfikuj `index` wyświetlić funkcji do odwoływania się do szablonu nowej ścieżki `HelloDjangoApp/index.html`. Następnie uruchom projekt Sprawdź poprawnie renderuje stronę, a zatrzymać serwer.

1. Zatwierdź zmiany do kontroli źródła i zaktualizować zdalnego repozytorium, w razie potrzeby, zgodnie z opisem w [krok 2-2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Pytanie: czy szablony stron muszą być w oddzielnym pliku?

Odpowiedź: Mimo że szablony są zazwyczaj obsługiwane w oddzielnych plików HTML, umożliwia także szablonem wbudowanego. Użycie osobnego pliku jest zalecane, jednak do obsługi czyste rozdzielenie znaczników i kodu.

### <a name="question-must-templates-use-the-html-file-extension"></a>Pytanie: szablony korzystać tylko z rozszerzeniem pliku HTML?

Odpowiedź: `.html` rozszerzeń plików szablonu strony jest opcjonalna, ponieważ zawsze zidentyfikować dokładnej ścieżki względnej do pliku w drugim argumentem `render` funkcji. Jednak program Visual Studio (i innych edytory) zazwyczaj zapewnia funkcje, takie jak uzupełnianie i składni zabarwienie kodu z `.html` pliki, które przeważa nad fakt, że strona szablony nie są ściśle HTML.

W rzeczywistości podczas pracy z projektem Django, Visual Studio automatycznie wykrywa plik HTML, który jest edytowany jest rzeczywiście szablonu Django i zawiera pewnych funkcji automatycznego zakończenia. Na przykład po rozpoczęciu wprowadzania komentarz Django strony szablonu `{#`, Visual Studio automatycznie umożliwia zamknięcie `#}` znaków. **Zaznaczanie komentarzy** i **usuń znaczniki komentarza wybór** polecenia (na **Edytuj** > **zaawansowane** menu i na pasku narzędzi) komentarze szablonu należy również użyć zamiast komentarze HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Pytanie: Uruchomienie projektu, wyświetlany błąd, którego nie można odnaleźć szablonu. Co jest nie tak?

Odpowiedź: Jeśli wyświetlane błędy, których nie można znaleźć szablonu, upewnij się, dodaniu aplikacji do projektu Django `settings.py` w `INSTALLED_APPS` listy. Bez tego wpisu Django nie będzie wiedzieć do wyszukiwania w aplikacji `templates` folderu.

### <a name="question-why-is-template-namespacing-important"></a>Pytanie: Dlaczego należy namespacing szablonu?

Odpowiedź: Gdy Django szuka szablon określony w `render` funkcji używa niezależnie od pliku znajdzie najpierw zgodna ze ścieżką względną. Jeśli masz wiele aplikacji Django w tym samym projekcie, które używają tej samej struktury folderów dla szablonów, prawdopodobnie, co aplikacja zostanie przypadkowo Użyj szablonu z innej aplikacji. Aby uniknąć tych błędów, Zawsze twórz w podfolderze aplikacji `templates` folderu, który jest zgodna z nazwą aplikacji, aby uniknąć duplikowania wszystkie.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Obsługi plików statycznych, Dodaj strony i użyj szablonu dziedziczenia](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- [Pisanie pierwszej aplikacji Django, część 1 - widoków](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Aby uzyskać więcej możliwości Django szablony, takie jak obejmuje i dziedziczenia, zobacz [język szablonu Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- [Wyrażenie regularne szkolenia na inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowy — vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)