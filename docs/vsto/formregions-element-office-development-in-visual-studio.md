---
title: '&lt;formRegions&gt; — element (Office development w programie Visual Studio)'
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
ms.openlocfilehash: b978ef47db6b8803b7730aef14173c3eb19b16e8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676217"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions&gt; — element (Office development w programie Visual Studio)
  `formRegions` Elementu `vstov4` przestrzeń nazw zawiera regionów formularzy programu Microsoft Office Outlook, które są skojarzone z dodatku narzędzi VSTO.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `formRegions` Elementu `vstov4` przestrzeń nazw zawiera wszystkie `formRegion` elementów dla dodatku narzędzi VSTO dla programu Outlook. Jest wymagane tylko dla dodatków narzędzi VSTO dla programu Outlook, obejmujących regionów formularza.  
  
 Może istnieć tylko jeden `formRegions` elementu zdefiniowanego w manifeście aplikacji.  
  
 `formRegions` Element nie ma żadnych atrybutów.  
  
 `formRegions` Element ma następujący element.  
  
### <a name="formregion"></a>elementu formRegion  
 Wymagana dla dodatków narzędzi VSTO dla programu Outlook, obejmujących regionów formularza. `formRegion` Element jest zdefiniowany w [ &#60;elementu formRegion&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Przykładu dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie kodu pokazano `formRegions` elementu w manifeście aplikacji dla rozwiązań pakietu Office dodatku poziomu aplikacji wdrożonych za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
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
  
  