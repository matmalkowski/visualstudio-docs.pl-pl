---
title: Zastąp w plikach — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8bf54892d17a877cd8e2c3ffd21ebd513e303d6c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946666"
---
# <a name="replace-in-files-command"></a>Zastąp w plikach — Polecenie
Zamienia tekst w plikach za pomocą podzbiór opcje dostępne na **Zastąp w plikach** karcie **Znajdź i Zamień** okna.

## <a name="syntax"></a>Składnia

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Argumenty
 `findwhat`

 Wymagana. Tekst do dopasowania.

 `replacewith`

 Wymagana. Tekst do zastąpienia dla dopasowanego tekstu.

## <a name="switches"></a>Przełączniki
 / all lub /a

 Opcjonalna. Zamienia wszystkie wystąpienia tekstu wyszukiwania tekst zastępczy.

 /Case lub /c

 Opcjonalna. Dopasowań występuje tylko wtedy, gdy po wielkich i małych liter dokładnie odpowiadać określone w `findwhat` argumentu.

 /ext: `extensions`

 Opcjonalna. Określa rozszerzenia plików dla plików do przeszukania.

 /Keep lub /k

 Opcjonalna. Określa, że wszystkie zmodyfikowane pliki pozostają otwarte.

 /lookin: `searchpath`

 Opcjonalna. Katalog do wyszukiwania. Jeśli ścieżka zawiera spacje, ujmij całą ścieżkę w cudzysłów.

 / Options lub /t

 Opcjonalna. Wyświetla listę bieżące ustawienia opcji wyszukiwania, a nie przeprowadza wyszukiwanie.

 /regex lub /r

 Opcjonalna. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji reprezentujących wzorce tekstu, a nie literał znaków. Pełną listę znaków wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).

 / Reset lub/e

 Opcjonalna. Zwraca opcje Znajdź do ustawień domyślnych i nie wykonuje wyszukiwanie.

 / stop

 Opcjonalna. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Zamień ignoruje wszystkie inne argumenty podczas `/stop` został określony. Na przykład można zatrzymać bieżącej zastąpienia należy wprowadzić następujące czynności:

```
>Edit.ReplaceinFiles /stop
```

 /Sub lub/s

 Opcjonalna. Wyszukuje podfolderów znajdujących się w katalogu określonym w /lookin:`searchpath` argumentu.

 /text2 lub /2

 Opcjonalna. Wyświetla wyniki zastąpienia w **znaleźć 2 wyniki** okna.

 /Wild lub/l

 Opcjonalna. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji do reprezentowania znaków ani sekwencji znaków.

 opcji lub /w

 Opcjonalna. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
 W tym przykładzie wyszukuje `btnCancel` i zastępuje go tekstem `btnReset` w .cls wszystkie pliki znajdujące się w folderze "Moje projekty visual studio" i wyświetla informacje dotyczące zastępowania w **znaleźć 2 wyniki** okna.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Zobacz też

- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)
- [Zastąp w plikach](../../ide/replace-in-files.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)