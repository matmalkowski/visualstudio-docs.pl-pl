---
title: Dyrektywa T4 dotycząca importowania
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4017ffc67558f6056cb01bf62c5adf9e7569ad4d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946913"
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

- [Dyrektywa T4 dotycząca zestawu](../modeling/t4-assembly-directive.md)