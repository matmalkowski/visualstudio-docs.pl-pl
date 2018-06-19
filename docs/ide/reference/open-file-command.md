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
ms.openlocfilehash: d238370586a9256d91f89f06fddbe3c58abc27e8
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703824"
---
# <a name="open-file-command"></a>Otwórz plik — Polecenie
Otwiera istniejący plik i umożliwia określenie edytora.

## <a name="syntax"></a>Składnia

```cmd
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

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Uwagi
 Podczas wprowadzania ścieżki automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku.

## <a name="example"></a>Przykład
 W tym przykładzie otwiera plik stylu "Test1.css" w edytorze kodu źródłowego.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Okno bezpośrednie](../../ide/reference/immediate-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)