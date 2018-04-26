---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 065648588b51ad6c71ae1a10235da4f096470abe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Otwiera określony plik wykonywalny do debugowania.

## <a name="syntax"></a>Składnia

```
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Argumenty
 `ExecutableFile`

 Wymagana. Ścieżka i nazwa pliku .exe.

 Jeśli plik .exe nie znaleziono lub nie istnieje, zostanie wyświetlony bez ostrzeżeń ani błędów i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uruchamia się normalnie.

## <a name="remarks"></a>Uwagi
 Wszelkie ciągi po `ExecutableFile` parametrów są przekazywane do tego pliku jako argumenty.

## <a name="example"></a>Przykład
 Poniższy przykład otwiera plik `MyApplication.exe` do debugowania.

```
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)