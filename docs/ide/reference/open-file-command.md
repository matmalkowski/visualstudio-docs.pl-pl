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
ms.openlocfilehash: 4be55cb2108b24c7a8f912844b719e6aa3135a06
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924003"
---
# <a name="open-file-command"></a>Otwórz plik — polecenie

Otwiera istniejący plik i pozwala na określenie edytora.

## <a name="syntax"></a>Składnia

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty

`filename`

Wymagane. Pełnej lub częściowej ścieżkę i nazwę pliku, aby otworzyć. Ścieżki zawierające spacje muszą być ujęte w znaki cudzysłowu.

## <a name="switches"></a>Przełączniki

/ e:`editorname`

Opcjonalna. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument jest określony, ale nazwa edytora nie został podany, **Otwórz za pomocą** pojawi się okno dialogowe.

/ E:`editorname` argument składni używa nazw edytora, w jakiej występują w Otwórz za pomocą okno dialogowe, ujęta w znaki cudzysłowu.

Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Uwagi

Gdy wprowadzasz ścieżkę, automatyczne uzupełnianie próbuje zlokalizować poprawną ścieżkę i nazwę pliku.

## <a name="example"></a>Przykład

W tym przykładzie otwiera plik styl "Test1.css" w edytorze kodu źródłowego.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Zobacz także

- [Polecenia programu Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Okno bezpośrednie](../../ide/reference/immediate-window.md)
- [Znajdź/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)