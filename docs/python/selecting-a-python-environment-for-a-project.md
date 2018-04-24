---
title: Wybierając środowisko dla projektu
description: W Eksploratorze rozwiązań programu Visual Studio można przypisać określone interpreter języka Python (Środowisko) zawsze na użytek żadnym konkretnym projektem, ignorowanie domyślnego środowiska. Można również tworzyć i zarządzać środowiskami wirtualnymi.
ms.date: 03/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 72f07115aa323db15dd5680575871b8d4c4b20b4
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="selecting-a-python-interpreter-and-environment-for-use-in-a-project"></a>Zaznaczanie interpreter języka Python i środowiska do użycia w projekcie

Cały kod w projekcie języka Python działa w kontekście określonego środowiska. Visual Studio również korzysta z tego środowiska do debugowania, importowanie i zakończeń — członek, sprawdzanie składni i innych zadań, które wymagają środowisku.

Wszystkie nowe projekty języka Python w programie Visual Studio są wstępnie skonfigurowane do używania domyślnej globalnej środowisko, w którym jest wyświetlany w obszarze **środowiska Python** węzła w Eksploratorze rozwiązań:

![Środowisko Python domyślnej globalnej wyświetlany w Eksploratorze rozwiązań](media/environments-project.png)

Aby zmienić środowisko dla projektu, kliknij prawym przyciskiem myszy **środowiska Python** a następnie wybierz węzeł **środowiska Python Dodaj lub Usuń...** . Z listy wyświetlanych w tym globalnych, wirtualnych i środowisk conda zaznacz wszystkie te mają być wyświetlane w obszarze **środowiska Python** węzła:

![Okno dialogowe Dodawanie/usuwanie środowiska Python](media/environments-add-remove.png)

Po wybraniu **OK**, są wyświetlane wszystkie wybrane środowiska **środowiska Python** węzła. Pogrubione pojawia się aktualnie aktywowanego środowiska:

![Wiele środowisk języka Python wyświetlany w Eksploratorze rozwiązań](media/environments-project-multiple.png)

Aby szybko uaktywnić innego środowiska, kliknij prawym przyciskiem myszy nazwę tego środowiska, a następnie wybierz **środowiska Aktywuj**. Wybór jest zapisywany w projekcie i tego środowiska jest uaktywniany przy każdym otwarciu projektu w przyszłości. Po wyczyszczeniu wszystkich opcji w **środowiska Python Dodaj lub usuń** globalnych domyślnego środowiska wygaszacza ekranu okna dialogowego, Visual Studio.

Menu kontekstowe **środowiska Python** węzeł oferuje również dodatkowe polecenia:

