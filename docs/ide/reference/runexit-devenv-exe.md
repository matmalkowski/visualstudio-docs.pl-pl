---
title: -Runexit (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fdb1cf075c97290883879537089dcee456351c8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
Kompiluje i uruchamia określony projekt lub rozwiązanie, a następnie zamyka zintegrowane środowisko programistyczne (IDE).  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>Argumenty  
 `SolutionName`  
 Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.  
  
 `ProjectName`  
 Wymagany. Pełna ścieżka i nazwa pliku projektu.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluje i uruchamia określony projekt lub rozwiązanie zgodnie z ustawieniami określonymi dla aktywnej konfiguracji rozwiązania. Ten przełącznik minimalizuje IDE podczas projekt lub rozwiązanie jest uruchamiana i zamyka IDE po projektu lub rozwiązania zakończy działanie.  
  
-   Należy ująć ciągi zawierające spacje w podwójny cudzysłów.  
  
-   Podsumowanie informacji, w tym błędy, mogą być wyświetlane w **polecenia** okna, lub określić za pomocą pliku dziennika `/out` przełącznika.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest uruchamiany rozwiązania `MySolution` w IDE w trybie zminimalizowanym za pomocą konfiguracji aktywnych wdrożeń, a następnie zamyka IDE.  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ Uruchom (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/ Kompilacji (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)