---
title: '&lt;formRegion&gt; elementu (Office development w Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2fd8036ea2a437ffc9fb68a523d8f25db964b5f6
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; elementu (Office development w Visual Studio)
  `formRegion` Elementu `vstov4` przestrzeni nazw identyfikuje regionów formularzy programu Microsoft Office Outlook jest skojarzony z dodatku VSTO.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `formRegion` Elementu `vstov4` przestrzeni nazw identyfikuje regionu formularza, który jest skojarzony z dodatku VSTO dla programu Outlook. Jest to wymagane tylko dodatków VSTO programu Outlook, które obejmują regionów formularzy.  
  
 Może istnieć wiele `formRegion` elementy zdefiniowane wewnątrz `formRegions` element pojedynczego dodatku VSTO.  
  
 `formRegion` Element ma następującego atrybutu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Wymagana. Określa nazwę regionu formularza.|  
  
 `formRegion` Element ma następujące elementy podrzędne.  
  
### <a name="messageclass"></a>Klasa_wiadomości  
 `messageClass` Element identyfikuje formularz programu Outlook, który jest skojarzony z regionu formularza.  
  
 `messageClass` Element ma następującego atrybutu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Wymagana. Identyfikuje formularz, który jest skojarzony z regionu formularza.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `formRegion` elementu w manifeście aplikacji dla dodatku VSTO dla programu Outlook wdrażane za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Istnieją trzy klasy komunikat skojarzony z tego obszaru jeden formularz. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
```xml  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  