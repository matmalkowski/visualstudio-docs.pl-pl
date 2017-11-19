---
title: "IntelliSense dla języka R kodu programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3677-e5ec-4e11-82a8-d914a93b1aa9
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 821f92f7a3cf0e5ca1d647890602ec17e580b36b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense wyświetla informacje na temat funkcji, można wywołać członkami obiektów, argumenty funkcji i [wstawki kodu](code-snippets.md) bezpośrednio w widoku podczas pisania kodu. On również wyświetla możliwe uzupełnienia podczas wpisywania, a działanie jest kończone po naciśnięciu klawiszy Tab lub Enter (zobacz [opcji edytora](code-editing.md#editor-options) dla **zaawansowane** kartę). Technologia IntelliSense jest dostępna w edytorze programu i [okna interaktywnego](interactive-repl.md).

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
