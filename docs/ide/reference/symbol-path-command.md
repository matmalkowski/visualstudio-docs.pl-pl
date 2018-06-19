---
title: Ścieżka symboli — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22a27d795e5491081dca98a395c788cf8407e43e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942773"
---
# <a name="symbol-path-command"></a>Ścieżka symboli — Polecenie
Ustawia listę katalogów dla debugera do wyszukiwania symboli.

## <a name="syntax"></a>Składnia

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Argumenty
 `pathname`

 Opcjonalna. Rozdzielany średnikami lista ścieżek debugera do wyszukiwania symboli.

## <a name="remarks"></a>Uwagi
 Jeśli nie `pathname` jest określony, polecenie wyświetla listę bieżącej ścieżki symboli.

## <a name="example"></a>Przykład
 W tym przykładzie dodaje dwie ścieżki do listy katalogów symbolu.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Przykład
 Ten przykład przedstawia rozdzielaną średnikami listę bieżącej ścieżki symboli.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Zobacz też

- [Okno Polecenie](../../ide/reference/command-window.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)