| Polecenie | Opis |
| --- | --- |
| Dodaj środowisko wirtualne... | Rozpocznie się proces tworzenia nowego środowiska wirtualnego w projekcie. Zobacz [tworzenie środowiska wirtualnego](#create-a-virtual-environment). |
| Dodaj istniejącego środowiska wirtualnego... | Wyświetla monit o wybranie folderu zawierającego środowisko wirtualne i dodaje go do listy w obszarze **środowiska Python**, ale go nie uaktywnia. Zobacz [ActivateAdd istniejącego środowiska wirtualnego](#activate-an-existing-virtual-environment). |
| Utwórz środowisko Conda... | Przełącza do **środowiska Python** *okna* w którym wprowadź nazwę dla środowiska i określ jej interpreter podstawowy. |

## <a name="using-virtual-environments"></a>Za pomocą środowisk wirtualnych

Środowisko wirtualne ma unikatowej kombinacji wartości określonych interpreter języka Python i określony zbiór biblioteki, który różni się od innych środowisk globalne i conda. Środowisko wirtualne jest przeznaczony do projektu i są przechowywane w folderze projektu. Ten folder zawiera biblioteki zainstalowany w środowisku wraz z `pyvenv.cfg` pliku, który określa ścieżkę do środowiska programu *interpreter podstawowy* w innym miejscu w systemie plików. (Oznacza to, że środowisko wirtualne nie zawiera kopię interpretera tylko link jej). 

Korzyścią z używania środowiska wirtualnego jest, że podczas opracowywania planu projektu w czasie, środowisko wirtualne zawsze odzwierciedla dokładnie zależności projektu. (Współużytkowanego środowiska z globalnej, z drugiej strony, zawiera dowolną liczbę bibliotek czy można używać ich w projekcie lub nie). Następnie możesz łatwo utworzyć `requirements.txt` plików ze środowiska wirtualnego, który jest następnie używany do ponownej instalacji tych zależności na innym komputerze rozwoju lub produkcji. Aby uzyskać więcej informacji, zobacz [zarządzania wymagane pakiety z pliku requirements.txt](managing-required-packages-with-requirements-txt.md).

Po otwarciu projektu w programie Visual Studio, który zawiera `requirements.txt` pliku, Visual Studio automatycznie wyświetla monit udostępnia opcję, aby ponownie utworzyć środowisko wirtualne. Na komputerach, gdzie nie jest zainstalowany program Visual Studio, takich jak usługi Azure App Service można użyć `pip install -r requirements.txt` pod kątem przywracania pakietów (ten proces jest opisany w [Zarządzanie Python w usłudze Azure App Service](managing-python-on-azure-app-service.md)).

Ponieważ środowisko wirtualne zawiera ścieżkę ustalony interpreter podstawowy i Utwórz ponownie przy użyciu środowiska `requirements.txt`, zwykle pominięto folderu całego środowiska wirtualnego z kontroli źródła.

W poniższych sekcjach opisano, jak aktywować istniejącego środowiska wirtualnego w projekcie oraz sposobu tworzenia nowego środowiska wirtualnego.

W programie Visual Studio można aktywować środowiska wirtualnego w projekcie podobnie jak każdy inny za pośrednictwem **środowiska Python** w węźle **Eksploratora rozwiązań**.

Gdy środowisko wirtualne zostanie dodany do projektu, zostanie wyświetlony w **środowiska Python** okna. Następnie można go uaktywnić podobnie jak inne środowiska i można zarządzać jej pakietów.

### <a name="create-a-virtual-environment"></a>Tworzenie środowiska wirtualnego

Nowe środowisko wirtualne można tworzyć bezpośrednio z programu Visual Studio w następujący sposób:

1. Kliknij prawym przyciskiem myszy **środowiska Python** w Eksploratorze rozwiązań i wybierz **Dodawanie środowiska wirtualnego...** , co spowoduje uruchomienie następującego okna dialogowego:

    ![Tworzenie środowiska wirtualnego](media/environments-add-virtual-1.png)

1. W **lokalizacji środowiska wirtualnego** Określ ścieżkę do środowiska wirtualnego. Jeśli określisz tylko nazwę środowiska wirtualnego jest tworzony w bieżącym projekcie w podfolderze o tej nazwie.

1. Wybierz środowisko jako podstawowy interpreter i wybierz **Utwórz**. Visual Studio Wyświetla pasek postępu podczas konfiguruje w środowisku i pobiera wszystkie niezbędne pakiety. W tym momencie zostanie wyświetlony w środowisku wirtualnym **środowiska Python** okna zawierającego projektu.

1. Środowisko wirtualne nie zostało uaktywnione domyślnie. Aby aktywować go dla projektu, kliknij go prawym przyciskiem myszy i wybierz **aktywacji środowiska**.

> [!Note]
> Jeśli ścieżka lokalizacji identyfikuje istniejącego środowiska wirtualnego, Visual Studio automatycznie wykrywa interpreter podstawowy (przy użyciu `orig-prefix.txt` plików w środowisku `lib` katalogu) i zmienia przycisk Utwórz, aby **Dodaj**.
>
> Jeśli `requirements.txt` plik istnieje w środowisku wirtualnym, dodając **Dodawanie środowiska wirtualnego** Wyświetla okno dialogowe opcję pakiety są instalowane automatycznie, dzięki czemu można łatwo odtworzyć w środowisku na innym komputerze:
>
> ![Tworzenie środowiska wirtualnego z pliku requirements.txt](media/environments-requirements-txt.png)
>
> W obu przypadkach efekt jest taki sam jak w przypadku **Dodawanie istniejącego środowiska wirtualnego...**  polecenia.

### <a name="activate-an-existing-virtual-environment"></a>Aktywuj istniejącego środowiska wirtualnego

Jeśli zostało już utworzone w innym miejscu środowiska wirtualnego, możesz to zrobić dla projektu w następujący sposób:

1. Kliknij prawym przyciskiem myszy **środowiska Python** w Eksploratorze rozwiązań i wybierz **Dodawanie istniejącego środowiska wirtualnego...** .

1. W **Przeglądaj** okno dialogowe zostanie wyświetlone, przejdź do wybierz folder, który zawiera środowisko wirtualne i wybierz **OK**. W przypadku wykrycia przez program Visual Studio `requirements.txt` pliku w tym środowisku go zapyta, czy zainstalować te pakiety.

1. Po kilku chwilach środowisko wirtualne zostanie wyświetlona w obszarze **środowiska Python** węzła w Eksploratorze rozwiązań. Środowisko wirtualne nie został aktywowany domyślnie, więc kliknij go prawym przyciskiem myszy i wybierz **aktywacji środowiska**.

### <a name="remove-a-virtual-environment"></a>Usuń środowisko wirtualne

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy środowisko wirtualne i wybierz **Usuń**.

1. Visual Studio zapyta, czy usunąć lub usunąć środowisko wirtualne. Wybieranie **Usuń** staje się niedostępny w projekcie, jednak nie pozostawia jej w systemie plików. Wybieranie **usunąć** zarówno usuwa środowisko z projektu i usuwa je z systemu plików. Nie wpływa na interpreter podstawowy.

## <a name="view-installed-packages"></a>Wyświetl zainstalowane pakiety

W Eksploratorze rozwiązań rozwiń węzeł w danym środowisku, aby szybko wyświetlić pakiety, które są zainstalowane w tym środowisku (co oznacza, że mogą być importowane i użyć tych pakietów w kodzie, gdy środowisko jest aktywny):

![Pakiety języka Python dla środowiska w Eksploratorze rozwiązań](media/environments-installed-packages.png)

Aby zainstalować nowe pakiety, kliknij prawym przyciskiem myszy środowisko i wybierz **zainstaluj pakiet języka Python...**  Aby przełączyć się do **pakiety** karcie **środowiska Python** okna. Wprowadź wyszukiwania termin (zazwyczaj nazwa pakietu) i Visual Studio zawiera pasujące pakiety.

W programie Visual Studio pakietów (i zależności) są pobierane z [indeksu pakietów języka Python (PyPI)](https://pypi.org), gdzie można także przeszukać dostępnych pakietów. Pasek stanu programu Visual Studio i okno dane wyjściowe zawierają informacje o instalacji. Aby odinstalować pakiet, kliknij prawym przyciskiem wybierz **Usuń**.

Należy pamiętać, że wyświetlane wpisy nie zawsze są dokładne i instalowaniem i odinstalowywaniem nie może być niezawodne lub są dostępne. Visual Studio korzysta z Menedżera pakietów pip, jeśli jest dostępny i pobiera i instaluje je w razie potrzeby. Program Visual Studio umożliwia także easy_install Menedżera pakietów. Pakiety zainstalowane przy użyciu `pip` lub `easy_install` również są wyświetlane w wierszu polecenia.

Również pamiętać, że program Visual Studio nie obecnie obsługuje przy użyciu `conda` pakiety mają być zainstalowane w środowisku conda. Użyj `conda` polecenia zamiast tego wiersza.

> [!Tip]
> Typowe sytuacji, gdy pip nie można zainstalować pakietu to pakietu zawierającego kod źródłowy dla natywnych składników w `*.pyd` plików. Bez wymagana wersja programu Visual Studio pip nie można skompilować tych składników. Komunikat o błędzie wyświetlany w tej sytuacji `error: Unable to find vcvarsall.bat`. `easy_install` często jest w stanie pobrać wstępnie skompilowanych plików binarnych, możesz również pobrać odpowiedni kompilatora dla starszych wersji języka Python z [ http://aka.ms/VCPython27 ](http://aka.ms/VCPython27). Aby uzyskać więcej informacji, zobacz [jak rozwiązać problemy z "nie można odnaleźć vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) na Python tools blogu zespołu.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiska Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Odwołanie do okna środowiska Python](python-environments-window-tab-reference.md)