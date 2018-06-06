---
title: Kompilacja Devenv — przełącznik
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 777347ba36cf3443a509d1d6c8c44c23a86901e0
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764972"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Buduje rozwiązanie przy użyciu pliku konfiguracji określonego rozwiązania.

## <a name="syntax"></a>Składnia

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Argumenty

|||
|-|-|
|*Nazwa rozwiązania*|Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.|
|*SolnConfigName*|Wymagana. Nazwa konfiguracji rozwiązania, który zostanie użyty do budowania rozwiązania o nazwie w *Nazwa rozwiązania*. Jeśli dostępnych jest wiele platform rozwiązanie, należy także określić platformy, na przykład **"Debug\|Win32"**.|
|/ project *nazwa_projektu.nazwa_modułu.nazwa_procedury*|Opcjonalna. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z *Nazwa rozwiązania* folderu do pliku projektu lub nazwa wyświetlana projektu lub pełną ścieżkę i nazwę pliku projektu.|
|/ projectconfig *ProjConfigName*|Opcjonalna. Nazwa projektu kompilacji konfiguracji, który będzie używany podczas kompilowania projektu o nazwie. Jeśli dostępnych jest wiele platform projektu, należy także określić platformy, na przykład **"Debug\|Win32"**.|

## <a name="remarks"></a>Uwagi

- **/Build** przełącznika wykonuje taką samą funkcję jak **Kompiluj rozwiązanie** polecenia menu w zintegrowane środowisko programistyczne (IDE).

- Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

- Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w oknie wiersza polecenia lub pliku dziennika określony za pomocą **/out** przełącznika.

- **/Build** przełącznika tylko kompilacje projektów, które uległy zmianie od czasu ostatniej kompilacji. Aby utworzyć wszystkich projektów w rozwiązaniu, użyj [/rebuild](../../ide/reference/rebuild-devenv-exe.md) zamiast tego.

- Jeśli zostanie wyświetlony komunikat o błędzie informujący o **konfiguracji nieprawidłowy projekt**, upewnij się, że określono platforma rozwiązania lub projektu platformy, na przykład **"Debug\|Win32"**.

## <a name="example"></a>Przykład

Poniższe polecenie tworzy projekt "CSharpConsoleApp", za pomocą konfiguracji kompilacji projektu "Debugowanie" w konfiguracji rozwiązania "Debug" "MySolution".

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz także

- [Projekty i rozwiązania — kompilowanie i czyszczenie](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Wwitches wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)