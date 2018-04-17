---
title: -UseEnv (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5fd76e44b2e503bd7b444e83bb9a64abceeaa561
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Uruchamia program Visual Studio i ładuje zmienne środowiskowe w **katalogi VC ++** okno dialogowe.

> [!NOTE]
> Ten przełącznik jest instalowany z **tworzenia klasycznych aplikacji w języku C++** obciążenia.

## <a name="syntax"></a>Składnia

```shell
Devenv /useenv
```

## <a name="example"></a>Przykład

W poniższym przykładzie uruchamiania programu Visual Studio i ładuje zmienne środowiskowe w **katalogi VC ++** okno dialogowe.

```shell
Devenv.exe /useenv
```

## <a name="see-also"></a>Zobacz także

* [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)