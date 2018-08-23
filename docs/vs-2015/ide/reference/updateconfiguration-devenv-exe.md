---
title: -Updateconfiguration (devenv.exe) | Dokumentacja firmy Microsoft
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
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31fd7f52ad2be89a3e6a40a76948aea0d8cc8bfc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678305"
---
# <a name="updateconfiguration-devenvexe"></a>/ Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [- Updateconfiguration (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/updateconfiguration-devenv-exe).  
  
  
Powiadamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] do scalenia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] żadnych zmian w pamięci podręcznej pakietów w systemie i wyboru MEF.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uruchamia to polecenie automatycznie po zainstalowaniu pakietu VSIX. Należy uruchomić `devenv.exe /updateconfiguration` po poprawianie plików tak, aby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aktualizuje pamięć podręczna MEF. Dzięki temu można ocenić, czy rozwiązanie problemu jest odpowiednia.  
  
## <a name="example"></a>Przykład  
 Poniższe przyczyny wiersza polecenia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] do scalenia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] żadnych zmian w pamięci podręcznej pakietów w systemie i wyboru MEF.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie ustawień środowiska deweloperskiego w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)



