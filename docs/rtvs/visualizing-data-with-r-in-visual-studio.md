---
title: Wizualizacja danych za pomocą języka R
description: Jak do wykreślenia danych z programów R w programie Visual Studio przy użyciu systemu windows kreślenia.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 0a11ef12a4ca38c2973c01575b59ef35826bc4a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="creating-visual-data-plots-with-r"></a>Tworzenie danych wizualnych geograficzne z języka R

Kreślenia jest kluczowym elementem naukowca danych przepływu pracy. W menu Narzędzia R dla programu Visual Studio (RTVS) wszystkie działania kreślenia koncentruje się wokół co najmniej jeden wykres systemu windows, które mają na celu poprawę wydajności dzięki tego klucza działania.

![Obraz bohater kreślenia](media/plotting-hero-image.png)

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (witrynie youtube.com)](https://www.youtube.com/watch?v=ZTbKmz5RSgY) na kreślenia z R (2 m 02s). |

## <a name="the-plot-window"></a>Okno kreślenia

Okno kreślenia przechowuje serii wykresów, gdzie każdy wykres jest generowany przez `plot` polecenia. Na przykład za pomocą `plot(1:100)` tworzy nowe okno wykresu, jeśli jeden nie jest już dostępny:

![Wykres liniowy 1 do 100](media/plotting-1-to-100.png)

Jak to działa, R `plot` polecenia renderować swoje dane wyjściowe do urządzenia graficznego R; okna kreślenia renderuje zawartość urządzenia graficznego R, dlatego każde okno kreślenia znajduje się numer urządzenia.

Windows kreślenia są niezależne od projektów programu Visual Studio i pozostają otwarte, obciążenia i zamknąć projektów.

Generowanie wykresu używa okna kreślenia "active" zapisywania wszystkie poprzednie wykreślenia go historii kreślenia (zobacz [wykreślenia historii](#plot-history)). Na przykład wprowadź `plot(100:1)` i pierwszy wykres jest zastępowany wiersz w dół.

Podobnie jak wszystkie inne okna programu Visual Studio. Okno kreślenia obsługuje niestandardowe układy (zobacz [dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Kreślenia systemu windows można zadokowane w różnych lokalizacjach w ramce programu Visual Studio, zmiany rozmiaru w tej ramce lub pobierane poza ramki dla całkowicie niezależne zmiany rozmiaru. 

Zmiana rozmiaru okna kreślenia zawsze renderuje ponownie kreślenia, aby zapewnić najlepszą jakość obrazu. Zwykle można zmienić rozmiar wykresu przed wyeksportowaniem na powierzchni do pliku lub do Schowka za pomocą poleceń opisanych w następnej sekcji.

## <a name="plot-window-commands"></a>Polecenia okna kreślenia

Pasek narzędzi okna kreślenia posiada odpowiednich poleceń, z których większość są również dostępne za pośrednictwem **narzędzia R > powierzchni** menu.

| Przycisk | Polecenie | Opis | 
| --- | --- | --- |
| ![Nowy przycisk okna kreślenia](media/plotting-toolbar-01-new-plot-window.png) | Nowe okno wykresu | Tworzy okno oddzielnych powierzchni z własną historią. Zobacz [wiele okien kreślenia](#multiple-plot-windows). |
| ![Włączenie przycisku okna kreślenia](media/plotting-toolbar-02-activate-plot-window.png) | Uaktywnij okno kreślenia | Ustawia bieżące okno kreślenia jako aktywne okno, tak że kolejne `plot` polecenia są renderowane do tego okna. Zobacz [wiele okien kreślenia](#multiple-plot-windows). Zobacz [wiele okien kreślenia](#multiple-plot-windows). |
| ![Wykres historii okna](media/plotting-toolbar-03-plot-history.png) | Okno historii kreślenia | Otwiera okno z wszystkich powierzchni w historii wyświetlane jako miniatury. Zobacz [wykreślenia historii](#plot-history). |
| ![Przyciski historii kreślenia](media/plotting-toolbar-04-plot-history-arrows.png) | Poprzedni i następny kreślenia |  Powoduje przejście do poprzedniego lub następnego kreślenia w historii. Można także przechodzić historii kodu za pomocą klawiszy Ctrl + Alt + F11 (poprzedni) i Ctrl + Alt + F12 (dalej). Zobacz [wykreślenia historii](#plot-history). |
| ![Zapisz jako obraz przycisku](media/plotting-toolbar-05-save-as-image.png)| Zapisz jako obrazu | Monit o podanie nazwy pliku i zapisanie bieżącego kreślenia (zawartość okna, w rozmiarze okna) do pliku obrazu. Są dostępne formaty `.png`, `.jpg`, `.bmp`, i `.tif`. |
| ![Zapisz jako przycisk PDF](media/plotting-toolbar-06-save-as-pdf.png)| Zapisz jako PDF | Zapisuje bieżący kreślenia plik PDF, za pomocą bieżącego rozmiaru okna. Powierzchni ponownie spowoduje, że w przypadku zmiany skali pliku PDF. |
| ![Kopiuj jako przycisk mapy bitowej](media/plotting-toolbar-07-copy-as-bitmap.png)| Kopiuj jako mapy bitowej | Kopiuje powierzchni do Schowka jako rastrowe mapy bitowej, przy użyciu bieżącego rozmiaru okna. | 
| ![Kopiuj jako przycisk metaplik](media/plotting-toolbar-08-copy-as-metafile.png)| Kopiuj jako metaplik | Kopiuje do Schowka jako powierzchni [Windows metafile](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedia). | 
| ![Usuń przycisk kreślenia](media/plotting-toolbar-09-remove-plot.png)| Usuń kreślenia | Usuwa bieżący kreślenia z historii. |
| ![Przycisk Wyczyść wszystko powierzchni](media/plotting-toolbar-10-clear-all-plots.png) | Wyczyść wszystkie powierzchnie | Usuwa wszystkie powierzchnie z historii (wyświetla monit o potwierdzenie). |

## <a name="multiple-plot-windows"></a>Wiele okien kreślenia

Ponieważ analityków danych często pracować z wielu powierzchni z wielu różnych zestawów danych, RTVS pozwala utworzyć dowolną liczbę niezależnych kreślenia systemu windows. Następnie można rozmieścić tych z systemem windows, jednak chcesz całkowicie w ramce Visual Studio lub spoza tej ramki. (Zobacz [dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) ogólne informacje na temat zadokowane i zmiany rozmiaru okna.)

Utwórz nowe okno wykresu za pomocą przycisku paska narzędzi lub **narzędzia R > powierzchni > nowe okno wykresu**. Staje się nowe okno wykresu *active* okna, które jest, gdzie mają być renderowane nowych powierzchni. Aby zmienić aktywnego okna, przełącz się do niego i kliknij przycisk Aktywuj wykreślenia okna narzędzi lub **narzędzia R > geograficzne > aktywować okno wykreślenia**.

Wykresy, zbyt, są niezależne obiektów, co oznacza można skopiować lub przenieść je między kreślenia systemu windows za pomocą obu przeciągania i upuszczania za pomocą myszy lub za pomocą **kopiowania**, **Wytnij**, i **Wklej** polecenia w kontekście kliknij prawym przyciskiem myszy i **Edytuj** menu.

Domyślnym zachowaniem przeciągania i upuszczania jest kopiowania; Aby przenieść, przeciągnij i upuść trzymając naciśnięty klawisz Shift.

## <a name="plot-history"></a>Historia kreślenia

Polecenia kreślenia są obsługiwane w historii wykresu dla każdego okna, zapewniając, że wszystkie Twoje kreślenia w ramach sesji jest zachowywany. Aby poruszać historii, użyj przycisków strzałek na powierzchni okna narzędzi lub Ctrl + Alt + F11 i Ctrl + Alt + F12. Można również usunąć pojedynczego powierzchni lub wyczyść wszystkie powierzchnie z okna ponownie, używając przycisków paska narzędzi lub **narzędzia R > geograficzne** poleceń menu.

Aby wyświetlić całą kolekcję powierzchni, Otwórz okno Historia kreślenia za pomocą przycisku paska narzędzi lub **narzędzia R > geograficzne > okno historii kreślenia**.
Historia zawiera listę miniatur dla powierzchni, które były wyświetlane w danym przedziale pogrupowane według różnych kreślenia systemu windows (lub urządzenia). Używanie przycisków powiększenia na pasku narzędzi zmienia rozmiar miniatur.

![Okno historii kreślenia](media/plotting-plot-history-window.png)

Aby otworzyć wykresu w jego oknie skojarzone, kliknij dwukrotnie ten wykres, zaznacz go, a następnie wybierz **Pokaż kreślenia** przycisku paska narzędzi lub kliknij prawym przyciskiem myszy i wybierz **Pokaż kreślenia**. Możesz również wybrać poszczególne kreślenia i skopiuj, Wytnij lub Usuń kontekst kliknij prawym przyciskiem myszy lub **Edytuj** menu.

Okres istnienia historii kreślenia we wszystkich okien jest powiązany z okres istnienia sesji R interaktywnego. Zresetuj sesję R lub zamknięcia i ponownego uruchomienia programu Visual Studio jest resetowany historii kreślenia.

## <a name="programmatically-manipulating-plot-windows"></a>Programowo manipulowanie kreślenia systemu windows

Można programowo manipulować windows kreślenia z kodu języka R, przy użyciu numerów urządzeń do identyfikowania kreślenia określonego systemu windows. 

- `dev.list()`: Wyświetl listę wszystkich urządzeń grafiki w bieżącej sesji R.
- `dev.new()`: Tworzenie nowego urządzenia graficznego (nowe okno wykresu).
- `dev.set(<device number>)`: Ustaw urządzenia active graficznego.
- `dev.off()`: Usuwanie aktywnego urządzenia.
