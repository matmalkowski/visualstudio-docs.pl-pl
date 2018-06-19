---
title: Lista źródeł — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03a5d0699fced4d01d439942081b359454bcf476
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943621"
---
# <a name="list-source-command"></a>Lista źródeł — Polecenie
Wyświetla określony wiersze kodu źródłowego.

## <a name="syntax"></a>Składnia

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Przełączniki
 / Liczba:`number`

 Opcjonalna. Określa liczbę wierszy do wyświetlenia.

 / Bieżącym

 Opcjonalna. Pokazuje bieżącego wiersza.

 / Plik:`filename`

 Opcjonalna. Ścieżka pliku do wyświetlenia. Jeśli nazwa pliku nie zostanie określony, polecenie wyświetla kod źródłowy dla wiersza bieżącej instrukcji.

 / Wiersz:`number`

 Opcjonalna. Pokazuje liczbę określonego wiersza.

 / ShowLineNumbers:`yes|no`

 Opcjonalna. Określa, czy do wyświetlania numerów wierszy.

## <a name="example"></a>Przykład
 W tym przykładzie przedstawiono kodu źródłowego z wiersza 4 pliku Form1.vb, numery wierszy są widoczne.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)