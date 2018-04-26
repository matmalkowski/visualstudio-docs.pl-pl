---
title: Evaluate Statement — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c2ec882bb2fdc9d0f3b74a0552c85a7b286617c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="evaluate-statement-command"></a>Evaluate Statement — Polecenie
Oblicza i wyświetla podanej instrukcji.

## <a name="syntax"></a>Składnia

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Argumenty
 `text` Wymagane. Instrukcja do oceny.

## <a name="remarks"></a>Uwagi
 Okno służy do wprowadzania **EvaluateStatement** polecenie Określa, czy znak równości (=) jest interpretowany jako operator porównania lub operator przypisania.

 W **polecenia** okna, znak równości (=) jest interpretowana jako operator porównania. Na przykład, jeśli wartości zmiennych `a` i `b` są różne, a następnie polecenie

```
>Debug.EvaluateStatement(a=b)
```

 Zwraca wartość `false`.

 W **Immediate** okna, natomiast znak równości (=) jest interpretowana jako operatora przypisania. Tak na przykład, polecenie

```
>Debug.EvaluateStatement(a=b)
```

 zostanie przypisana do zmiennej `a` wartość zmiennej `b`.

## <a name="example"></a>Przykład

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Zobacz też

- [Drukuj, polecenie](../../ide/reference/print-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)