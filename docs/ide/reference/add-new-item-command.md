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
ms.openlocfilehash: cb238559cd59c03f134e781bc4beaf7ba7cb7893
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="add-new-item-command"></a>Dodaj nowy element — Polecenie
Dodaje nowy element rozwiązania, takie jak htm, CSS, txt lub ramek do obecnego rozwiązania, a następnie go otwiera.

## <a name="syntax"></a>Składnia

```
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename` Opcjonalne. Nazwa i ścieżka pliku element, aby dodać do rozwiązania.

## <a name="switches"></a>Przełączniki
 / t: `templatename` opcjonalne. Określa typ pliku ma zostać utworzony. Jeśli nazwa szablonu nie jest określony, domyślnie jest utworzony plik tekstowy.

 / T:`templatename` składnię argumentu odzwierciedla informacji zamieszczonych w **Dodaj nowy element rozwiązania** okno dialogowe. Należy wprowadzić pełną kategorii oraz typ pliku, oddzielając nazwy kategorii z typem plików przez ukośnik odwrotny (`\`) i otaczającej cały ciąg w cudzysłowie.

 Na przykład, aby utworzyć nowy plik tekstowy, należy wprowadzić następujący kod pod kątem / t:`templatename` argumentu.

```
/t:"General\Style Sheet"
```

 / e: `editorname` opcjonalne. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument zostanie określony, ale zostanie podana żadna nazwa edytora, **Otwórz za pomocą** zostanie wyświetlone okno dialogowe.

 / E:`editorname` składnię argumentu korzysta z nazw Edytor znajdujące się w **Otwieranie z okna dialogowego**, ujęty w cudzysłów.

 Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Przykład
 W tym przykładzie dodaje nowy element rozwiązania MyHTMLpg, do bieżącego rozwiązania.

```
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)