---
title: -Setup (devenv.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e63b69c9d97edf5049dfb6e55b8f9d5010984d4d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
Wymusza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do scalenia metadanych zasobów, które opisują menu, paski narzędzi i polecenia grup, wszystkie dostępne pakiety VSPackage.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten przełącznik nie przyjmuje żadnych argumentów. `devenv /setup` Polecenia jest zazwyczaj podawana jako ostatni etap procesu instalacji. Użycie `/setup` przełącznika nie można uruchomić [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Należy uruchomić `devenv` jako administrator, aby można było używać [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) i [/installvstemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) przełączników.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano ostatni krok w instalacji wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawierającą VSPackages.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)