---
title: Lista wątków — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa44556be7c20c52d44ec83da1ba9d4972b4542d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="list-threads-command"></a>Lista wątków — Polecenie
Wyświetla listę wątki bieżącego programu.

## <a name="syntax"></a>Składnia

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumenty
 `index`

 Opcjonalna. Wybiera wątku przez jego indeksu bieżącego wątku.

## <a name="remarks"></a>Uwagi
 W przypadku `index` argumentu oznacza wskazanych wątku, co bieżący wątek. Znak gwiazdki (*) jest wyświetlana na liście obok bieżącego wątku.

## <a name="example"></a>Przykład

```
>Debug.ListThreads
```

## <a name="see-also"></a>Zobacz też

- [Lista stosu wywołań, polecenie](../../ide/reference/list-call-stack-command.md)
- [Lista dezasemblacji, polecenie](../../ide/reference/list-disassembly-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)