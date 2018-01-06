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
ms.workload: multiple
ms.openlocfilehash: 8f50bfd0fa5b0f9303bc6256078a30da6e1c0575
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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