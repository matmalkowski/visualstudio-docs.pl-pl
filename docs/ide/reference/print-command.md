---
title: Print — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7cf241ec0a9ff849b52761a241e84a15d287bb88
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="print-command"></a>Print — Polecenie
Oblicza wyrażenie lub wyświetla określony tekst.

## <a name="syntax"></a>Składnia

```
Debug.Print text
```

## <a name="arguments"></a>Argumenty
 `text`

 Wymagana. Wyrażenie do oceny lub tekst do wyświetlenia.

## <a name="remarks"></a>Uwagi
 Znak zapytania (?) można użyć jako alias dla tego polecenia. Tak na przykład, polecenie

```
>Debug.Print expA
```

 można również zapisać

```
>? expA
```

 Obie wersje to polecenie zwróci bieżącą wartość wyrażenia `expA`.

## <a name="example"></a>Przykład

```
>Debug.Print varA
```

## <a name="see-also"></a>Zobacz też

- [Oceń instrukcję, polecenie](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)