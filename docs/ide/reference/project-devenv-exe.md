---
title: -Projekt (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2f9eef5ba7973f2735be575b6282fac0afc201c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
Identyfikuje jeden projekt w określona konfiguracja rozwiązania do kompilacji, czyszczenia, odbudować lub wdrożenia.

## <a name="syntax"></a>Składnia

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumenty
 / Build

 Tworzy projekt określony przez `/project` `ProjName`.

 / clean

 Czyści wszystkie pośredniczące pliki i katalogi dane wyjściowe tworzone podczas kompilacji.

 / REBUILD

 Czyści, a następnie tworzy projekt określony przez `/project` `ProjName`.

 / deploy

 Określa, czy po Tworzenie lub odbudowywanie można wdrożyć projektu.

 `SolnConfigName`

 Wymagana. Nazwa konfiguracji rozwiązania, które zostaną zastosowane do rozwiązania o nazwie w `SolutionName`.

 `SolutionName`

 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

 / Project `ProjName`

 Opcjonalna. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu do pliku projektu lub nazwa wyświetlana projektu lub pełną ścieżkę i nazwę pliku projektu.

 / projectconfig `ProjConfigName`

 Opcjonalna. Nazwa projektu konfiguracja ma zostać zastosowany do kompilacji `/project` o nazwie.

## <a name="remarks"></a>Uwagi

-   Należy użyć częścią `devenv /build`, /`clean`, `/rebuild`, lub `/deploy` polecenia.

-   Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

-   Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okna, lub określić za pomocą pliku dziennika `/out` przełącznika.

## <a name="example"></a>Przykład
 W tym przykładzie kompilacji projektu `CSharpConsoleApp`za pomocą `Debug` konfigurację kompilacji projektu w `Debug` Konfiguracja rozwiązania o `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/ Kompilacji (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Wdróż (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)