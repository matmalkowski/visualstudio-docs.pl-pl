---
title: IntelliSense dla kodu języka R
description: Visual Studio IntelliSense wyświetla informacje o funkcji, elementach członkowskich obiektu, fragmentów kodu i zakończeń, pisania kodu języka R.
ms.custom: ''
ms.date: 01/24/2018
ms.technology:
- devlang-r
dev_langs:
- R
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: a5ba810cc1dc988a72de1e9e596578bca1ae85e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense wyświetla informacje na temat funkcji, można wywołać członkami obiektów, argumenty funkcji i [wstawki kodu](code-snippets-for-r.md) bezpośrednio w widoku podczas pisania kodu. On również wyświetla możliwe uzupełnienia podczas wpisywania, a działanie jest kończone po naciśnięciu klawiszy Tab lub Enter (zobacz [opcji edytora](editing-r-code-in-visual-studio.md#editor-options) dla **zaawansowane** kartę). Technologia IntelliSense jest dostępna w edytorze programu i [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md).

![Wyświetlanie sygnatura funkcji IntelliSense](media/intellisense-function-signature.png)

Podczas wpisywania, funkcji lub innych instrukcji, IntelliSense zapewnia automatyczne uzupełnianie menu (case-sensitively) filtrowane według co zostały już wprowadzone:

![Menu automatycznego uzupełniania IntelliSense](media/intellisense-auto-complete-menu.png)

Naciśnięcie klawisza Tab (lub Enter lub miejsca, w zależności od konfiguracji opcji), wstawia elementu wybranego w listy rozwijanej. Zaznaczenie można zmienić za pomocą klawiszy strzałek.

IntelliSense zawiera też propozycje członkami R obiektów:

![Sugestie IntelliSense dla elementów członkowskich obiektu](media/intellisense-auto-complete-r-objects.png)

Naciśnięcie klawisza ESC odrzuci całkowicie menu. Można przenieść go Utwórz kopię zapasową z klawiszy Ctrl + spacja.

Wpisywanie otwarcia `(` dla funkcji wywołania Wstawia zamykający `)` i wywołuje pomoc podpis, jak pokazano wcześniej:

![Pomoc podpisu IntelliSense dla funkcji](media/intellisense-function-signature.png)

Ponownie ESC odrzuci podręcznego; dla sygnatury funkcji można przenieść go ponownie z klawiszy Ctrl + Shift + spacja.

> [!Tip]
> Jeśli parametr pomocy ukrywa tekst podrzędne, naciśnij i przytrzymaj klawisz Ctrl, aby parametr półprzezroczyste tekst pomocy.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense dla użytkownika funkcje i zmienne

Dotyczy funkcji IntelliSense dla funkcji zdefiniowanej przez użytkownika w tym samym pliku, w tym zakończenia parametr name:

![IntelliSense dla funkcji zdefiniowanej przez użytkownika](media/intellisense-same-file-functions.png)

![Uzupełnianie parametru IntelliSense funkcje zdefiniowane przez użytkownika](media/intellisense-parameter-completion.png)

IntelliSense ma zastosowanie również do zmiennych w tym samym pliku i bieżącej sesji:

![Zmienna uzupełniania IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> W oknie interaktywnym IntelliSense uwzględnia tylko nazwy w bieżącej sesji R i ignoruje pliki w projekcie.

## <a name="code-suggestions"></a>Sugestie kodu

Gdy żarówka (nazywane tagów inteligentnych) pojawi się na marginesie, Visual Studio jest sugerowanie dostępne dla często używanych akcji jest skrót. Na przykład, umieść kursor nad wiersz, który zawiera `library` instrukcji w edytorze, aby zobaczyć żarówka. Wybieranie żarówkę Wyświetla dostępne opcje:

![Tagi inteligentne R w edytorze](media/intellisense-smart-tags.png)
