---
title: -ResetAddin (devenv.exe) | Dokumentacja firmy Microsoft
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
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f306e6952b5cf0d41901b85e554cfc3f444dbb00
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42631812"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [- ResetAddin (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/resetaddin-devenv-exe).  
  
  
Usuwa poleceń i polecenia interfejs użytkownika skojarzony z określonym dodatku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Argumenty  
 `AddIn`  
 Opcjonalna. Nazwa polecenia dodatku.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie nazwa polecenia dodatku jest równa  *\<AddInSolutionName >*. Połącz *.\< AddInSolutionName >* i pojawia się w Connect.cs jako `commandName` parametru `Exec` metody. Nazwę polecenia można również sprawdzić, zaczynając wpisywanie nazwy dodatku w oknie polecenia w programie Visual Studio, a następnie wypełniając pozostałe za pomocą technologii Intellisense.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie uruchamia programu Visual Studio i zapobiega `MyAddin` dodatek podczas uruchamiania systemu.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)



