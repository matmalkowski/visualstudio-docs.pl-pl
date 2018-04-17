---
title: -Kompilacji (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: 1cc01dac34723f2a587e76461d41a60361a72091
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
Buduje rozwiązanie przy użyciu pliku konfiguracji określonego rozwiązania.  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `SolutionName`  
 Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.  
  
 `SolnConfigName`  
 Wymagany. Nazwa konfiguracji rozwiązania, który zostanie użyty do budowania rozwiązania o nazwie w `SolutionName`.  
  
 / Project `ProjName`  
 Opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu do pliku projektu lub nazwa wyświetlana projektu lub pełną ścieżkę i nazwę pliku projektu.  
  
 / projectconfig `ProjConfigName`  
 Opcjonalny. Nazwa projektu kompilacji konfiguracji, który będzie używany podczas tworzenia `/project` o nazwie.  
  
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
 [Kompilowanie oraz Oczyszczanie projektów i rozwiązań w programie Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)