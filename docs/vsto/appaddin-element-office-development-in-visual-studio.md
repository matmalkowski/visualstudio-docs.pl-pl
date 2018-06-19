---
title: '&lt;appAddin&gt; elementu (Office development w Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0defe437e0778ee9d3c134148a3ca7e4b4cd2ef9
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264665"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; elementu (Office development w Visual Studio)
  **AppAddin** elementu `vstov4` przestrzeni nazw są przechowywane informacje dotyczące dostosowywania dotyczące dodatków narzędzi VSTO.  
  
## <a name="syntax"></a>Składnia  
  
```xml 
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
 **AppAddin** element jest wymagany i znajduje się w `vstov4` przestrzeni nazw. Istnieje tylko jeden **appAddin** zdefiniowany w manifeście aplikacji element.  
  
 **AppAddin** element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Aplikacji**|Wymagana. Identyfikuje aplikację Microsoft Office. Wartość może być jedną z następujących: Excel, InfoPath, Outlook, PowerPoint, projektu, Visio lub programu Word.|  
|**LoadBehavior**|Opcjonalna. Domyślnie **loadBehavior** jest włączane przez ustawienie wartości. Dla celów debugowania dodatku VSTO można wyłączyć za pomocą ustawienia wartości do dwóch. Aby uzyskać więcej informacji, zobacz tabelę wartości LoadBehavior w tytule [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
|**Nazwa klucza**|Wymagana. Ta wartość jest nazwę klucza rejestru, który będzie używany przez aplikację do ładowania dodatku VSTO. Aby uzyskać więcej informacji, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 **AppAddin** element ma następujące elementy podrzędne.  
  
### <a name="friendlyname"></a>friendlyName  
 Opcjonalna. **FriendlyName** element znajduje się w [ &#60;friendlyName&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>opis  
 Opcjonalna. **Opis** element znajduje się w [ &#60;opis&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formregions —  
 Wymagany tylko dla dodatków VSTO programu Outlook, które obejmują regionów formularzy. **Formregions —** element znajduje się w [ &#60;formregions —&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje **appAddin** elementów rozwiązania programu Outlook wdrażane za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Kod  
  
```xml  
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
  
## <a name="see-also"></a>Zobacz także  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  