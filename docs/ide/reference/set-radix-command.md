---
title: Ustaw Radix — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f23e2492a183dcae2e2b3cb87e39b08f66a7c2ae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="set-radix-command"></a>Ustaw Radix — Polecenie
Ustawia lub zwraca base liczbowego, używany do wyświetlania wartości będące liczbami całkowitymi.

## <a name="syntax"></a>Składnia

```
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumenty
 `10` lub `16` lub `hex` lub `dec`

 Opcjonalna. Wskazuje dziesiętna (10 lub gru) lub liczba szesnastkowa (16 lub szesnastkowych). Jeśli argument zostanie pominięty, zwracany jest bieżąca wartość Podstawa.

## <a name="example"></a>Przykład
 W tym przykładzie środowiska do wyświetlenia w formacie szesnastkowym wartości będące liczbami całkowitymi.

```
>Debug.SetRadix hex
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)