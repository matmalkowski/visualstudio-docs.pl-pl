---
title: -Setup (devenv.exe) | Dokumentacja firmy Microsoft
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
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75b7fb7d812135014a8b868ef7590c99e83c15b5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684619"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [-Instalatora (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/setup-devenv-exe).  
  
  
Wymusza [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] do scalenia metadanych zasobów, które opisują, menu, paski narzędzi i grup poleceń, ze wszystkich dostępnych pakietów VSPackage.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten przełącznik nie przyjmuje żadnych argumentów. `devenv /setup` Polecenia jest zazwyczaj podawana jako ostatni krok w procesie instalacji programu. Korzystanie z `/setup` przełącznika nie można uruchomić [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Należy uruchomić `devenv` jako administrator, aby można było używać [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) i [/installvstemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) przełączników.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono ostatni krok w instalacji wersji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zawierającej pakietów VSPackage.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)



