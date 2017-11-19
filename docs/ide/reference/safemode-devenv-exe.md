---
title: -Tryb awaryjny (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 72630bd7c16c3830fecddc34a71b7ea1e4cf382c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Uruchamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym, ładowanie tylko domyślnego środowiska i usług.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Uwagi  
 Ten przełącznik zapobiega podczas ładowania wszystkich innych firm VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zostanie uruchomiony, w związku z tym zapewnienia stabilnej wykonywania.  
  
## <a name="description"></a>Opis  
 W następującym przykładzie uruchomiono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym.  
  
## <a name="code"></a>Kod  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)