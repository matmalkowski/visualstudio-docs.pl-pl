---
title: T4 Import — dyrektywa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2b0b4332f9c156bc9690ef94f8670e963203b5a9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690050"
---
# <a name="t4-import-directive"></a>Dyrektywa T4 dotycząca importowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [dyrektywa T4 dotycząca importowania](https://docs.microsoft.com/visualstudio/modeling/t4-import-directive).  
  
W blokach kodu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonu tekstowego T4, `import` dyrektywy zezwala na odnoszenie się do elementów w innej przestrzeni nazw bez podawania w pełni kwalifikowaną nazwą. Jest to równoważne z `using` w języku C# lub `imports` w [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
 Aby uzyskać ogólne omówienie pisania szablonów tekstowych T4, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-import-directive"></a>Używanie dyrektywy Import  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 W tym przykładzie kod szablonu może pominąć jawną przestrzeń nazw dla członków System.IO:  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## <a name="standard-imports"></a>Standardowe importowanie  
 Następująca przestrzeń nazw jest importowana automatycznie, aby nie trzeba było pisać dla niej dyrektywy importu:  
  
-   `System`  
  
 Ponadto, jeśli używasz niestandardowej dyrektywy, procesor dyrektywy mógłby automatycznie zaimportować niektóre przestrzenie nazw.  
  
 Na przykład, jeśli piszesz szablony dla języka specyficznego dla domeny (domain-specific language — DSL), nie musisz pisać dyrektyw importu dla następujących przestrzeni nazw:  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   Przestrzeń nazw DSL  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywa T4 dotycząca zestawu](../modeling/t4-assembly-directive.md)



