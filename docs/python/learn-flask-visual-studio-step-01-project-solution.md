---
title: Samouczek — Dowiedz się Flask w programie Visual Studio, krok 1
description: Wskazówki dotyczące podstawy Flask w kontekście projektów programu Visual Studio.
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
ms.openlocfilehash: 2420beaa7f200ca281e04189667c1534e2a0f991
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752502"
---
# <a name="tutorial-step-1-get-started-with-the-flask-web-framework-in-visual-studio"></a>Samouczek krok 1: wprowadzenie do platformy Flask struktura sieci web w programie Visual Studio

[Flask](http://flask.pocoo.org/) to lekkie platforma języka Python dla aplikacji sieci web, która zapewnia podstawowe informacje dotyczące routingu adresów URL i renderowania stron.

Flask jest nazywany framework "micro", ponieważ nie zawiera on bezpośrednio funkcje, takie jak weryfikacja formularza, abstrakcji bazy danych, uwierzytelnianie i tak dalej. Takie funkcje zamiast tego są dostarczane przez specjalnych pakietów języka Python o nazwie Flask *rozszerzenia*. Rozszerzenia bezproblemowo zintegrować z platformy Flask, tak aby wyglądały jak są one częścią platformy Flask, sama. Na przykład platformy Flask, sama nie udostępnia aparatu szablonu strony. Tworzenia szablonów są udostępniane przez rozszerzenia, takie jak Jinja i Jade, jak pokazano w tym samouczku.

Z tego samouczka, dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie podstawowego projektu platformy Flask w repozytorium Git przy użyciu szablonu "Pusty projekt sieci Web platformy Flask" (krok 1)
> - Tworzenie aplikacji platformy Flask z jednej strony i renderowania tej strony za pomocą szablonu (krok 2)
> - Obsługi plików statycznych, Dodaj strony i Użyj dziedziczenia szablonu (krok 3)
> - Szablon projektu sieci Web platformy Flask umożliwia tworzenie aplikacji z wielu stron i elastyczny projekt (krok 4)
> - Szablon projektu sieci Web platformy Flask sond do tworzenia aplikacji sondowania, który używa różne opcje magazynu (usługa Azure storage, bazy danych MongoDB lub pamięci).

W ciągu tych kroków tworzenia jedno rozwiązanie Visual Studio, zawierający trzy osobne projekty. Można utworzyć projektu przy użyciu różnych szablonów projektu platformy Flask, dostępnych w programie Visual Studio. Dzięki przechowywaniu projekty w tym samym rozwiązaniu, można łatwo przełączać i z powrotem między różnych plików do porównania.

> [!Note]
> W tym samouczku różni się od [szybkiego startu Flask](../ide/quickstart-python.md?context=visualstudio/python/default) , możesz dowiedzieć się więcej o Flask oraz jak używać innej platformy Flask szablonów projektu, które zapewniają bardziej rozległych początkowy punkt dla własnych projektów. Na przykład szablony projektów automatycznie zainstalować pakiet Flask podczas tworzenia projektu, a nie można zainstalować ręcznie, jak pokazano w szybkiego startu pakiet.

## <a name="prerequisites"></a>Wymagania wstępne

- 2017 Visual Studio w systemie Windows z następującymi opcjami:
  - **Programowania Python** obciążenia (**obciążenia** kartę w Instalatorze). Aby uzyskać instrukcje, zobacz [obsługi instalacji języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git dla systemu Windows** i **rozszerzenie GitHub dla programu Visual Studio** na **pojedynczych składników** w obszarze **kodu narzędzia**.

Szablony projektu platformy flask są dołączane do wszystkich starszych wersji narzędzi Python Tools for Visual Studio, chociaż szczegóły mogą się różnić od co opisano w tym samouczku.

Tworzenie Python nie jest obecnie obsługiwany w programie Visual Studio dla komputerów Mac. W systemie Mac i Linux, użyj [rozszerzenia języka Python w programie Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: Tworzenie projektu Visual Studio i rozwiązania

1. W programie Visual Studio, wybierz **pliku** > **nowy** > **projektu**, wyszukaj "Flask" i wybierz **pusty projekt sieci Web platformy Flask**  szablonu. (Szablon znajduje się również w **Python** > **Web** na liście po lewej stronie.)

    ![Okno dialogowe nowego projektu w programie Visual Studio dla pustego projektu sieci Web platformy Flask](media/flask/step01-new-blank-project.png)

1. W polach w dolnej części okna dialogowego, wprowadź następujące informacje (jak pokazano na rysunku poprzedniej), a następnie wybierz **OK**:

    - **Nazwa**: Ustaw nazwę projektu programu Visual Studio "BasicProject". Ta nazwa jest również używana dla projektu platformy Flask.
    - **Lokalizacja**: Określ lokalizację, w której chcesz utworzyć rozwiązanie Visual Studio i projektu.
    - **Nazwa rozwiązania**: wartość "LearningFlask", który jest odpowiedni do rozwiązania jako kontener dla wielu projektów w tym samouczku.
    - **Utwórz katalog rozwiązania**: pozostaw wartość (ustawienie domyślne).
    - **Tworzenie nowego repozytorium Git**: Wybierz tę opcję, (czyli wyczyść domyślnie), dzięki czemu program Visual Studio tworzy lokalne repozytorium Git, podczas tworzenia rozwiązania. Jeśli nie widzisz tej opcji, uruchom Instalatora programu Visual Studio 2017 i Dodaj Git dla systemu Windows i rozszerzenie GitHub dla programu Visual Studio na **pojedynczych składników** w obszarze **kodu narzędzia**.

1. Po chwili Visual Studio Wyświetla okno dialogowe z informacją "ten projekt wymaga pakiety zewnętrzne" (pokazana poniżej). To okno dialogowe pojawia się, ponieważ szablon zawiera `requirements.txt` pliku odwołujące się do najnowszego pakietu 1.x Flask. (Wybierz **Pokaż wymagane pakiety** aby zobaczyć dokładnie zależności.)

    ![Monituj zawierający komunikat, że projekt wymaga pakiety zewnętrzne](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Wybierz opcję **będzie zainstalować je samodzielnie**. Możesz utworzyć środowisko wirtualne wkrótce do upewnij się, że jest ona wykluczana z kontroli źródła. (Zawsze można utworzyć środowisko z `requirements.txt`.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1 i 2: Sprawdź formanty Git i opublikuj do zdalnego repozytorium

Ponieważ wybrano **Tworzenie nowego repozytorium Git** w **nowy projekt** okna dialogowego, Projekt już został przekazany do kontroli źródła lokalnego zaraz po zakończeniu procesu tworzenia. W tym kroku należy zapoznać się z formantów Git programu Visual Studio i **Team Explorer** okna, w którym pracujesz z kontroli źródła.

1. Sprawdź, czy formanty Git na dolnym rogu okna głównego programu Visual Studio. Od lewej do prawej tych kontrolek Pokaż unpushed zatwierdzeń, niezatwierdzone zmiany nazwy repozytorium i bieżącej gałęzi:

    ![Git formantów w oknie programu Visual Studio](media/flask/step01-git-controls.png)

    > [!Note]
    > Jeśli nie zaznaczysz **Tworzenie nowego repozytorium Git** w **nowy projekt** dialogowym formanty Git Pokaż tylko **Dodaj do kontroli źródła** polecenia tworzącą lokalnym repozytorium.
    >
    > ![Dodaj do kontroli źródła pojawia się w programie Visual Studio, jeśli nie utworzono repozytorium](media/tutorials-common/step01-git-add-to-source-control.png)

1. Wybierz przycisk zmiany i Visual Studio otworzy jego **Team Explorer** okno na **zmiany** strony. Ponieważ nowo utworzonego projektu już został przekazany do kontroli źródła automatycznie, nie widać żadnych oczekujących zmian.

    ![Okno Eksploratora zespołu na stronie zmian](media/flask/step01-team-explorer-changes.png)

1. Na pasku stanu programu Visual Studio, kliknij przycisk unpushed zatwierdzeń (strzałkę w górę o "2") można otworzyć **synchronizacji** strony **Team Explorer**. Masz lokalnego repozytorium, dlatego ta strona zawiera opcje łatwe publikowanie różnych repozytoria zdalne repozytorium.

    ![Team Explorer okna pokazujący dostępne Git opcji repozytorium dla kontroli źródła](media/flask/step01-team-explorer.png)

    Można wybrać dowolną wskazaną usługi dla własnych projektów. W tym samouczku pokazano sposób użycia GitHub, w którym ukończone przykładowy kod dla tego samouczka jest zachowywany w [Microsoft/python — przykładowy — vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) repozytorium.

1. Podczas zaznaczania poszczególnych **publikowania** formantów, **Team Explorer** monit, aby uzyskać więcej informacji. Na przykład przy publikowaniu przykładowej w tym samouczku, repozytorium sam musieli najpierw należy utworzyć, w którym to przypadku **wypychania do zdalnego repozytorium** użyto opcji z adresem URL z repozytorium.

    ![Okno Eksploratora zespołu do wypychania do istniejącego zdalnego repozytorium](media/flask/step01-push-to-github.png)

    Jeśli nie masz istniejące repozytorium **publikowanie w usłudze GitHub** i **wypychania do programu Visual Studio Team Services** opcje pozwalają utworzyć bezpośrednio z poziomu programu Visual Studio.

1. Podczas pracy z tym samouczkiem pobranie do przejrzenia okresowo za pomocą formantów w programie Visual Studio do zatwierdzenia i wypychania zmian. W tym samouczku przypomina w odpowiednich miejscach.

> [!Tip]
> Aby szybko przejść w **Team Explorer**, wybierz pozycję nagłówka (odczytujący "Zmiany" lub "Push" w obrazach powyżej), aby wyświetlić menu podręczne dostępnych stron.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Pytanie: Jakie są niektóre korzyści wynikające z używania kontroli źródła od początku projektu?

Odpowiedź: Przede wszystkim do kontroli źródła od początku, zwłaszcza, jeśli używasz zdalnego repozytorium, zapewnia regularne poza siedzibą firmy kopii zapasowej projektu. W przeciwieństwie do obsługi tylko w projekcie lokalny system plików, kontroli źródła są także historii zmiany i łatwe możliwość przywracania pojedynczego pliku lub całego projektu do poprzedniego stanu. Który historii zmian można ustalić przyczyny regresji (test awarii). Ponadto kontroli źródła jest niezbędne, jeśli wiele osób pracuje nad projektem, zarządza zastępuje i udostępnia rozwiązywania konfliktów. Na koniec kontroli źródła, która jest zasadniczo formę automatyzacji, konfiguruje można również do automatyzacji kompilacji, testowania i zarządzania zleceniami. Naprawdę jest pierwszym krokiem przy użyciu DevOps dla projektu, a ponieważ bariery, są tak niewielkie, nie istnieje naprawdę Przyczyna opcję rezygnacji z używania kontroli źródła od początku.

Aby zapoznać się w kontroli źródła jako automatyzacji, zobacz [źródła prawdy: roli repozytoria w DevOps](https://msdn.microsoft.com/magazine/mt763232), artykułu w MSDN Magazine napisane dla aplikacji mobilnych, która ma zastosowanie również do aplikacji sieci web.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Pytanie: Można zapobiec Visual Studio automatyczne zatwierdzanie nowego projektu?

Odpowiedź: tak. Aby wyłączyć automatyczne zatwierdzanie, przejdź do **ustawienia** strony **Team Explorer**, wybierz pozycję **Git** > **ustawienia globalne**Usuń zaznaczenie pola wyboru Opcja etykietą **Zatwierdź zmiany po scaleniu domyślnie**, a następnie wybierz pozycję **aktualizacji**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1: 3: tworzenie środowiska wirtualnego i wyklucz je z kontroli źródła

Teraz, gdy skonfigurowano kontroli źródła dla projektu, można utworzyć środowisko wirtualne niezbędne pakiety platformy Flask, które wymaga projektu. Następnie można użyć **Team Explorer** Aby wykluczyć folder w środowisku z kontrolą źródła.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **środowiska Python** a następnie wybierz węzeł **Dodawanie środowiska wirtualnego**.

    ![Dodaj polecenie środowisko wirtualne w Eksploratorze rozwiązań](media/flask/step01-add-virtual-environment-command.png)

1. **Dodawanie środowiska wirtualnego** zostanie wyświetlone okno dialogowe z komunikatem "Znaleziono plik requirements.txt." Ten komunikat oznacza, że program Visual Studio używa tego pliku do konfigurowania środowiska wirtualnego.

    ![Dodaj okno dialogowe środowiska wirtualnego z pliku requirements.txt wiadomości](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Wybierz **Utwórz** zaakceptować wartości domyślne. (Można zmienić nazwę środowiska wirtualnego, jeśli chcesz, która po prostu zmienia nazwę jej podfolder, ale `env` jest standardowej konwencji.)

1. Uprawnienia administratora, jeśli zostanie wyświetlony monit, następnie cierpliwość przez kilka minut, podczas gdy program Visual Studio pobiera i instaluje pakiety, czyli Flask i jego zależności rozszerzanie o tysięcy plików w podfolderach ponad 100 oznacza zgodę. Wyświetlany postęp w programie Visual Studio **dane wyjściowe** okna. Póki czekasz, ponder w kolejnych sekcjach pytanie. Można również wyświetlić opis platformy Flask, w zależności na [instalacji platformy Flask](http://flask.pocoo.org/docs/1.0/installation/#installation) strony (flask.pcocoo.org).

1. W formantach Visual Studio Git (na pasku stanu), wybierz wskaźnik zmian (który zawiera "99\*") co spowoduje otwarcie **zmiany** w obszarze **Team Explorer**.

    Tworzenie środowiska wirtualnego, sprowadzonych setki zmiany, ale nie ma potrzeby zawierać żadnego z nich w kontroli źródła (lub innym klonowania projektu) zawsze można odtworzyć środowisko z `requirements.txt`.

    Aby wykluczyć środowiska wirtualnego, kliknij prawym przyciskiem myszy `env` i wybierz polecenie **ignorować te elementy lokalne**.

    ![Ignorowanie środowiska wirtualnego w zmian kontroli źródła](media/flask/step01-ignore-local-items.png)

1. Po wykluczeniu środowiska wirtualnego, tylko pozostałe zmiany są do pliku projektu i `.gitignore`. `.gitignore` Plik zawiera dodano wpis dla folderu środowiska wirtualnego. Możesz kliknąć dwukrotnie plik, aby wyświetlić porównania.

1. Wprowadź komunikat zatwierdzenia i wybierz **zatwierdzania wszystkich** przycisk, a następnie, jeśli chcesz wypychać zatwierdzenia do repozytorium zdalnego.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Pytanie: Dlaczego chcę utworzyć środowisko wirtualne?

Odpowiedź: Środowiska wirtualnego jest doskonałym sposobem izolować dokładne zależności aplikacji. Takie izolacji pozwala uniknąć konfliktów w środowisku Python globalne i ułatwia testowanie i współpracy. Wraz z upływem czasu podczas opracowywania aplikacji niezmiennie przełączeniem we wszystkich wiele pomocnych pakietów języka Python. Umieszczanie pakietów w środowisku wirtualnym specyficznego dla projektu, można łatwo aktualizować projektu `requirements.txt` pliku, który opisuje tego środowiska, który jest dostępny w kontroli źródła. Po skopiowaniu na inne komputery, w tym serwery kompilacji, wdrożenia serwerów i innych komputerów rozwoju projektu jest łatwo utworzyć ponownie ze środowiskiem za pomocą tylko `requirements.txt` (tworzonym środowiska nie musi być w kontroli źródła). Aby uzyskać więcej informacji, zobacz [za pomocą środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Pytanie: Jak usunąć środowisko wirtualne już przywiązuje dużą wagę do kontroli źródła?

Odpowiedź: Najpierw Edytuj Twojej `.gitignore` plik, aby wykluczyć folder: Znajdź sekcję na końcu komentarz `# Python Tools for Visual Studio (PTVS)` i Dodaj nowy wiersz do folderu, w środowisku wirtualnym, takie jak `/BasicProject/env`. (Ponieważ Visual Studio nie wyświetla go w **Eksploratora rozwiązań**, otwórz go bezpośrednio przy użyciu **pliku** > **Otwórz**  >   **Plik** polecenia menu. Można również otworzyć plik z **Team Explorer**: na **ustawienia** wybierz pozycję **ustawienia repozytorium**, przejdź do **Ignoruj & atrybutów plików** sekcji, a następnie wybierz **Edytuj** znajdujący się obok podsekcji `.gitignore`.)

Po drugie, Otwórz okno poleceń, przejdź do folderu, takich jak `BasicProject` zawiera takie jak folder środowiska wirtualnego `env`i uruchom `git rm -r env`. Następnie zatwierdzić te zmiany z poziomu wiersza polecenia (`git commit -m 'Remove venv'`) lub czy zatwierdzić z **zmiany** strony **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: Badanie kodu umożliwiającego

1. Po zakończeniu tworzenia projektu, zobacz rozwiązania i projektu w **Eksploratora rozwiązań**, jeśli projekt zawiera tylko dwa pliki `app.py` i `requirements.txt`:

    ![Puste pliki projektu platformy Flask, w Eksploratorze rozwiązań](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Jak wspomniano wcześniej, `requirements.txt` plik określa zależność pakietu platformy Flask. Obecność tego pliku jest co umożliwiające tworzenie środowiska wirtualnego, tworząc po raz pierwszy projekt.

1. Pojedynczy `app.py` plik zawiera trzy części. Najpierw jest `import` instrukcji dla platformy Flask, tworzenia wystąpienia `Flask` klasy, która jest przypisana do zmiennej `app`i przypisując `wsgi_app` zmiennej (co jest przydatne w przypadku wdrażania na serwerze sieci web, ale nie jest używany w chwili obecnej):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. Druga część, na końcu pliku, to bit opcjonalne kodu, który rozpoczyna się serwera programistycznego platformy Flask od konkretnego hosta i portu wartości z zmienne środowiskowe (domyślnie localhost:5555):

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Trzeci jest krótki bitowego kodu, który przypisuje funkcji do adresu URL trasy, co oznacza, że funkcja zapewnia zasobu wskazywanego przez adres URL. Definiowanie tras za pomocą platformy Flask w `@app.route` dekoratora, którego argument jest względny adres URL z katalogu głównego witryny. Jak widać w kodzie, funkcja zwraca tylko ciąg tekstowy, który jest wystarczająca dla przeglądarki do renderowania. W kolejnych krokach renderowania są bardziej rozbudowane stron HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-name-argument-to-the-flask-class"></a>Pytanie: co to jest celem __nazwa__ argument klasy Flask?

Odpowiedź: Argument jest nazwę modułu lub pakietu aplikacji i instruuje platformy Flask, gdzie ma zostać wyszukane szablony, pliki statyczne oraz inne zasoby, które należą do aplikacji. Dla aplikacji zawarte w module pojedynczego `__name__` jest zawsze poprawnej wartości. Należy również dla rozszerzeń, które wymagają informacji o debugowaniu. Aby uzyskać więcej informacji i dodatkowe argumenty, zobacz [dokumentacji klasy Flask](http://flask.pocoo.org/docs/1.0/api/#flask.Flask) (flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Pytanie: funkcja mają więcej niż jedną trasę dekoratora?

Odpowiedź: Tak, można użyć dowolną liczbę elementów decorator dowolnie Jeśli taką samą funkcję obsługuje wiele tras. Na przykład, aby użyć `hello` funkcja zarówno dla "/" i "/ hello", użyj następującego kodu:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Pytanie: jak Flask działa z tras adresów URL zmiennych i parametrów zapytania?

Odpowiedź: W trasie, będzie oznaczenie dowolnej zmiennej z `<variable_name>`, i Flask przekazuje zmiennej przy użyciu nazwanego argumentu funkcji. Zmienna może być częścią ścieżki adresu URL lub parametr zapytania. Na przykład trasy w formie `'/hello/<name>` generuje argumentu w postaci ciągu o nazwie `name` funkcji i przy użyciu `?message=<msg>` w trasie analizuje wartości podanej dla "komunikat =" parametr zapytania i przekazuje je do funkcji jako `msg`:

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Aby zmienić typ, prefiks zmiennej o `int`, `float`, `path` (który akceptuje ukośniki do odróżniać nazwy folderów), i `uuid`. Aby uzyskać więcej informacji, zobacz [reguły zmiennych](http://flask.pocoo.org/docs/1.0/quickstart/#variable-rules) w dokumentacji platformy Flask.

Parametry zapytania są również dostępne za pośrednictwem `request.args` właściwości, w szczególności za pomocą `request.args.get` metody. Aby uzyskać więcej informacji, zobacz [żądanie obiektu](http://flask.pocoo.org/docs/1.0/quickstart/#the-request-object) w dokumentacji platformy Flask.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Pytanie: Czy Visual Studio wygenerować plik requirements.txt ze środowiska wirtualnego po zainstalowaniu innych pakietów?

Odpowiedź: tak. Rozwiń węzeł **środowiska Python** węzła, kliknij prawym przyciskiem myszy środowiska wirtualnego, a następnie wybierz **Generuj plik requirements.txt** polecenia. Dobra Aby użyć tego polecenia okresowo podczas modyfikowania środowiska i zatwierdzania zmian `requirements.txt` do kontroli źródła oraz innych zmian kodu, które są zależne od tego środowiska. Jeśli konfigurujesz ciągłej integracji na serwerze kompilacji powinna generować plik i zatwierdzić zmiany przy każdym zmodyfikowanie tego środowiska.

## <a name="step-1-5-run-the-project"></a>Krok 1-5: uruchamianie projektu

1. W programie Visual Studio, wybierz **debugowania** > **Rozpocznij debugowanie** (F5) lub użyj **serwera sieci Web** przycisk na pasku narzędzi (przeglądarka Zobacz może różnić się):

    ![Uruchom serwer sieci web przycisku paska narzędzi w programie Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Polecenie albo przypisuje numeru portu losowe do zmiennej środowiskowej portu, a następnie uruchamia `python app.py`. Zaczyna się kod aplikacji przy użyciu portu w ramach serwera programistycznego platformy Flask firmy. Jeśli program Visual Studio "Nie można uruchomić debugera" z komunikatem o nie pliku uruchamiania, kliknij prawym przyciskiem myszy `app.py` w **Eksploratora rozwiązań** i wybierz **Ustaw jako plik uruchamiania**.

1. Podczas uruchamiania serwera, jest wyświetlane okno konsoli otwórz ten wyświetla dziennik serwera. Visual Studio następnie automatycznie otwiera w przeglądarce `http://localhost:<port>`, gdzie powinien zostać wyświetlony komunikat przez `hello` funkcji:

    ![Widok domyślny projekt platformy flask](media/flask/step01-first-run-success.png)

1. Gdy wszystko będzie gotowe, Zatrzymaj serwer zamknięcie okna konsoli lub za pomocą **debugowania** > **Zatrzymaj debugowanie** polecenia w programie Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Pytanie: Jaka jest różnica między za pomocą poleceń menu debugowania i poleceń serwera w podmenu Python projektu?

Odpowiedź: W uzupełnieniu do **debugowania** poleceń menu i przycisków paska narzędzi można również uruchomić serwera przy użyciu **Python** > **uruchamiania serwera** lub **Python** > **serwer uruchamiania debugowania** polecenia w menu kontekstowym projektu. Oba polecenia Otwórz okno konsoli zawiera adres URL lokalnego (localhost:port) dla uruchomionego serwera. Jednak należy ręcznie Otwórz przeglądarkę z tego adresu URL i uruchamiania serwera debugowania nie zostanie uruchomiony automatycznie debuger programu Visual Studio. Możesz dołączyć debugera do uruchomionego procesu później, jeśli chcesz, za pomocą **debugowania** > **dołączyć do procesu** polecenia.

## <a name="next-steps"></a>Następne kroki

W tym momencie podstawowego projektu platformy Flask zawiera kod uruchomienia i kodu strony w tym samym pliku. Najlepiej do oddzielania tych dwóch problemów, a także rozdzielić HTML i danych przy użyciu szablonów.

> [!div class="nextstepaction"]
> [Tworzenie aplikacji platformy Flask widoki i szablony stron](learn-flask-visual-studio-step-02-create-app.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- [Szybki Start flask](http://flask.pocoo.org/docs/1.0/quickstart/) (flask.pocoo.org)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowy — vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
