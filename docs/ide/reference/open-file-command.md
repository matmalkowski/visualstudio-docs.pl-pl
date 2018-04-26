---
title: Otwórz plik — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd75d32021f2dd3f6ac1ef76772ea30376ea1b8a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="open-file-command"></a>Otwórz plik — Polecenie
Otwiera istniejący plik i umożliwia określenie edytora.

## <a name="syntax"></a>Składnia

```
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename`

 Wymagana. Pełnej lub częściowej ścieżkę i nazwę pliku, aby otworzyć. Ścieżek zawierających spacje musi być ujęta w cudzysłów.

## <a name="switches"></a>Przełączniki
 / e:`editorname`

 Opcjonalna. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument zostanie określony, ale zostanie podana żadna nazwa edytora, **Otwórz za pomocą** zostanie wyświetlone okno dialogowe.

 / E:`editorname` argumentu składni korzysta z nazw Edytor znajdujące się w otwartych z okno dialogowe, ujęty w cudzysłów.

 Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Uwagi
 Podczas wprowadzania ścieżki automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku.

## <a name="example"></a>Przykład
 W tym przykładzie otwiera plik stylu "Test1.css" w edytorze kodu źródłowego.

```
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Okno bezpośrednie](../../ide/reference/immediate-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)