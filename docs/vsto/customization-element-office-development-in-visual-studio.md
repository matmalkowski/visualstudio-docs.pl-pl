---
title: '&lt;Dostosowywanie&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: b8e1c2c21fe5cf3a038066a47f50fe4b813b277e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;Dostosowywanie&gt; elementu (Office Development w Visual Studio)
  `customization` Elementu `vstov4` przestrzeni nazw w tym artykule opisano konkretnego rozwiązania pakietu Office. Elementy podrzędne są różne dla Dostosowywanie na poziomie dokumentu i dodatków VSTO.  
  
## <a name="syntax-for-document-level-customizations"></a>Składnia Dostosowywanie na poziomie dokumentu  
  
```  
<customization  
  id  
  <document  
    solutionId  
  />  
</customization>  
```  
  
## <a name="syntax-for-vsto-add-ins"></a>Składnia dla dodatków VSTO  
  
```  
<customization  
  id  
  <appAddin  
    application  
    loadBehavior  
    keyName>  
  <friendlyName></friendlyName>  
  <description></description>  
  <formRegions></formRegions>  
</customization>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `customization` Element zawiera informacje dotyczące dostosowywania. Ten element musi być w następującej przestrzeni nazw: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Istnieje `customization` elementu dla każdego z rozwiązań pakietu Office. Na przykład, jeśli wdrożono trzy rozwiązań pakietu Office w przypadku wdrożenia wielu projektów, istnieją trzy `customization` elementów w manifeście aplikacji.  
  
 Elementy podrzędne zestawu również musi być w tej przestrzeni nazw.  
  
 `customization` Element ma następującego atrybutu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`id`|Wymagany w przypadku wdrażania wielu projektów. `id` Element unikatowo identyfikuje rozwiązania do pakietu Office.|  
  
### <a name="document-level-customizations"></a>Dostosowania na poziomie dokumentów  
 `customization` Element ma następujący element podrzędny.  
  
#### <a name="document"></a>dokument  
 `document` Element `vstov4` przestrzeni nazw jest zdefiniowany w [&#62; &#60; dokumentu Element &#40; programowanie Office w Visual Studio &#41; ](../vsto/document-element-office-development-in-visual-studio.md).  
  
### <a name="vsto-add-ins"></a>Dodatków VSTO  
 `customization` Element ma następujący element podrzędny.  
  
#### <a name="appaddin"></a>appAddin  
 `appAddin` Element `vstov4` przestrzeni nazw jest zdefiniowany w [&#60; appAddin &#62; Element &#40; programowanie Office w Visual Studio &#41; ](../vsto/appaddin-element-office-development-in-visual-studio.md).  
  
## <a name="example-of-a-document-level-customization"></a>Przykład dostosowania poziomie dokumentu  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `customization` element do dostosowania poziomie dokumentu. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstov4:customization>  
  <vstov4:document   
    solutionId="73e" />  
</vstov4:customization>  
```  
  
## <a name="example-of-an-vsto-add-in"></a>Przykład dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `customization` elementu dodatku VSTO. Jest to dodatku VSTO dla programu Outlook obejmuje regionów formularzy. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstov4:customization>  
  <vstov4:appAddIn   
    application="Outlook"   
    loadBehavior="3"   
    keyName="ContosoOutlookAddIn">  
    <vstov4:friendlyName>  
      ContosoOutlookAddIn  
    </vstov4:friendlyName>  
    <vstov4:description>  
      ContosoOutlookAddIn - Outlook VSTO Add-in   
      created with Visual Studio Tools for Office  
    </vstov4:description>  
    <vstov4:formRegions>  
      <vstov4:formRegion  
          name="OutlookAddIn1.FormRegion1">  
        <vstov4:messageClass name="IPM.Note" />  
        <vstov4:messageClass name="IPM.Contact" />  
        <vstov4:messageClass name="IPM.Appointment" />  
      </vstov4:formRegion>  
    </vstov4:formRegions>  
  </vstov4:appAddIn>  
</vstov4:customization>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  