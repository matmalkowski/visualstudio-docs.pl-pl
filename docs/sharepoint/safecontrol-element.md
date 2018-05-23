---
title: SafeControl — Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8cf6d3d168e3d12d74a9773ccfb3312a29046f7
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="safecontrol-element"></a>SafeControl — Element
  Reprezentuje kontrolki ASPX lub składnik Web Part jest oznaczony jako bezpieczny dla każdego użytkownika uzyskiwać dostęp do dowolnej strony ASPX w witrynie programu SharePoint.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Assembly**|Opcjonalne **xs:string** atrybutu.<br /><br /> Nazwa zestawu, w którym jest zdefiniowany formantu ASPX lub części sieci Web. Domyślnie używa tego atrybutu **$SharePoint.Project.AssemblyFullName$** replaceable parametr dla nazwy zestawu. Aby uzyskać więcej informacji, zobacz [parametry wymienne](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Opcjonalne **xs:boolean** atrybutu.<br /><br /> Określa, czy formant ASPX lub składnik Web Part jest bezpieczna opcja dla niezaufanym użytkownikom na dostęp.|  
|**IsSafeAgainstScript**|Opcjonalne **xs:boolean** atrybutu.<br /><br /> Określa, czy niezaufanym użytkownikom umożliwia wyświetlenie i edytowanie właściwości formantu ASPX lub części sieci Web.|  
|**Nazwa**|Opcjonalne **xs:string** atrybutu.<br /><br /> Nazwa tego wpisu kontroli bezpieczne w kolekcji.|  
|**Namespace**|Opcjonalne **xs:string** atrybutu.<br /><br /> Przestrzeń nazw formantu ASPX lub części sieci Web.|  
|**Właściwość TypeName**|Opcjonalne **xs:string** atrybutu.<br /><br /> Nazwa typu formantu ASPX lub części sieci Web.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[SafeControls —](../sharepoint/safecontrols-element.md)|Reprezentuje kolekcję ASPX kontrolek i składników Web Part, które są wyznaczone jako bezpieczne dla każdego użytkownika uzyskiwać dostęp do dowolnej strony ASPX w witrynie programu SharePoint.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat bezpiecznych formantów, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informacje o elementach  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nazwa schematu**|Schemat elementu projektu SharePoint|  
|**Sprawdzanie poprawności pliku**|ProjectItemModelSchema.xsd|  
|**Może być pusta.**|Nie|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  