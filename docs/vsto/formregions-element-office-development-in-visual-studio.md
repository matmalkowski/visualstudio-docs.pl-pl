---
title: "&lt;formregions —&gt; — Element (Office Development w Visual Studio) | Dokumentacja firmy Microsoft"
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
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
ms.assetid: 71faa2da-9d38-43e8-9d7d-0bcd944ef9a3
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 87909c1586f631ba598258faaf0c7cd02967519c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formregions —&gt; — Element (Office Development w Visual Studio)
  `formRegions` Elementu `vstov4` przestrzeń nazw zawiera regionów formularzy programu Microsoft Office Outlook, które są skojarzone z dodatku VSTO.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 Wymagana dla dodatków VSTO programu Outlook, które obejmują regionów formularzy. `formRegion` w jest zdefiniowany element [&#60; formRegion &#62; Element &#40; programowanie Office w Visual Studio &#41; ](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `formRegions` elementu w manifeście aplikacji dla rozwiązań pakietu Office poziomie aplikacji wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
<vstov4:formRegions>  
  <vstov4:formRegion  
      name="OutlookAddIn1.FormRegion1">  
    <vstov4:messageClass name="IPM.Note" />  
    <vstov4:messageClass name="IPM.Contact" />  
    <vstov4:messageClass name="IPM.Appointment" />  
  </vstov4:formRegion>  
</vstov4:formRegions>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  