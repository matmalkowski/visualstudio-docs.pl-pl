---
title: -ResetAddin (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f54e50e62b7f7f8f6dd1610904b66c82da02380
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
Usuwa poleceń i polecenia Interfejsem skojarzonym z określonego dodatku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Argumenty  
 `AddIn`  
 Opcjonalny. Polecenie Nazwa dodatku.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie nazwa polecenia dodatek jest równa  *\<AddInSolutionName >*. Połącz*.\< AddInSolutionName >*, a w Connect.cs jako `commandName` parametr `Exec` metody. Można również sprawdzić nazwa polecenia, wpisz nazwę dodatku do okna poleceń w programie Visual Studio rozpoczyna i używanie Intellisense do wypełniania w pozostałej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie uruchamiania programu Visual Studio i uniemożliwia `MyAddin` dodatku podczas uruchamiania systemu.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)