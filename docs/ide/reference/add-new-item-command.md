---
title: Dodaj nowy element — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8084cdebf4cba1bf3bb79ac1fbf386837b977d97
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705050"
---
# <a name="add-new-item-command"></a>Dodaj nowy element — Polecenie
Dodaje nowy element rozwiązania, takie jak htm, CSS, txt lub ramek do obecnego rozwiązania, a następnie go otwiera.

## <a name="syntax"></a>Składnia

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename` Opcjonalne. Nazwa i ścieżka pliku element, aby dodać do rozwiązania.

## <a name="switches"></a>Przełączniki
 / t: `templatename` opcjonalne. Określa typ pliku ma zostać utworzony. Jeśli nazwa szablonu nie jest określony, domyślnie jest utworzony plik tekstowy.

 / T:`templatename` składnię argumentu odzwierciedla informacji zamieszczonych w **Dodaj nowy element rozwiązania** okno dialogowe. Należy wprowadzić pełną kategorii oraz typ pliku, oddzielając nazwy kategorii z typem plików przez ukośnik odwrotny (`\`) i otaczającej cały ciąg w cudzysłowie.

 Na przykład, aby utworzyć nowy plik tekstowy, należy wprowadzić następujący kod pod kątem / t:`templatename` argumentu.

```cmd
/t:"General\Style Sheet"
```

 / e: `editorname` opcjonalne. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument zostanie określony, ale zostanie podana żadna nazwa edytora, **Otwórz za pomocą** zostanie wyświetlone okno dialogowe.

 / E:`editorname` składnię argumentu korzysta z nazw Edytor znajdujące się w **Otwieranie z okna dialogowego**, ujęty w cudzysłów.

 Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Przykład
 W tym przykładzie dodaje nowy element rozwiązania MyHTMLpg, do bieżącego rozwiązania.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)