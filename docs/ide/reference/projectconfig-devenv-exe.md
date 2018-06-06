---
title: ProjectConfig Devenv — przełącznik
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44f5d4479658b450074ba35f2759a273bb584e0a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764657"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Określa konfigurację kompilacji projektu ma być stosowany podczas kompilacji, czyszczenia, odbudować lub wdrożenia projektu o nazwie w **/project** argumentu.

## <a name="syntax"></a>Składnia

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumenty

|||
|-|-|
|/ Build|Tworzy projekt określony przez **/project** argumentu.|
|/ clean|Czyści wszystkie pośredniczące pliki i katalogi dane wyjściowe tworzone podczas kompilacji.|
|/ REBUILD|Czyści, a następnie tworzy projekt określony przez **/project** argumentu.|
|/ deploy|Określa, czy po Tworzenie lub odbudowywanie można wdrożyć projektu.|
|*SolnConfigName*|Wymagana. Nazwa konfiguracji rozwiązania, które zostaną zastosowane do rozwiązania o nazwie w *Nazwa rozwiązania*. Jeśli dostępnych jest wiele platform rozwiązanie, należy także określić platformy, na przykład **"Debug\|Win32"**.|
|*Nazwa rozwiązania*|Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.|
|/ project *nazwa_projektu.nazwa_modułu.nazwa_procedury*|Opcjonalna. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z *Nazwa rozwiązania* folderu do pliku projektu lub nazwa wyświetlana projektu lub pełną ścieżkę i nazwę pliku projektu.|
|/ projectconfig *ProjConfigName*|Opcjonalna. Nazwa projektu kompilacji konfiguracji ma zostać zastosowany do projektu, określony przez **/project** argumentu. Jeśli dostępnych jest wiele platform rozwiązanie, należy także określić platformy, na przykład **"Debug\|Win32"**.|

## <a name="remarks"></a>Uwagi

**/Projectconfig** przełącznika musi być używany z **/project** przełącznika jako część **/build**, **/ clean**,  **/rebuild**, lub **/ deploy** polecenia.

Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w oknie wiersza polecenia lub pliku dziennika określony za pomocą **/out** przełącznika.

## <a name="example"></a>Przykład

Poniższe polecenie tworzy projekt "CSharpConsoleApp", za pomocą konfiguracji kompilacji projektu "Debugowanie" w konfiguracji rozwiązania "Debug" "MySolution":

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/ Kompilacji (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Wdróż (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)