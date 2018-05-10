---
title: Dodaj istniejący element — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4647fd5ca2cc5199c1f9b85e5237dd57d95dbbd
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="add-existing-item-command"></a>Dodaj istniejący element — Polecenie
Dodaje istniejący plik do bieżącego rozwiązania, a następnie go otwiera.

## <a name="syntax"></a>Składnia

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename` Wymagane. Pełna ścieżka i nazwa pliku, z rozszerzeniem element do dodania do bieżącego rozwiązania. Jeśli ścieżka pliku lub nazwa pliku zawiera spacje, ujmij całą ścieżkę w cudzysłów.

## <a name="switches"></a>Przełączniki
 / e: `editorname` opcjonalne. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument zostanie określony, ale zostanie podana żadna nazwa edytora, **Otwórz za pomocą** zostanie wyświetlone okno dialogowe.

 / E:`editorname` składnię argumentu korzysta z nazw Edytor znajdujące się w **Otwieranie z okna dialogowego**, ujęty w cudzysłów. Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Uwagi
 Autocompletion próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas pisania.

## <a name="example"></a>Przykład
 W tym przykładzie dodaje plik Form1.frm, do bieżącego rozwiązania.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)