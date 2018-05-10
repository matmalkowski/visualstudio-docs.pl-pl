---
title: Znajdź w plikach — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4cf5078bb16d90744b83dfd99cf0c1da663149a
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="find-in-files-command"></a>Znajdź w plikach — Polecenie
Wyszukiwania plików przy użyciu podzbiór opcje dostępne na **Znajdź w plikach** karcie **Znajdź i Zamień** okna.

## <a name="syntax"></a>Składnia

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumenty
 `findwhat` Wymagane. Tekst do dopasowania.

## <a name="switches"></a>Przełączniki
 /Case lub /c opcjonalne. Dopasowań występuje tylko w przypadku wielkich i małych liter dokładnie odpowiadać określone w `findwhat` argumentu.

 /ext: `extensions` opcjonalne. Określa rozszerzenia plików dla plików do przeszukania. Jeśli nie zostanie określony, poprzednie rozszerzenie zostanie użyty, jeśli zostało wprowadzone wcześniej.

 /lookin: `searchpath` opcjonalne. Katalog do wyszukiwania. Jeśli ścieżka zawiera spacje, ujmij całą ścieżkę w cudzysłów.

 /names lub /n opcjonalne. Wyświetla listę nazw plików, które zawierają dopasowania.

 / Options lub /t opcjonalne. Wyświetla listę bieżące ustawienia opcji wyszukiwania, a nie przeprowadza wyszukiwanie.

 /regex lub /r opcjonalne. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji reprezentujących wzorce tekstu, a nie literał znaków. Pełną listę znaków wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).

 / Reset lub /e opcjonalne. Zwraca opcje Znajdź do ustawień domyślnych i nie wykonuje wyszukiwanie.

 / stop opcjonalne. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Wyszukiwanie ignoruje wszystkie inne argumenty podczas `/stop` został określony. Na przykład aby zatrzymać bieżące wyszukiwanie należy wprowadzić następujące:

```cmd
>Edit.FindinFiles /stop
```

 /Sub lub /s opcjonalne. Wyszukuje podfolderów znajdujących się w katalogu określonym w /lookin:`searchpath` argumentu.

 /text2 lub /2 opcjonalne. Wyświetla wyniki wyszukiwania w oknie Znajdź 2 wyników.

 /Wild lub /l opcjonalne. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji do reprezentowania znaków ani sekwencji znaków.

 opcji lub /w opcjonalne. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
 W tym przykładzie szuka btnCancel we wszystkich plikach .cls znajdujące się w folderze "Moje projektów programu Visual Studio" i wyświetla informacje dopasowania w oknie Znajdź 2 wyniki.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Zobacz też

- [Znajdź w plikach](../../ide/find-in-files.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)