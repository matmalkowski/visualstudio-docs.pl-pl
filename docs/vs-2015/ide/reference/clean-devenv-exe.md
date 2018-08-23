---
title: -Wyczyść (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 194081570d3b6e99966e960b3cef3163aeb945f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680631"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [-Wyczyść (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/clean-devenv-exe).  
  
  
Czyści wszystkie pośrednie pliki i katalogi wyjściowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## <a name="arguments"></a>Argumenty  
 `FileName`  
 Wymagane. Pełna ścieżka i nazwa pliku rozwiązania lub pliku projektu.  
  
 / Project `ProjName`  
 Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu pliku projektu lub nazwy wyświetlanej projektu, lub pełną ścieżkę i nazwę pliku projektu.  
  
 / projectconfig `ProjConfigName`  
 Opcjonalna. Nazwa projektu kompilacji konfiguracji, który będzie używany podczas czyszczenia `/project` o nazwie.  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja wykonuje taką samą funkcję jak **czyste rozwiązanie** polecenia menu w ramach zintegrowanego środowiska programistycznego (IDE).  
  
 Należy ująć ciągi zawierające spacje w podwójny cudzysłów.  
  
 Podsumowanie informacji na temat Czyści i kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą `/out` przełącznika.  
  
## <a name="example"></a>Przykład  
 Pierwszy przykład czyści `MySolution` rozwiązania przy użyciu domyślnej konfiguracji określone w pliku rozwiązania.  
  
 Drugi przykład czyści projektu `CSharpConsoleApp`przy użyciu `Debug` konfigurację kompilacji projektu w ramach `Debug` Konfiguracja rozwiązania o `MySolution`.  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



