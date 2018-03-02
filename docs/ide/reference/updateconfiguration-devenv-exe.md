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
ms.workload: multiple
ms.openlocfilehash: 0ec3bfc47829bce2fe5ad836c970cb28f8a1294e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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