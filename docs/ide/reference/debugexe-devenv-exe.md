---
title: -DebugExe (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 00677826cceab6a54c0fb2216ac6c6284a65631f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Otwiera określony plik wykonywalny do debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Argumenty  
 `ExecutableFile`  
 Wymagany. Ścieżka i nazwa pliku .exe.  
  
 Jeśli plik .exe nie znaleziono lub nie istnieje, zostanie wyświetlony bez ostrzeżeń ani błędów i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uruchamia się normalnie.  
  
## <a name="remarks"></a>Uwagi  
 Wszelkie ciągi po `ExecutableFile` parametrów są przekazywane do tego pliku jako argumenty.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład otwiera plik `MyApplication.exe` do debugowania.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)