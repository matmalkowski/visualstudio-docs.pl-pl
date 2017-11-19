---
title: -ProjectConfig (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 954d2807e510e43e0931070335dce5f92d5c2464
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
Określa konfigurację kompilacji projektu ma być stosowany podczas kompilacji, czyszczenia, odbudować lub wdrożenia projektu o nazwie w `/project` argumentu.  
  
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
 Wymagany. Nazwa konfiguracji rozwiązania, które zostaną zastosowane do rozwiązania o nazwie w `SolutionName`.  
  
 `SolutionName`  
 Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.  
  
 / Project`ProjName`  
 Opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu do pliku projektu lub nazwa wyświetlana projektu lub pełną ścieżkę i nazwę pliku projektu.  
  
 / projectconfig`ProjConfigName`  
 Opcjonalny. Nazwa projektu konfiguracja ma zostać zastosowany do kompilacji `/project` o nazwie.  
  
## <a name="remarks"></a>Uwagi  
  
-   Musi być używany z `/project` przełącznika jako część `devenv /build`, /`clean`, `/rebuild`, lub `/deploy` polecenia.  
  
-   Należy ująć ciągi zawierające spacje w podwójny cudzysłów.  
  
-   Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okna, lub określić za pomocą pliku dziennika `/out` przełącznika.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie kompilacji projektu `CSharpConsoleApp`za pomocą `Debug` konfigurację kompilacji projektu w `Debug` Konfiguracja rozwiązania o `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)   
 [/ Kompilacji (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/ Wdróż (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)   
 [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)