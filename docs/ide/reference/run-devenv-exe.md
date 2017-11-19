---
title: -Uruchom (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5be97e75ac7dc29a6dd0244293259bcd17591233
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
Kompiluje i uruchamia określony projekt lub rozwiązanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>Argumenty  
 `SolutionName`  
 Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.  
  
 `ProjectName`  
 Wymagany. Pełna ścieżka i nazwa pliku projektu.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluje i uruchamia określony projekt lub rozwiązanie zgodnie z ustawieniami określonymi dla aktywnej konfiguracji rozwiązania. Ten przełącznik uruchamia zintegrowane środowisko programistyczne (IDE) i pozostawia active po projekt lub rozwiązanie zakończy działanie.  
  
-   Należy ująć ciągi zawierające spacje w podwójny cudzysłów.  
  
-   Podsumowanie informacji, w tym błędy, mogą być wyświetlane w **polecenia** okna, lub określić za pomocą pliku dziennika `/out` przełącznika.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest uruchamiany rozwiązania `MySolution` za pomocą konfiguracji aktywnych wdrożeń.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)   
 [/ Kompilacji (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)