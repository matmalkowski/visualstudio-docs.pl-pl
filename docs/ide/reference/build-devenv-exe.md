---
title: -Kompilacji (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 90e331ed637edcc81dc99f99c3ec39aa75928f7d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
Buduje rozwiązanie przy użyciu pliku konfiguracji określonego rozwiązania.

## <a name="syntax"></a>Składnia

```
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Argumenty
 `SolutionName` Wymagane. Pełna ścieżka i nazwa pliku rozwiązania.

 `SolnConfigName` Wymagane. Nazwa konfiguracji rozwiązania, który zostanie użyty do budowania rozwiązania o nazwie w `SolutionName`.

 / project `ProjName` opcjonalne. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu do pliku projektu lub nazwa wyświetlana projektu lub pełną ścieżkę i nazwę pliku projektu.

 / projectconfig `ProjConfigName` opcjonalne. Nazwa projektu kompilacji konfiguracji, który będzie używany podczas tworzenia `/project` o nazwie.

## <a name="remarks"></a>Uwagi
 Ta opcja wykonuje taką samą funkcję jak **Kompiluj rozwiązanie** polecenia menu w zintegrowane środowisko programistyczne (IDE).

 Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

 Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okna, lub określić za pomocą pliku dziennika `/out` przełącznika.

 To polecenie tworzy tylko projekty, które uległy zmianie od czasu ostatniej kompilacji. Aby utworzyć wszystkich projektów w rozwiązaniu, użyj [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md).

## <a name="example"></a>Przykład
 W tym przykładzie kompilacji projektu `CSharpConsoleApp`za pomocą `Debug` konfigurację kompilacji projektu w `Debug` Konfiguracja rozwiązania o `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też

- [Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)