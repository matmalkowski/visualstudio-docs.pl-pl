---
title: Czujka — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97fe1c6865b8934d2c0329547e98323c75bf3ec0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="watch-command"></a>Czujka — Polecenie
Tworzy i otwiera określone wystąpienie programu **czujki** okna. Można użyć **czujki** okna do obliczania wartości zmiennych, wyrażenia i rejestrów, aby edytować te wartości i zapisać wyniki.

## <a name="syntax"></a>Składnia

```
Debug.Watch[index]
```

## <a name="arguments"></a>Argumenty
 `index`

 Wymagana. Liczba wystąpień okna czujki.

## <a name="remarks"></a>Uwagi
 `index` Musi być liczbą całkowitą. Prawidłowe wartości to 1, 2, 3 lub 4.

## <a name="example"></a>Przykład

```
>Debug.Watch1
```

## <a name="see-also"></a>Zobacz też

- [Automatyczne i ustawień regionalnych systemu Windows](../../debugger/autos-and-locals-windows.md)
- [Ustaw czujki na zmiennych czujki i QuickWatch Windows w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)