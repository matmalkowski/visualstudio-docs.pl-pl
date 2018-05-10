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
ms.openlocfilehash: 07dfcbb6064d0f1043c0621534b953a5f5c63e82
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Otwiera określony plik wykonywalny do debugowania.

## <a name="syntax"></a>Składnia

```cmd
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

```cmd
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)