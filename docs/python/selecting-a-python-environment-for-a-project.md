---
title: "Wybierając środowisko dla projektu | Dokumentacja firmy Microsoft"
description: "W Eksploratorze rozwiązań programu Visual Studio można przypisać określone interpreter języka Python (Środowisko) zawsze na użytek żadnym konkretnym projektem, ignorowanie domyślnego środowiska. Można również tworzyć i zarządzać środowiskami wirtualnymi."
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 6f422cc60638b7eed4a5b42516e7496c4a6f6209
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="selecting-a-python-interpreter-and-environment-for-use-in-a-project"></a>Zaznaczanie interpreter języka Python i środowiska do użycia w projekcie

Cały kod w projekcie języka Python działa w kontekście określonego środowiska. Visual Studio również korzysta z tego środowiska do debugowania, importowanie i zakończeń — członek, sprawdzanie składni i innych zadań, które wymagają środowisku.

Wszystkie nowe projekty języka Python w programie Visual Studio są wstępnie skonfigurowane do używania domyślnej globalnej środowisko, w którym jest wyświetlany w obszarze **środowiska Python** węzła w Eksploratorze rozwiązań:

![Środowisko Python domyślnej globalnej wyświetlany w Eksploratorze rozwiązań](media/environments-project.png)

Można udostępnić innych środowisk do projektu, również w środowiskach wirtualnych. W dowolnym momencie można aktywować tylko jednego środowiska.

## <a name="using-global-environments"></a>Za pomocą środowisk globalne

Aby udostępnić określone globalnego środowiska do projektu (również w środowiskach conda [zidentyfikowane ręcznie](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)), kliknij prawym przyciskiem myszy **środowiska Python** a następnie wybierz węzeł **Dodaj lub usuń Środowiska Python...** . Na wyświetlonej liście wybierz żądany środowiskach:

![Okno dialogowe Dodawanie/usuwanie środowiska Python](media/environments-add-remove.png)

Po wybraniu **OK**, są wyświetlane wszystkie wybrane środowiska **środowiska Python** węzła. Pogrubione pojawia się obecnie aktywowany środowiska:

![Wiele środowisk języka Python wyświetlany w Eksploratorze rozwiązań](media/environments-project-multiple.png)

Aby aktywować innego środowiska, kliknij prawym przyciskiem myszy nazwę środowiska i wybierz **aktywacji środowiska**. Wybór jest zapisywany w projekcie i tego środowiska jest uaktywniany przy każdym otwarciu projektu w przyszłości.

Po wyczyszczeniu wszystkich opcji w **środowiska Python Dodaj lub usuń** globalnych domyślnego środowiska wygaszacza ekranu okna dialogowego, Visual Studio.

## <a name="using-virtual-environments"></a>Za pomocą środowisk wirtualnych

Środowisko wirtualne ma unikatowej kombinacji wartości określonych interpreter języka Python i określony zbiór biblioteki, który różni się od innych środowisk globalne i conda. Środowisko wirtualne jest zazwyczaj używana, gdy ma określonych potrzeb w projekcie i nie chcesz zmodyfikować innych środowisk zaspokojenie tych potrzeb.

Gdy środowisko wirtualne zostanie dodany do projektu, zostanie wyświetlony w **środowiska Python** okna, możesz to zrobić podobnie jak inne środowiska i można zarządzać jej pakietów.

