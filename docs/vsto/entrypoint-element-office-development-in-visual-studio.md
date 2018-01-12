---
title: "&lt;punkt wejścia&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2416a50707d36295a6ddb1c2388f6ee9ef37b113
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;punkt wejścia&gt; elementu (Office Development w Visual Studio)
  Każdy `entryPoint` elementu `vstav3` przestrzeni nazw identyfikuje zestawu dostosowania, który powinien być uruchomiony, jeśli to [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] aplikacja jest zainstalowana.  
  
## <a name="syntax"></a>Składnia  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `entryPoint` Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw.  
  
 Każdy `entryPoint` element może zawierać tylko jeden zestaw dostosowania. Może istnieć wiele `entryPoint` elementy zdefiniowane w manifeście aplikacji.  
  
 `entryPoint` Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`class`|Wymagany. Identyfikuje zestawem dostosowania do wykonania. Składnia dla tego atrybutu jest *NamespaceName.ClassName*.|  
  
 `entryPoint`ma następujący element.  
  
### <a name="assemblyidentity"></a>element assemblyIdentity  
 Wymagany. `assemblyIdentity` Element `vstav3` przestrzeni nazw, który odwołuje się do istniejącego `assemblyIdentity` element [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] manifest aplikacji.  
  
 Rola `assemblyIdentity` i jego atrybuty jest zdefiniowany w [&#60; assemblyIdentity &#62; Element &#40; &#41; aplikacji ClickOnce ](/visualstudio/deployment/assemblyidentity-element-clickonce-application).  
  
## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `entryPoint` elementów w aplikacji manifestu dla rozwiązania do pakietu Office poziomie dokumentu wdrażane za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.ThisWorkbook">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet1">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet2">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet3">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `entryPoint` elementu w manifeście aplikacji dla rozwiązań pakietu Office poziomie aplikacji wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstav3:entryPoint   
  class="ContosoOutlookAddIn.ThisAddIn">  
  <assemblyIdentity   
    name="ContosoOutlookAddIn"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  