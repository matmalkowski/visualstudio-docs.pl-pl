---
title: -Odbudować (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e462e64df90a7672efa890897b48726a0e764e6c
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
Czyści a potem kompiluje określona konfiguracja rozwiązania.

## <a name="syntax"></a>Składnia

```cmd
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumenty
 `SolnConfigName`

 Wymagana. Nazwa konfiguracji rozwiązania, która będzie służyć do ponownie skompiluj rozwiązanie o nazwie w `SolutionName`.

 `SolutionName`

 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

 / Project `ProjName`

 Opcjonalna. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu do pliku projektu lub nazwa wyświetlana projektu lub pełną ścieżkę i nazwę pliku projektu.

 / projectconfig `ProjConfigName`

 Opcjonalna. Nazwa projektu kompilacji konfiguracji do użycia podczas odbudowywania `/project` o nazwie.

## <a name="remarks"></a>Uwagi

-   Ta opcja wykonuje taką samą funkcję jak **Kompiluj ponownie rozwiązanie** polecenia menu w zintegrowane środowisko programistyczne (IDE).

-   Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

-   Podsumowanie informacji na temat Czyści i kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okna, lub określić za pomocą pliku dziennika `/out` przełącznika.

## <a name="example"></a>Przykład
 W tym przykładzie Czyści i odtwarza projektu `CSharpWinApp`za pomocą `Debug` konfigurację kompilacji projektu w `Debug` Konfiguracja rozwiązania o `MySolution`.

```cmd
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Kompilacji (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)