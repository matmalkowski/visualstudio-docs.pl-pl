---
title: Ustaw bieżący proces
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 907ef900283cb3f15d9e65f7196c3cf42e191ed3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="set-current-process"></a>Ustaw bieżący proces
Ustawia określony proces jako aktywnego procesu w debugerze.

## <a name="syntax"></a>Składnia

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumenty
 `index`

 Wymagana. Indeks procesu.

## <a name="remarks"></a>Uwagi
 Możesz dołączyć do wielu procesów podczas debugowania, ale tylko jeden proces jest aktywny w dubber w danym momencie. Można użyć `SetCurrentProcess` polecenie, aby ustawić aktywnego procesu.

## <a name="example"></a>Przykład

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)