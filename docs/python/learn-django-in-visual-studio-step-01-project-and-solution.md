---
title: Samouczek — Dowiedz się Django w programie Visual Studio, krok 1
description: Wskazówki dotyczące podstawy Django w kontekście projektów programu Visual Studio, prezentacja obsługi programu Visual Studio udostępnia programowanie Django.
ms.date: 05/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: de9726b6716ff66178b90792a25f7bf02bec8ede
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="tutorial-step-1-get-started-with-the-django-web-framework-in-visual-studio"></a>Samouczek krok 1: wprowadzenie do platformy sieci web Django w programie Visual Studio

[Django](https://www.djangoproject.com/) to struktura Python wysokiego poziomu przeznaczone do rozwoju szybkie, bezpieczne i skalowalne sieci web. W tym samouczku Eksploruje framework Django w kontekście szablony projektu Visual Studio udostępnia uprościć tworzenie aplikacji sieci web opartych na Django.

Z tego samouczka, dowiesz się, jak:

> [!div class="checklist"]
> - Tworzenie podstawowego projektu Django w repozytorium Git przy użyciu szablonu "Pusty projekt sieci Web Django" (krok 1)
> - Tworzenie aplikacji Django z jednej strony i renderowania tej strony za pomocą szablonu (krok 2)
> - Obsługi plików statycznych, Dodaj strony i Użyj dziedziczenia szablonu (krok 3)
> - Szablon projektu sieci Web Django umożliwia tworzenie aplikacji z wielu stron i elastyczny projekt (krok 4)
> - Uwierzytelnianie użytkowników (krok 5)
> - Szablon projektu sieci Web Django sond służy do tworzenia aplikacji, która używa modeli, migracja bazy danych i dostosowania do interfejsu administracyjnego (krok 6)

## <a name="prerequisites"></a>Wymagania wstępne

- 2017 Visual Studio z następującymi opcjami:
  - **Programowania Python** obciążenia (**obciążenia** kartę w Instalatorze). Aby uzyskać instrukcje, zobacz [obsługi instalacji języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git dla systemu Windows** i **rozszerzenie GitHub dla programu Visual Studio** na **pojedynczych składników** w obszarze **kodu narzędzia**.

Szablony projektów Django również są dołączane do wszystkich starszych wersji narzędzi Python Tools for Visual Studio, chociaż szczegóły mogą się różnić od co opisano w tym samouczku (szczególnie różni się w starszych wersjach platformy Django).

### <a name="visual-studio-projects-and-django-projects"></a>"Programu visual Studio" i "Django projektów"

W terminologii Django "Projekt Django" składa się z kilku plików konfiguracji na poziomie witryny, wraz z co najmniej jeden "" wdrażane aplikacje na serwerze sieci web, aby utworzyć aplikację sieci web pełną. Projekt Django może zawierać wielu aplikacji, a ta sama aplikacja może być w wielu projektach Django.

Projektu programu Visual Studio dla jego części mogą zawierać projektu Django wraz z wielu aplikacji. Dla uproszczenia, należy zawsze, gdy w tym samouczku odwołanie do właśnie "projektu," odwołuje się do projektu programu Visual Studio. Kiedy odnosi się do części "Django projektu" aplikacja sieci web, używa "Django projektu" specjalnie.

W trakcie tego samouczka utworzysz jedno rozwiązanie Visual Studio zawierający trzy oddzielne projekty Django, z których każdy zawiera tylko jednej aplikacji Django. Dzięki przechowywaniu projekty w tym samym rozwiązaniu, można łatwo przełączać i z powrotem między różnych plików do porównania.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: Tworzenie projektu Visual Studio i rozwiązania

Podczas pracy z Django z wiersza polecenia, zazwyczaj rozpoczyna się projekt, uruchamiając `django-admin startproject <project_name>` polecenia. W programie Visual Studio przy użyciu szablonu "Pusty projekt sieci Web Django" zapewnia tej samej struktury w Visual Studio projektu i rozwiązania.

1. W programie Visual Studio, wybierz **pliku** > **nowy** > **projektu**, wyszukaj "Django" i wybierz **pusty projekt sieci Web Django**  szablonu. (Szablon znajduje się również w **Python** > **Web** na liście po lewej stronie.)

    ![Okno dialogowe nowego projektu w programie Visual Studio dla pustego projektu sieci Web Django](media/django/step01-new-blank-project.png)

1. W polach w dolnej części okna dialogowego, wprowadź następujące informacje (jak pokazano na rysunku poprzedniej), a następnie wybierz **OK**:

    - **Nazwa**: Ustaw nazwę projektu programu Visual Studio "BasicProject". Ta nazwa jest również używana dla projektu Django.
    - **Lokalizacja**: Określ lokalizację, w której chcesz utworzyć rozwiązanie Visual Studio i projektu.
    - **Rozwiązanie**: pozostaw tego formantu ustawioną opcję "Utwórz nowe rozwiązanie" domyślną.
    - **Nazwa rozwiązania**: wartość "LearningDjango", który jest odpowiedni do rozwiązania jako kontener dla wielu projektów w tym samouczku.
    - **Utwórz katalog rozwiązania**: pozostaw wartość (ustawienie domyślne).
    - **Tworzenie nowego repozytorium Git**: Wybierz tę opcję, (czyli wyczyść domyślnie), dzięki czemu program Visual Studio tworzy lokalne repozytorium Git, podczas tworzenia rozwiązania. Jeśli nie widzisz tej opcji, uruchom Instalatora programu Visual Studio 2017 i Dodaj Git dla systemu Windows i rozszerzenie GitHub dla programu Visual Studio na **pojedynczych składników** w obszarze **kodu narzędzia**.

1. Po chwili Visual Studio Wyświetla okno dialogowe z informacją "ten projekt wymaga pakiety zewnętrzne" (pokazana poniżej). To okno dialogowe pojawia się, ponieważ szablon zawiera `requirements.txt` pliku odwołujące się do najnowszego pakietu 1.x Django. (Wybierz **Pokaż wymagane pakiety** aby zobaczyć dokładnie zależności.)

    ![Monituj zawierający komunikat, że projekt wymaga pakiety zewnętrzne](media/django/step01-requirements-prompt-install-myself.png)

1. Wybierz opcję **będzie zainstalować je samodzielnie**. Możesz utworzyć środowisko wirtualne wkrótce do upewnij się, że jest ona wykluczana z kontroli źródła. (Zawsze można utworzyć środowisko z `requirements.txt`.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1 i 2: Sprawdź formanty Git i opublikuj do zdalnego repozytorium

Ponieważ wybrano **Tworzenie nowego repozytorium Git** w **nowy projekt** okna dialogowego, Projekt już został przekazany do kontroli źródła lokalnego zaraz po zakończeniu procesu tworzenia. W tym kroku należy zapoznać się z formantów Git programu Visual Studio i **Team Explorer** okna, w którym pracujesz z kontroli źródła.

1. Sprawdź, czy formanty Git na dolnym rogu okna głównego programu Visual Studio. Od lewej do prawej tych kontrolek Pokaż unpushed zatwierdzeń, niezatwierdzone zmiany nazwy repozytorium i bieżącej gałęzi:

    ![Git formantów w oknie programu Visual Studio](media/django/step01-git-controls.png)

    > [!Note]
    > Jeśli nie zaznaczysz **Tworzenie nowego repozytorium Git** w **nowy projekt** dialogowym formanty Git Pokaż tylko **Dodaj do kontroli źródła** polecenia tworzącą lokalnym repozytorium.
    >
    > ![Dodaj do kontroli źródła pojawia się w programie Visual Studio, jeśli nie utworzono repozytorium](media/django/step01-git-add-to-source-control.png)

1. Wybierz przycisk zmiany i Visual Studio otworzy jego **Team Explorer** okno na **zmiany** strony. Ponieważ nowo utworzonego projektu już został przekazany do kontroli źródła automatycznie, nie widać żadnych oczekujących zmian.

    ![Okno Eksploratora zespołu na stronie zmian](media/django/step01-team-explorer-changes.png)

1. Na pasku stanu programu Visual Studio, kliknij przycisk unpushed zatwierdzeń (strzałkę w górę o "2") można otworzyć **synchronizacji** strony **Team Explorer**. Masz lokalnego repozytorium, dlatego ta strona zawiera opcje łatwe publikowanie różnych repozytoria zdalne repozytorium.

    ![Team Explorer okna pokazujący dostępne Git opcji repozytorium dla kontroli źródła](media/django/step01-team-explorer.png)

    Można wybrać dowolną wskazaną usługi dla własnych projektów. W tym samouczku pokazano sposób użycia GitHub, w którym ukończone przykładowy kod dla tego samouczka jest zachowywany w [Microsoft/python — przykładowy — vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django) repozytorium.

1. Podczas zaznaczania poszczególnych **publikowania** formantów, **Team Explorer** monit, aby uzyskać więcej informacji. Na przykład przy publikowaniu przykładowej w tym samouczku, repozytorium sam musieli najpierw należy utworzyć, w którym to przypadku **wypychania do zdalnego repozytorium** użyto opcji z adresem URL z repozytorium.

    ![Okno Eksploratora zespołu do wypychania do istniejącego zdalnego repozytorium](media/django/step01-push-to-github.png)

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

Teraz, gdy skonfigurowano kontroli źródła dla projektu, można utworzyć środowisko wirtualne niezbędne pakiety Django, które wymaga projektu. Następnie można użyć **Team Explorer** Aby wykluczyć folder w środowisku z kontrolą źródła.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **środowiska Python** a następnie wybierz węzeł **Dodawanie środowiska wirtualnego**.

    ![Dodaj polecenie środowisko wirtualne w Eksploratorze rozwiązań](media/django/step01-add-virtual-environment-command.png)

1. **Dodawanie środowiska wirtualnego** zostanie wyświetlone okno dialogowe z komunikatem "Znaleziono plik requirements.txt." Ten komunikat oznacza, że program Visual Studio używa tego pliku do konfigurowania środowiska wirtualnego.

    ![Dodaj okno dialogowe środowiska wirtualnego z pliku requirements.txt wiadomości](media/django/step01-add-virtual-environment-found-requirements.png)

1. Wybierz **Utwórz** zaakceptować wartości domyślne. (Można zmienić nazwę środowiska wirtualnego, jeśli chcesz, która po prostu zmienia nazwę jej podfolder, ale `env` jest standardowej konwencji.)

1. Wyrażenia zgody na uprawnienia administratora, jeśli zostanie wyświetlony monit, a następnie cierpliwość kilka minut, gdy Visual Studio pobiera i instaluje pakiety, które Django oznacza Rozpakowywanie kilku tysięcy plików w o tyle podfoldery! Wyświetlany postęp w programie Visual Studio **dane wyjściowe** okna. Póki czekasz, ponder w kolejnych sekcjach pytanie.

1. W formantach Visual Studio Git (na pasku stanu), wybierz wskaźnik zmian (który zawiera "99 *") co spowoduje otwarcie **zmiany** w obszarze **Team Explorer**.

    Tworzenie środowiska wirtualnego, sprowadzonych tysięcy zmian, ale nie ma potrzeby zawierać żadnego z nich w kontroli źródła (lub innym klonowania projektu) zawsze można odtworzyć środowisko z `requirements.txt`.

    Aby wykluczyć środowiska wirtualnego, kliknij prawym przyciskiem myszy `env` i wybierz polecenie **ignorować te elementy lokalne**.

    ![Ignorowanie środowiska wirtualnego w zmian kontroli źródła](media/django/step01-ignore-local-items.png)

1. Po wykluczeniu środowiska wirtualnego, tylko pozostałe zmiany są do pliku projektu i `.gitignore`. `.gitignore` Plik zawiera dodano wpis dla folderu środowiska wirtualnego. Możesz kliknąć dwukrotnie plik, aby wyświetlić porównania.

1. Wprowadź komunikat zatwierdzenia i wybierz **zatwierdzania wszystkich** przycisk, a następnie, jeśli chcesz wypychać zatwierdzenia do repozytorium zdalnego.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Pytanie: Dlaczego chcę utworzyć środowisko wirtualne?

Odpowiedź: Środowiska wirtualnego jest doskonałym sposobem izolować dokładne zależności aplikacji. Takie izolacji pozwala uniknąć konfliktów w środowisku Python globalne i ułatwia testowanie i współpracy. Wraz z upływem czasu podczas opracowywania aplikacji niezmiennie przełączeniem we wszystkich wiele pomocnych pakietów języka Python. Umieszczanie pakietów w środowisku wirtualnym specyficznego dla projektu, można łatwo aktualizować projektu `requirements.txt` pliku, który opisuje tego środowiska, który jest dostępny w kontroli źródła. Po skopiowaniu na inne komputery, w tym serwery kompilacji, wdrożenia serwerów i innych komputerów rozwoju projektu jest łatwo utworzyć ponownie ze środowiskiem za pomocą tylko `requirements.txt` (tworzonym środowiska nie musi być w kontroli źródła). Aby uzyskać więcej informacji, zobacz [za pomocą środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Pytanie: Jak usunąć środowisko wirtualne już przywiązuje dużą wagę do kontroli źródła?

Odpowiedź: Najpierw Edytuj Twojej `.gitignore` plik, aby wykluczyć folder: Znajdź sekcję na końcu komentarz `# Python Tools for Visual Studio (PTVS)` i Dodaj nowy wiersz do folderu, w środowisku wirtualnym, takie jak `/BasicProject/env`. (Ponieważ Visual Studio nie wyświetla go w **Eksploratora rozwiązań**, otwórz go bezpośrednio przy użyciu **pliku** > **Otwórz**  >   **Plik** polecenia menu. Można również otworzyć plik z **Team Explorer**: na **ustawienia** wybierz pozycję **ustawienia repozytorium**, przejdź do **Ignoruj & atrybutów plików** sekcji, a następnie wybierz **Edytuj** znajdujący się obok podsekcji `.gitignore`.)

Po drugie, Otwórz okno poleceń, przejdź do folderu, takich jak `BasicProject` zawiera takie jak folder środowiska wirtualnego `env`i uruchom `git rm -r env`. Następnie zatwierdzić te zmiany z poziomu wiersza polecenia (`git commit -m 'Remove venv'`) lub czy zatwierdzić z **zmiany** strony **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: Badanie kodu umożliwiającego

Po zakończeniu tworzenia projektu, sprawdź schematyczny kod projektu Django (która jest ponownie tak samo jak wygenerowane za pomocą polecenia interfejsu wiersza polecenia `django-admin startproject <project_name>`).

1. W projekcie głównym jest `manage.py`, Django narzędzie wiersza polecenia administratora programu Visual Studio automatycznie ustawia jako plik uruchomienia projektu. Uruchom narzędzie przy użyciu wiersza polecenia `python manage.py <command> [options]`. Do wykonywania typowych zadań Django program Visual Studio oferuje wygodny poleceń. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Python** Aby wyświetlić listę. Niektóre z tych poleceń, w ramach tego samouczka wystąpią.

    ![Menu kontekstowe projektu Django poleceń języka Python](media/django/step01-django-commands-menu.png)

1. W projekcie jest folder o nazwie takiej jako projekt. Zawiera podstawowe pliki projektu Django:

    - `__init.py`: pusty plik Python informuje, czy ten folder jest pakiet języka Python.
    - `wsgi.py`: punkt wejścia dla serwerów sieci web zgodnej WSGI do obsługi projektu. Zwykle pozostaw ten plik jako — jako zapewnia punkty zaczepienia do produkcyjnych serwerów sieci web.
    - `settings.py`: zawiera ustawienia dla projektu Django, które można zmodyfikować w trakcie opracowywania aplikacji sieci web.
    - `urls.py`: zawiera spis treści dla projektu Django, który również zmodyfikować w trakcie opracowywania.

    ![Pliki projektu Django w Eksploratorze rozwiązań](media/django/step01-django-project-in-solution-explorer.png)

1. Jak wspomniano wcześniej, szablon programu Visual Studio również dodaje `requirements.txt` plik do projektu określania zależności pakietu Django. Obecność tego pliku jest co umożliwiające tworzenie środowiska wirtualnego, tworząc po raz pierwszy projekt.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Pytanie: Czy Visual Studio wygenerować plik requirements.txt ze środowiska wirtualnego po zainstalowaniu innych pakietów?

Odpowiedź: tak. Rozwiń węzeł **środowiska Python** węzła, kliknij prawym przyciskiem myszy środowiska wirtualnego, a następnie wybierz **Generuj plik requirements.txt** polecenia. Dobra Aby użyć tego polecenia okresowo podczas modyfikowania środowiska i zatwierdzania zmian `requirements.txt` do kontroli źródła oraz innych zmian kodu, które są zależne od tego środowiska. Jeśli konfigurujesz ciągłej integracji na serwerze kompilacji powinna generować plik i zatwierdzić zmiany przy każdym zmodyfikowanie tego środowiska.

## <a name="step-1-5-run-the-empty-django-project"></a>Krok 1-5: Uruchom pusty projekt Django

1. W programie Visual Studio, wybierz **debugowania** > **Rozpocznij debugowanie** (F5) lub użyj **serwera sieci Web** przycisk na pasku narzędzi (przeglądarka Zobacz może różnić się):

    ![Uruchom serwer sieci web przycisku paska narzędzi w programie Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Uruchamianie serwera oznacza, uruchamiając polecenie `manage.py runserver <port>`, co spowoduje włączenie serwera wdrożeniowego wbudowanych w Django. Jeśli program Visual Studio "Nie można uruchomić debugera" z komunikatem o nie pliku uruchamiania, kliknij prawym przyciskiem myszy `manage.py` w **Eksploratora rozwiązań** i wybierz **Ustaw jako plik uruchamiania**.

1. Po ponownym uruchomieniu serwera, jest wyświetlane okno konsoli otwórz to również Wyświetla dziennik serwera. Visual Studio automatycznie otwiera w przeglądarce `http://localhost:<port>`. Ponieważ Django projektu nie ma żadnych aplikacji, jednak Django pokazuje tylko domyślną stronę potwierdzenia, że do tej pory ma działa prawidłowo:

    ![Widok domyślny projekt Django](media/django/step01-first-run-success.png)

1. Gdy wszystko będzie gotowe, Zatrzymaj serwer zamknięcie okna konsoli lub za pomocą **debugowania** > **Zatrzymaj debugowanie** polecenia w programie Visual Studio.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Pytanie: Jest Django serwera sieci web, a także struktury?

Odpowiedź: Tak i nie. Django się serwer sieci web wbudowanych, który służy do celów programistycznych. Jest to serwer sieci web co to jest używany podczas uruchamiania aplikacji sieci web lokalnie, takie jak kiedy debugowania w programie Visual Studio. Podczas wdrażania na serwerze sieci web, jednak Django użyje hosta serwera sieci web. `wsgi.py` Modułu w projekcie Django zajmuje się przechwytywanie na serwerach produkcyjnych.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Pytanie: Jaka jest różnica między za pomocą poleceń menu debugowania i poleceń serwera w podmenu Python projektu?

Odpowiedź: W uzupełnieniu do **debugowania** poleceń menu i przycisków paska narzędzi można również uruchomić serwera przy użyciu **Python** > **uruchamiania serwera** lub **Python** > **serwer uruchamiania debugowania** polecenia w menu kontekstowym projektu. Oba polecenia Otwórz okno konsoli zawiera adres URL lokalnego (localhost:port) dla uruchomionego serwera. Jednak należy ręcznie Otwórz przeglądarkę z tego adresu URL i uruchamiania serwera debugowania nie zostanie uruchomiony automatycznie debuger programu Visual Studio. Możesz dołączyć debugera do uruchomionego procesu później, jeśli chcesz, za pomocą **debugowania** > **dołączyć do procesu** polecenia.

## <a name="next-steps"></a>Następne kroki

W tym momencie podstawowego projektu Django nie zawiera żadnych aplikacji. Tworzenie aplikacji w następnym kroku. Ponieważ zwykle pracować z więcej niż projekt Django aplikacji Django, nie trzeba znać znacznie więcej plików umożliwiającego obecnie.

> [!div class="nextstepaction"]
> [Tworzenie aplikacji Django z widoki i szablony stron](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- Kod projektu Django: [pisanie pierwszej aplikacji Django, część 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Narzędzie administracyjne: [django admin i manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- Kod źródłowy samouczek w witrynie GitHub: [Microsoft/python — przykładowy — vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
