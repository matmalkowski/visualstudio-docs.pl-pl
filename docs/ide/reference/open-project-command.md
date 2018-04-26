---
title: Otwórz projekt — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09241e72119a0a0973995b16152941bbe5272c3f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="open-project-command"></a>Otwórz projekt — Polecenie
Otwiera istniejący projekt.

## <a name="syntax"></a>Składnia

```
File.OpenProject filename
```

## <a name="arguments"></a>Argumenty
 `filename`

 Wymagana. Pełna ścieżka i nazwa projektu, aby otworzyć.

 Składnia `filename` wymaga argumentu ścieżek zawierających spacje, użyj cudzysłowów.

## <a name="remarks"></a>Uwagi
 Automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas pisania.

 To polecenie nie jest dostępna podczas debugowania.

## <a name="example"></a>Przykład
 W tym przykładzie otwiera [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu Test1.

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)