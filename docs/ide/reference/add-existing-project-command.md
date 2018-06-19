---
title: Dodaj istniejący projekt — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c030358eb071613e98d473845708b01235683ded
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704788"
---
# <a name="add-existing-project-command"></a>Dodaj istniejący projekt — Polecenie
Dodaje istniejący projekt do bieżącego rozwiązania.

## <a name="syntax"></a>Składnia

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Argumenty
 `filename` Opcjonalne. Pełna ścieżka i projektu nazwa, z rozszerzeniem projektu do dodania do rozwiązania.

 Jeśli `filename` argument zawiera spacje, musi być ujęta w cudzysłów.

 Jeśli nazwa pliku nie zostanie określony, polecenie będzie Otwórz okno dialogowe pliku, użytkownik może wybrać projekt.

## <a name="remarks"></a>Uwagi
 Automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas pisania.

## <a name="example"></a>Przykład
 W tym przykładzie dodaje [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu, TestProject1, do bieżącego rozwiązania.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)