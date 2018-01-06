---
title: -Projekt (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 16cd05607bfd6a3bec2bee143b8f735220a5b643
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
Identyfikuje jeden projekt w określona konfiguracja rozwiązania do kompilacji, czyszczenia, odbudować lub wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
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
 Wymagany. Nazwa konfiguracji rozwiązania, które zostaną zastosowane do rozwiązania o nazwie w `SolutionName`.  
  
 `SolutionName`  
 Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.  
  
 / Project`ProjName`  
 Opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu do pliku projektu lub nazwa wyświetlana projektu lub pełną ścieżkę i nazwę pliku projektu.  
  
 / projectconfig`ProjConfigName`  
 Opcjonalny. Nazwa projektu konfiguracja ma zostać zastosowany do kompilacji `/project` o nazwie.  
  
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
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)   
 [/ Kompilacji (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/ Wdróż (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)   
 [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)