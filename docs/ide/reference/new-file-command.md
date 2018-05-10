---
title: Nowy plik — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a519de555f35df4fac91a9960993a0f163c4de5a
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="new-file-command"></a>Nowy plik — Polecenie
Tworzy nowy plik, a następnie go otwiera. Plik pojawi się w folderze dodatkowych plików.

## <a name="syntax"></a>Składnia

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename`

 Opcjonalna. Nazwa pliku. Jeśli nazwa nie zostanie podany, podano nazwę domyślną. Jeśli żadna nazwa szablonu nie jest wyświetlane, jest tworzony plik tekstowy.

## <a name="switches"></a>Przełączniki
 / t:`templatename`

 Opcjonalna. Określa typ pliku ma zostać utworzony.

 / T:`templatename` argumentu składni odzwierciedla informacje znajdujące się w oknie dialogowym Nowy plik. Wprowadź nazwę kategorii, a następnie ukośnik odwrotny (`\`) i szablonu, nazwy i ująć cały ciąg w cudzysłowie.

 Na przykład, aby utworzyć nową [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] pliku źródłowego, należy wpisać następujący kod pod kątem / t:`templatename` argumentu.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

 W powyższym przykładzie oznacza, że szablon pliku C++ znajduje się w kategorii Visual C++ w **nowy plik** okno dialogowe.

 / e:`editorname`

 Opcjonalna. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument zostanie określony, ale zostanie podana żadna nazwa edytora, **Otwórz za pomocą** zostanie wyświetlone okno dialogowe.

 / E:`editorname` argumentu składni korzysta z nazw Edytor znajdujące się w otwartych z okno dialogowe, ujęty w cudzysłów.

 Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Przykład
 W tym przykładzie tworzy nową stronę sieci Web "test1.htm" i otwarcie go w edytorze kodu źródłowego.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Okno bezpośrednie](../../ide/reference/immediate-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)