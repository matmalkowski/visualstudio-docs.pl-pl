---
title: -DebugExe (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0882ae58919cafae71bcb056e74533b7ce64a4e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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