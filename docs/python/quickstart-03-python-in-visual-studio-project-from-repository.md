---
title: Szybki Start - klonowania repozytorium kodu języka Python
description: W tym szybkiego startu tworzenia projektu języka Python w programie Visual Studio w klonowania repozytorium koans Python za pomocą programu Visual Studio Team Explorer.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: e183833222f64a24a2d523e32f624ed24c54bc58
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056711"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Szybki Start: klonowanie repozytorium kodu języka Python w programie Visual Studio

Po wprowadzeniu [zainstalowane obsługę języka Python w Visual Studio 2017](installing-python-support-in-visual-studio.md), można dodać rozszerzenie GitHub dla programu Visual Studio. Rozszerzenie pozwala łatwo sklonować repozytorium kodu Python i tworzenie projektu z jej w środowisku IDE. Można zawsze sklonować repozytoria z wiersza polecenia, a następnie pracować z nimi w programie Visual Studio.

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

1. Uruchom program Visual Studio.

1. Wybierz **Widok > Team Explorer** otworzyć **Team Explorer** okna, w którym można nawiązać połączenia z usługi GitHub lub Visual Studio Team Services lub sklonować repozytorium. (Jeśli nie widzisz **Connect** strony pokazano poniżej, wybierz ikonę plug na górnym pasku narzędzi, który umożliwia przejście do strony.)

    ![Zespół przedstawiający okno Eksploratora Visual Studio Team Services, GitHub i klonowanie repozytorium](media/team-explorer.png)

1. W obszarze **lokalnego repozytoria Git**, wybierz pozycję **klonowania** polecenia, a następnie wprowadź `https://github.com/gregmalcolm/python_koans` w polu adresu URL wprowadź folder plików sklonowany, a następnie wybierz **klonowania** przycisk.

    > [!Tip]
    > Folder, który określisz w programie Team Explorer jest dokładnie folder do odbierania sklonowany plików. W przeciwieństwie do `git clone` poleceń, utworzenie klona w programie Team Explorer nie tworzy automatycznie podfolder o nazwie repozytorium.

1. Po ukończeniu klonowania repozytorium nazwa pojawi się **lokalnego repozytoria Git** listy. Kliknij dwukrotnie tę nazwę, aby przejść do pulpitu nawigacyjnego repozytorium w **Team Explorer**.

1. W obszarze **rozwiązań**, wybierz pozycję **nowy**.

    ![Okno Eksploratora zespołu, tworzenia nowego projektu z klonu](media/team-explorer-new-project.png)

1. W **nowy projekt** okno dialogowe zostanie wyświetlone, przejdź do języka Python (lub wyszukaj frazę "Python"), wybierz "Z istniejących Python Code", określ nazwę dla projektu, ustaw **lokalizacji** na tym samym folderze co repozytorium, a następnie wybierz **OK**. W oknie kreatora wybierz **Zakończ**.

1. Wybierz **Widok > Eksploratora rozwiązań** z menu.

1. W **Eksploratora rozwiązań**, rozwiń węzeł `python3` węzła, kliknij prawym przyciskiem myszy `contemplate_koans.py`i wybierz **Ustaw jako plik uruchamiania**. W tym kroku opisano Visual Studio plik, który należy używać, gdy uruchamiania projektu.

1. Wybierz **projektu > właściwości Koans** z menu wybierz **ogólne** , a następnie ustaw **katalog roboczy** do "python3". Ten krok jest niezbędny, ponieważ domyślnie program Visual Studio Ustawia katalog roboczy katalogu głównym projektu, a nie lokalizacja pliku uruchamiania (`python3\contemplate_koans.py`, który można wyświetlić w oknie właściwości projektu). Kod programu szuka pliku `koans.txt` folderu roboczego, tak zmieniając tę wartość jest widoczny błąd w czasie wykonywania.

    ![Ustawianie katalogu roboczego dla projektów języka Python](media/projects-set-working-directory.png)

1. Naciśnij klawisze Ctrl + F5 lub wybierz **Debuguj > Uruchom bez debugowania** do uruchomienia programu. Jeśli widzisz `FileNotFoundError` dla `koans.txt`, Sprawdź katalog roboczy ustawienia, zgodnie z opisem w poprzednim kroku.

1. Jeśli program zostanie uruchomiony pomyślnie, wyświetla błąd potwierdzenia w wierszu 17 `python3/koans/about_asserts.py`. Jest to zamierzone: program jest przeznaczony do nauki, Python, konfigurując należy poprawić wszystkie błędy zamierzone. (Szczegółowe informacje znajdują się na [Ruby Koans](http://rubykoans.com/), który inspirowana Python Koans.)

    ![Pierwsze dane wyjściowe z programu koans języka Python](media/koans-output.png)

1. Otwórz `python3/koans/about_asserts.py` przejdź do niego w Eksploratorze rozwiązań, a następnie klikając dwukrotnie plik. Należy zauważyć, że numery wierszy nie są wyświetlane domyślnie w edytorze. Aby zmienić to ustawienie, wybierz **Narzędzia > Opcje**, wybierz pozycję **Pokaż wszystkie ustawienia** w dolnej części okna dialogowego, a następnie przejdź do **Edytor tekstu > Python > Ogólne** i wybierz pozycję **Numerów linii**:

    ![Włączanie numer wiersza dla plików języka Python](media/options-general-line-numbers.png)

1. Popraw błąd, zmieniając `False` argument w wierszu 17 do `True`. Wiersz powinien wyglądać następująco:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Ponownie uruchom program. Jeśli program Visual Studio ostrzega o błędach, odpowiadać, podając **tak** kontynuowanie działania kodu. Zostanie wyświetlony przekazuje pierwszy wyboru, a program zatrzymuje się na koan dalej. Kontynuować, popraw błędy i program ponownie ma.

> [!Important]
> W tego przewodnika Szybki Start, został utworzony bezpośrednio Sklonowanie *python_koans* repozytorium w witrynie GitHub. Takie repozytorium jest chroniony przez jego autora z zmian bezpośrednio, dlatego próba Zatwierdź zmiany do repozytorium kończy się niepowodzeniem. W praktyce deweloperzy rozwidlania zamiast tego repozytorium do ich własnego konta GitHub, wprowadzić zmiany, a następnie utwórz żądania ściągnięcia do przesyłania tych zmian w oryginalnej repozytorium. Jeśli masz własne rozwidlenia używać adresu URL zamiast używana wcześniej oryginalny adres URL repozytorium.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z języka Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz także

- [Ręczne identyfikowanie istniejących interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).
- [Zainstaluj obsługę języka Python w programie Visual Studio 2015 i starszych wersji](installing-python-support-in-visual-studio.md).
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations).
