---
title: Find — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb84e7305797522c7e34e387357eedfdcd61e88f
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704190"
---
# <a name="find-command"></a>Find — Polecenie
Wyszukuje pliki przy użyciu podzbiór opcje dostępne na **Znajdź w plikach** karcie **Znajdź i Zamień** okna.

## <a name="syntax"></a>Składnia

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumenty
 `findwhat` Wymagane. Tekst do dopasowania.

## <a name="switches"></a>Przełączniki
 /Case lub /c opcjonalne. Dopasowań występuje tylko w przypadku wielkich i małych liter dokładnie odpowiadać określone w `findwhat` argumentu.

 / doc lub /d opcjonalne. Wyszukuje tylko bieżącego dokumentu. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 /markall lub/m opcjonalne. Umieszcza grafiki w każdym wierszu, zawierający zgodność wyszukiwania w bieżącym dokumencie.

 / Open lub /o opcjonalne. Przeszukuje wszystkie otwarte dokumenty, tak jakby były to jeden dokument. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 / Options lub /t opcjonalne. Wyświetla listę bieżące ustawienia opcji wyszukiwania, a nie przeprowadza wyszukiwanie.

 /proc lub /p opcjonalne. Wyszukuje bieżącą procedurę. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 / Reset lub /e opcjonalne. Zwraca opcje Znajdź do ustawień domyślnych i nie wykonuje wyszukiwanie.

 /SEL lub /s opcjonalne. Wyszukuje tylko bieżące zaznaczenie. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 /Up lub /u opcjonalne. Wyszukiwanie od bieżącej lokalizacji w pliku kierunku początku pliku. Domyślnie wyszukiwanie rozpoczyna się w bieżącej lokalizacji w pliku i wyszukiwania pod koniec pliku.

 /regex lub /r opcjonalne. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji reprezentujących wzorce tekstu, a nie literał znaków. Pełną listę znaków wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).

 /Wild lub /l opcjonalne. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji do reprezentowania znaków ani sekwencji znaków.

 opcji lub /w opcjonalne. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
 W tym przykładzie wykonuje wyszukiwanie z uwzględnieniem wielkości liter dla słowa "somestring" w aktualnie wybranej części kodu.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Zobacz też

- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)