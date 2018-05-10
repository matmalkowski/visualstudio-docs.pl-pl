---
title: Przejdź do — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e583ee3bcb764d09bed9907710454dd6c39c6b8d
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="go-to-command"></a>Przejdź do — Polecenie
Przesuwa kursor do określonego wiersza.

## <a name="syntax"></a>Składnia

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumenty
 `linenumber`

 Opcjonalna. Liczba całkowita reprezentująca numer wiersza, aby przejść do.

## <a name="remarks"></a>Uwagi
 Rozpoczyna się numerowanie wierszy w jednej. Jeśli wartość `linenumber` jest mniejsza niż jedna, pierwszy wyświetla wiersza. Jeśli wartość `linenumber` jest większy niż numer ostatniego wiersza ostatniego Wyświetla wiersza.

 Jeśli określono wartość `linenumber` nie zostanie określony, **przejdź do wiersza** Wyświetla okno dialogowe.

 Alias dla tego polecenia jest GoToLn.

## <a name="example"></a>Przykład

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)