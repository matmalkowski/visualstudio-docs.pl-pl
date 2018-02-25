---
title: "Szybki Start - w klonowania repozytorium kodu języka Python w programie Visual Studio | Dokumentacja firmy Microsoft"
description: "Rozpoczynanie pracy szybko przy użyciu języka Python w klonowania repozytorium koans Python za pomocą programu Visual Studio Team Explorer."
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: a7ddd0f7cf24805eef529d08bf0e37b19fc6a8bc
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Szybki Start: klonowanie repozytorium kodu języka Python w programie Visual Studio

Po wprowadzeniu [zainstalowane obsługę języka Python w Visual Studio 2017](installing-python-support-in-visual-studio.md), można łatwo Klonuj repozytorium kodu Python i utworzyć projekt z niego.

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

2. Uruchom program Visual Studio.

3. Wybierz **Widok > Team Explorer...**  otworzyć **Team Explorer** okna, w którym można nawiązać połączenia z usługi GitHub lub Visual Studio Team Services lub sklonować repozytorium.

    ![Zespół przedstawiający okno Eksploratora Visual Studio Team Services, GitHub i klonowanie repozytorium](media/team-explorer.png)

4. W polu adresu URL **lokalnego repozytoria Git**, wprowadź `https://github.com/gregmalcolm/python_koans`, wprowadź folder plików sklonowany i wybierz **klonowania**.

    > [!Tip]
    > Folder, który określisz w programie Team Explorer jest konkretnego folderu do odbierania sklonowany plików. W przeciwieństwie do `git clone` poleceń, utworzenie klona w programie Team Explorer nie tworzy automatycznie podfolder o nazwie repozytorium.

5. Kiedy klonowanie zostanie ukończone, kliknij dwukrotnie folder repozytorium w dolnej części Team Explorer, aby przejść do pulpitu nawigacyjnego repozytorium. W obszarze **rozwiązań**, wybierz pozycję **nowy...** .

    ![Okno Eksploratora zespołu, tworzenia nowego projektu z klonu](media/team-explorer-new-project.png)

6. W **nowy projekt** okno dialogowe zostanie wyświetlone, wybierz "Z istniejących Python Code", określ nazwę dla projektu, ustaw **lokalizacji** na tym samym folderze co repozytorium, a następnie wybierz **OK**. W oknie kreatora wybierz **Zakończ**.

7. Wybierz **Widok > Eksploratora rozwiązań** z menu.

8. W Eksploratorze rozwiązań rozwiń `python3` węzła, kliknij prawym przyciskiem myszy `contemplate_koans.py`i wybierz **Ustaw jako plik uruchamiania**. W tym kroku opisano Visual Studio plik, który należy używać, gdy uruchamiania projektu.

9. Wybierz **projektu > właściwości** z menu wybierz **ogólne** , a następnie ustaw **katalog roboczy** do "python3". Jest to konieczne, ponieważ domyślnie program Visual Studio Ustawia katalog roboczy katalogu głównym projektu, a nie lokalizacja pliku uruchamiania (`python3\contemplate_koans.py`, który można wyświetlić w oknie właściwości projektu). Kod programu szuka pliku `koans.txt` folderu roboczego, tak zmieniając tę wartość jest widoczny błąd w czasie wykonywania.

    ![Ustawianie katalogu roboczego dla projektów języka Python](media/projects-set-working-directory.png)

10. Naciśnij klawisze Ctrl + F5 lub wybierz **Debuguj > Uruchom bez debugowania** do uruchomienia programu. Jeśli widzisz `FileNotFoundError` dla `koans.txt`, ponownie Sprawdź katalog roboczy ustawienia w poprzednim kroku.

11. Jeśli program zostanie uruchomiony pomyślnie, wyświetla błąd potwierdzenia w wierszu 17 `python3/koans/about_asserts.py`. Jest to zamierzone: program jest przeznaczony do nauki, Python, konfigurując należy poprawić wszystkie błędy zamierzone. (Szczegółowe informacje znajdują się na [Ruby Koans](http://rubykoans.com/), który inspirowana Python Koans.)

    ![Pierwsze dane wyjściowe z programu koans języka Python](media/koans-output.png)

12. Otwórz `python3/koans/about_asserts.py` przejdź do niego w Eksploratorze rozwiązań, a następnie klikając dwukrotnie plik. Należy zauważyć, że numery wierszy nie są wyświetlane domyślnie w edytorze. Aby zmienić to ustawienie, wybierz **Narzędzia > Opcje**, wybierz pozycję **Pokaż wszystkie ustawienia** w dolnej części okna dialogowego, a następnie przejdź do **Edytor tekstu > Python > Ogólne** i wybierz pozycję **Numerów linii**:

    ![Włączanie numer wiersza dla plików języka Python](media/options-general-line-numbers.png)

13. Popraw błąd, zmieniając `False` argument w wierszu 17 do `True`. Wiersz powinien wyglądać następująco:

    ```python
    self.assertTrue(True) # This should be True
    ```

14. Uruchom program ponownie, aby zobaczyć, czy pierwszy wyboru przekazuje i zatrzymuje program na koan dalej. Kontynuuj, naprawa błędów i uruchom ponownie program można dowolnie.

> [!Important]
> W tego przewodnika Szybki Start, został utworzony bezpośrednio Sklonowanie *python_koans* repozytorium w witrynie GitHub. Takie repozytorium jest chroniony przez jego autora z zmian bezpośrednio, dlatego próba Zatwierdź zmiany do repozytorium kończy się niepowodzeniem. W praktyce deweloperzy rozwidlania zamiast tego repozytorium do ich własnego konta GitHub, wprowadzić zmiany, a następnie utwórz żądania ściągnięcia do przesyłania tych zmian w oryginalnej repozytorium. Te kroki opisano w [samouczek krok 6 — Praca z usługą Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z języka Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz także

- [Ręczne identyfikowanie istniejących interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).
- [Zainstaluj obsługę języka Python w programie Visual Studio 2015 i starszych wersji](installing-python-support-in-visual-studio.md).
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations).
