---
title: Szybka czujka — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 957f521b23bc56a6bfa4f8de315f130d5f82d8d3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="quick-watch-command"></a>Szybka czujka — Polecenie
Wyświetla wybrany lub określony tekst w polu wyrażenie [QuickWatch](../../debugger/watch-and-quickwatch-windows.md) okna. To okno dialogowe służy do obliczania bieżącą wartość zmiennej lub wyrażenie rozpoznawane przez debuger lub zawartość rejestru. Ponadto można zmienić wartość zmiennej żadnych wartością stałą lub zawartość dowolnego rejestru.

## <a name="syntax"></a>Składnia

```
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumenty
 `text`

 Opcjonalna. Tekst, aby dodać do **QuickWatch** okno dialogowe.

## <a name="remarks"></a>Uwagi
 Jeśli `text` jest pominięty, aktualnie zaznaczonego tekstu lub word wskazywanej przez kursor jest dodawany do okna czujki.

## <a name="example"></a>Przykład

```
>Debug.QuickWatch
```

## <a name="see-also"></a>Zobacz też

- [Ustaw czujki na zmiennych czujki i QuickWatch Windows w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)