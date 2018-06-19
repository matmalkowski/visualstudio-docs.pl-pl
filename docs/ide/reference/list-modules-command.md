---
title: Lista modułów — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 54e975cf886f0bb8392bd3679a28bae6bb6bfe00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944664"
---
# <a name="list-modules-command"></a>Lista modułów — Polecenie
Wyświetla listę modułów dla bieżącego procesu.

## <a name="syntax"></a>Składnia

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametry
 / Adres:`yes|no`

 Opcjonalna. Określa, czy wyświetlać adresy pamięci w modułach. Wartość domyślna to `yes`.

 / Name:`yes|no`

 Opcjonalna. Określa, czy są wyświetlane nazwy modułów. Wartość domyślna to `yes`.

 / Order:`yes|no`

 Opcjonalna. Określa, czy z kolejnością modułów. Wartość domyślna to `no`.

 / Path:`yes|no`

 Opcjonalna. Określa, czy ścieżki modułów. Wartość domyślna to `yes`.

 / Proces:`yes|no`

 Opcjonalna. Określa, czy Pokaż procesy modułów. Wartość domyślna to `no`.

 / SymbolFile:`yes|no`

 Opcjonalna. Określa, czy wyświetlać pliki symboli modułów. Wartość domyślna to `no`.

 / SymbolStatus:`yes|no`

 Opcjonalna. Określa, czy mają być wyświetlane stany symboli modułów. Wartość domyślna to `yes`.

 / Sygnatura czasowa:`yes|no`

 Opcjonalna. Określa, czy pokazywać sygnatury czasowe modułów. Wartość domyślna to `no`.

 / Version:`yes|no`

 Opcjonalna. Określa, czy Pokaż wersje modułów. Wartość domyślna to `no`.

## <a name="example"></a>Przykład
 W tym przykładzie przedstawiono nazwy modułu, adresy i sygnatury czasowe dla bieżącego procesu.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Porady: Korzystanie z okna modułów](../../debugger/how-to-use-the-modules-window.md)