---
title: -Wdrażanie (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 368680321f8ff8ab908e79e075a5797ba9ecd598
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945119"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
Wdraża rozwiązanie po kompilacji lub ponownej kompilacji. Dotyczy tylko projektów kodu zarządzanego.

## <a name="syntax"></a>Składnia

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>Argumenty
 `SolnConfigName`

 Wymagana. Nazwa konfiguracji rozwiązania, który zostanie użyty do budowania rozwiązania o nazwie w `SolutionName`.

 `SolutionName`

 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

 / Project `ProjName`

 Opcjonalna. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu do pliku projektu lub nazwa wyświetlana projektu lub pełną ścieżkę i nazwę pliku projektu.

 / projectconfig `ProjConfigName`

 Opcjonalna. Nazwa projektu kompilacji konfiguracji, który będzie używany podczas tworzenia `/project` o nazwie.

## <a name="remarks"></a>Uwagi
 Określony projekt musi być projektu wdrożenia. Jeśli określony projekt nie jest projekt wdrożenia, gdy projekt, który został utworzony jest przekazywany do wdrożenia, jego kończy się niepowodzeniem z powodu błędu.

 Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

 Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okna, lub określić za pomocą pliku dziennika `/out` przełącznika.

## <a name="example"></a>Przykład
 W tym przykładzie wdroży projekt `CSharpConsoleApp`za pomocą `Release` konfigurację kompilacji projektu w `Release` Konfiguracja rozwiązania o `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/ Kompilacji (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)