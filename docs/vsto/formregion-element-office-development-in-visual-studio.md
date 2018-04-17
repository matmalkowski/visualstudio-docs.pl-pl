---
title: '&lt;formRegion&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: af7dd4f3472692def9f05a937297d54d13c6f0d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; elementu (Office Development w Visual Studio)
  `formRegion` Elementu `vstov4` przestrzeni nazw identyfikuje regionów formularzy programu Microsoft Office Outlook jest skojarzony z dodatku VSTO.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`name`|Wymagany. Określa nazwę regionu formularza.|  
  
 `formRegion` Element ma następujące elementy podrzędne.  
  
### <a name="messageclass"></a>Klasa_wiadomości  
 `messageClass` Element identyfikuje formularz programu Outlook, który jest skojarzony z regionu formularza.  
  
 `messageClass` Element ma następującego atrybutu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Wymagany. Identyfikuje formularz, który jest skojarzony z regionu formularza.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `formRegion` elementu w manifeście aplikacji dla dodatku VSTO dla programu Outlook wdrażane za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Istnieją trzy klasy komunikat skojarzony z tego obszaru jeden formularz. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  