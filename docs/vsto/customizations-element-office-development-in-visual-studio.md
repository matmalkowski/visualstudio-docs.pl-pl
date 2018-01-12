---
title: '&lt;Dostosowywanie&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft'
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
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8e84fbba0bf70e28e996dab3c5aa081825447864
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;Dostosowywanie&gt; elementu (Office Development w Visual Studio)
  `customizations` Elementu `vstov4` przestrzeń nazw zawiera wszystkie informacje o instalowaniu i ładowanie poszczególnych rozwiązań pakietu Office.  
  
## <a name="syntax-for-document-level-customizations"></a>Składnia Dostosowywanie na poziomie dokumentu  
  
```  
<customizations>  
  <customization  
    id  
    <document  
      solutionId  
    />  
  </customization>  
</customizations>  
```  
  
## <a name="syntax-for-vsto-add-ins"></a>Składnia dla dodatków VSTO  
  
```  
<customizations>  
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
</customizations>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `customizations` Element zawiera szczegółowe informacje na temat każdego z rozwiązań pakietu Office. Ten element musi być w następującej przestrzeni nazw: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Elementy podrzędne zestawu również musi być w tej przestrzeni nazw.  
  
 `customizations` Element nie ma żadnych atrybutów.  
  
 `customizations` Element ma następujący element podrzędny.  
  
### <a name="customization"></a>dostosowanie  
 Wymagany. `customization` Element `vstov4` przestrzeni nazw jest zdefiniowany w [&#60; dostosowania &#62; Element &#40; programowanie Office w Visual Studio &#41; ](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## <a name="example-of-a-document-level-customization"></a>Przykład dostosowania poziomie dokumentu  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `customizations` element do dostosowania poziomie dokumentu.  
  
> [!NOTE]  
>  Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstov4:customizations   
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
  <vstov4:customization>  
    <vstov4:document   
      solutionId="73e" />  
  </vstov4:customization>  
</vstov4:customizations>  
```  
  
## <a name="example-of-an-vsto-add-in"></a>Przykład dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `customizations` elementu dodatku VSTO. Jest to dodatku VSTO dla programu Outlook obejmuje regionów formularzy. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstov4:customizations   
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
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
</vstov4:customizations>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  