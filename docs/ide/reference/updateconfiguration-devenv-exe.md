---
title: -Updateconfiguration (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93efd5d0e0eb391a164f4997b7ddeedab09b4201
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="updateconfiguration-devenvexe"></a>/ Updateconfiguration (devenv.exe)
Powiadamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do scalenia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pakietów w systemie i wyboru MEF pamięci podręcznej zostały wprowadzone zmiany.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Jeśli pakiet VSIX jest instalowany automatycznie uruchamia to polecenie. Należy uruchomić `devenv.exe /updateconfiguration` po stosowanie poprawek do plików, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aktualizuje pamięć podręczna MEF. Dzięki temu można ocenić, czy Twoje poprawka jest odpowiedni.  
  
## <a name="example"></a>Przykład  
 Następujące przyczyny wiersza polecenia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do scalenia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pakietów w systemie i wyboru MEF pamięci podręcznej zostały wprowadzone zmiany.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)