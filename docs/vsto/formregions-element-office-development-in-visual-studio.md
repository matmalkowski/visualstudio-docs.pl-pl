---
title: '&lt;formregions —&gt; — element (Office development w Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 36741e5e3bcd39dbb6e4ea0746e1877acc581e70
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formregions —&gt; — element (Office development w Visual Studio)
  `formRegions` Elementu `vstov4` przestrzeń nazw zawiera regionów formularzy programu Microsoft Office Outlook, które są skojarzone z dodatku VSTO.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `formRegions` Elementu `vstov4` przestrzeń nazw zawiera wszystkie `formRegion` elementy dodatku VSTO dla programu Outlook. Jest to wymagane tylko dodatków VSTO programu Outlook, które obejmują regionów formularzy.  
  
 Może istnieć tylko jedna `formRegions` zdefiniowany w manifeście aplikacji element.  
  
 `formRegions` Element nie ma żadnych atrybutów.  
  
 `formRegions` Element ma następujący element.  
  
### <a name="formregion"></a>formRegion  
 Wymagana dla dodatków VSTO programu Outlook, które obejmują regionów formularzy. `formRegion` w jest zdefiniowany element [ &#60;formRegion&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `formRegions` elementu w manifeście aplikacji dla rozwiązań pakietu Office poziomie aplikacji wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```xml  
<vstov4:formRegions>  
  <vstov4:formRegion  
      name="OutlookAddIn1.FormRegion1">  
    <vstov4:messageClass name="IPM.Note" />  
    <vstov4:messageClass name="IPM.Contact" />  
    <vstov4:messageClass name="IPM.Appointment" />  
  </vstov4:formRegion>  
</vstov4:formRegions>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  