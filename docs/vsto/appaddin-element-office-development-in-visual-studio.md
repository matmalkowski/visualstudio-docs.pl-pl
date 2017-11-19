---
title: '&lt;appAddin&gt; elementu (Office Development w Visual Studio) | Dokumentacja firmy Microsoft'
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <appAddin> element
ms.assetid: 6152fe5b-6af1-465d-aee7-19e4fd4d04c1
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c5637a449ea40f6e4f910e061c7e2e324c91ae70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; elementu (Office Development w Visual Studio)
  `appAddin` Elementu `vstov4` przestrzeni nazw są przechowywane informacje dotyczące dostosowywania dotyczące dodatków narzędzi VSTO.  
  
## <a name="syntax"></a>Składnia  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `appAddin` Element jest wymagany i znajduje się w `vstov4` przestrzeni nazw. Istnieje tylko jeden `appAddin` zdefiniowany w manifeście aplikacji element.  
  
 `appAddin` Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`application`|Wymagany. Identyfikuje aplikację Microsoft Office. Wartość może być jedną z następujących: Excel, InfoPath, Outlook, PowerPoint, projektu, Visio lub programu Word.|  
|`loadBehavior`|Opcjonalny. Domyślnie `loadBehavior` jest włączane przez ustawienie wartości. Dla celów debugowania dodatku VSTO można wyłączyć za pomocą ustawienia wartości do dwóch. Aby uzyskać więcej informacji, zobacz tabelę wartości LoadBehavior w tytule [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
|`keyName`|Wymagany. Ta wartość jest nazwę klucza rejestru, który będzie używany przez aplikację do ładowania dodatku VSTO. Aby uzyskać więcej informacji, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 `appAddin` Element ma następujące elementy podrzędne.  
  
### <a name="friendlyname"></a>friendlyName  
 Opcjonalny. `friendlyName` Element znajduje się w [&#60; friendlyName &#62; Element &#40; programowanie Office w Visual Studio &#41; ](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>opis  
 Opcjonalny. `description` Element znajduje się w [&#60; opis &#62; Element &#40; programowanie Office w Visual Studio &#41; ](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formregions —  
 Wymagany tylko dla dodatków VSTO programu Outlook, które obejmują regionów formularzy. `formRegions` Element znajduje się w [&#60; formregions — &#62; Element &#40; programowanie Office w Visual Studio &#41; ](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje `appAddin` elementów rozwiązania programu Outlook wdrażane za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```  
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
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  