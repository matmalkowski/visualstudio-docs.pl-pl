---
title: Uruchomienie — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1e5ade7d02882633504ac5615ee751b2533adde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="start-command"></a>Uruchomienie — Polecenie
Rozpoczyna debugowania projektu startowego.

## <a name="syntax"></a>Składnia

```
Debug.Start [address]
```

## <a name="arguments"></a>Argumenty
 `address`

 Opcjonalna. Adres, pod którym program wstrzymuje wykonywanie, podobnie jak punkt przerwania w kodzie źródłowym. Ten argument jest prawidłowy tylko w trybie debugowania.

## <a name="remarks"></a>Uwagi
 **Start** polecenia po wykonaniu wykonuje operację RunToCursor do określonego adresu.

## <a name="example"></a>Przykład
 W tym przykładzie uruchomienie debugera i ignoruje wszelkie wyjątki, które występują.

```
>Debug.Start
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)