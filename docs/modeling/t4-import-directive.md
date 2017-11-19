---
title: "T4 Import — dyrektywa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: e27400d82f751136a3ce8e2e448f04935f2157a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="t4-import-directive"></a>Dyrektywa T4 dotycząca importowania
W blokach kodu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablonu tekstowego T4, `import` dyrektywy służy do odwoływania się do elementów w innej przestrzeni nazw nie oferuje w pełni kwalifikowaną nazwą. Jest to równoważne `using` w języku C# lub `imports` w [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
 Ogólne omówienie pisania szablonów tekstowych T4, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).  
  
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
  
-   Przestrzeń nazw z DSL  
  
## <a name="see-also"></a>Zobacz też  
 [T4 dotycząca Dyrektywa zestawu](../modeling/t4-assembly-directive.md)