Należy pamiętać, że wadą do środowisk wirtualnych jest że ustalony plikowym i w związku z tym nie można łatwo można udostępnione lub do innych komputerów programowanie. Na szczęście, można użyć `requirements.txt` pliku, aby zezwolić adresatów projektu, aby łatwo przywrócić środowiska. Aby uzyskać więcej informacji, zobacz [zarządzania wymagane pakiety z pliku requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="activating-an-existing-virtual-environment"></a>Aktywowanie istniejącego środowiska wirtualnego

Jeśli zostało już utworzone w innym miejscu środowiska wirtualnego, możesz to zrobić dla projektu w następujący sposób:

1. Kliknij prawym przyciskiem myszy **środowiska Python** w Eksploratorze rozwiązań i wybierz **Dodawanie istniejącego środowiska wirtualnego...** .

1. W **Przeglądaj** okno dialogowe zostanie wyświetlone, przejdź do wybierz folder, który zawiera środowisko wirtualne i wybierz **OK**. W przypadku wykrycia przez program Visual Studio `requirements.txt` pliku w tym środowisku go zapyta, czy zainstalować te pakiety.

1. Po kilku chwilach środowisko wirtualne zostanie wyświetlona w obszarze **środowiska Python** węzła w Eksploratorze rozwiązań. Środowisko wirtualne nie został aktywowany domyślnie, więc kliknij go prawym przyciskiem myszy i wybierz **aktywacji środowiska**.

### <a name="creating-a-virtual-environment"></a>Tworzenie środowiska wirtualnego

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

### <a name="remove-a-virtual-environment"></a>Usuń środowisko wirtualne

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy środowisko wirtualne i wybierz **Usuń**.

1. Visual Studio zapyta, czy usunąć lub usunąć środowisko wirtualne. Wybieranie **Usuń** staje się niedostępny w projekcie, jednak nie pozostawia jej w systemie plików. Wybieranie **usunąć** zarówno usuwa środowisko z projektu i usuwa je z systemu plików. Nie wpływa na interpreter podstawowy.

## <a name="viewing-installed-packages"></a>Wyświetlanie zainstalowanych pakietów

W Eksploratorze rozwiązań rozwiń węzeł w danym środowisku, aby szybko wyświetlić pakiety, które są zainstalowane w tym środowisku (co oznacza, że mogą być importowane i użyć tych pakietów w kodzie, gdy środowisko jest aktywny):

![Pakiety języka Python dla środowiska w Eksploratorze rozwiązań](media/environments-installed-packages.png)

Aby zainstalować nowe pakiety, kliknij prawym przyciskiem myszy środowisko i wybierz **zainstaluj pakiet języka Python...**  Aby przełączyć się do **pakiety** karcie **środowiska Python** okna. Wprowadź wyszukiwania termin (zazwyczaj nazwa pakietu) i Visual Studio zawiera pasujące pakiety.

W programie Visual Studio pakietów (i zależności) są pobierane z [indeksu pakietów języka Python (PyPI)](https://pypi.python.org/pypi), gdzie można także przeszukać dostępnych pakietów. Pasek stanu programu Visual Studio i okno dane wyjściowe zawierają informacje o instalacji. Aby odinstalować pakiet, kliknij prawym przyciskiem wybierz **Usuń**.

Należy pamiętać, że wyświetlane wpisy nie zawsze są dokładne i instalowaniem i odinstalowywaniem nie może być niezawodne lub są dostępne. Visual Studio korzysta z Menedżera pakietów pip, jeśli jest dostępny i pobiera i instaluje je w razie potrzeby. Program Visual Studio umożliwia także easy_install Menedżera pakietów. Pakiety zainstalowane przy użyciu `pip` lub `easy_install` również są wyświetlane w wierszu polecenia.

Również pamiętać, że program Visual Studio nie obecnie obsługuje przy użyciu `conda` pakiety mają być zainstalowane w środowisku conda. Użyj `conda` polecenia zamiast tego wiersza.

> [!Tip]
> Typowe sytuacji, gdy pip nie można zainstalować pakietu to pakietu zawierającego kod źródłowy dla natywnych składników w `*.pyd` plików. Bez wymagana wersja programu Visual Studio pip nie można skompilować tych składników. Komunikat o błędzie wyświetlany w tej sytuacji `error: Unable to find vcvarsall.bat`. `easy_install` często jest w stanie pobrać wstępnie skompilowanych plików binarnych, możesz również pobrać odpowiedni kompilatora dla starszych wersji języka Python z [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Aby uzyskać więcej informacji, zobacz [jak rozwiązać problemy z "nie można odnaleźć vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) na Python tools blogu zespołu.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiska Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Odwołanie do okna środowiska Python](python-environments-window-tab-reference.md)