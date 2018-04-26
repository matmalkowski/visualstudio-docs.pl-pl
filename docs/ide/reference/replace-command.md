---
title: Zastąp — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b712ee88526585d24ffd7b22fadbbf015c3d131
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="replace-command"></a>Zastąp — Polecenie
Zamienia tekst w plikach za pomocą podzbiór opcje dostępne na **Zastąp w plikach** karcie **Znajdź i Zamień** okna.

## <a name="syntax"></a>Składnia

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
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

 / doc lub /d

 Opcjonalna. Wyszukuje tylko bieżącego dokumentu. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 / hidden lub /h

 Opcjonalna. Wyszukiwanie tekstu ukryte i zwinięte, takich jak metadanych formant czasu projektowania, ukryty obszar konspektu dokumentu lub zwinięte klasy lub metody.

 / Open lub /o

 Opcjonalna. Przeszukuje wszystkie otwarte dokumenty, tak jakby były to jeden dokument. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 / Options lub /t

 Opcjonalna. Wyświetla listę bieżące ustawienia opcji wyszukiwania, a nie przeprowadza wyszukiwanie.

 /proc lub /p

 Opcjonalna. Wyszukuje bieżącą procedurę. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 /regex lub /r

 Opcjonalna. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji reprezentujących wzorce tekstu, a nie literał znaków. Pełną listę znaków wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).

 / Reset lub/e

 Opcjonalna. Zwraca opcje Znajdź do ustawień domyślnych i nie wykonuje wyszukiwanie.

 /SEL lub/s

 Opcjonalna. Wyszukuje tylko bieżące zaznaczenie. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 /Up lub /u

 Opcjonalna. Wyszukiwanie z bieżącej lokalizacji w pliku w kierunku do góry pliku. Domyślnie wyszukiwanie rozpoczyna się w bieżącej lokalizacji w pliku i wcześniejszym kierunku końca pliku.

 /Wild lub/l

 Opcjonalna. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji do reprezentowania znaków ani sekwencji znaków.

 opcji lub /w

 Opcjonalna. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
 W tym przykładzie zastępuje `btnSend` z `btnSubmit` we wszystkich otwieranie dokumentów.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Zobacz też

- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)