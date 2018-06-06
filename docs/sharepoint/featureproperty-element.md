---
title: FeatureProperty — Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a937310ddbb866cbe046ea2975f8d76e75fe2a98
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766968"
---
# <a name="featureproperty-element"></a>FeatureProperty — element
  Reprezentuje właściwości niestandardowej, która jest zawarta w funkcji po wdrożeniu programu SharePoint. Po wdrożeniu funkcji można uzyskać dostępu do właściwości, w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Key**|Wymagane **xs:string** atrybutu.<br /><br /> Klucz, który jest używany do przechowywania i pobierania wartości właściwości. Każda właściwość musi mieć klucz, który jest unikatowy w ramach funkcji.|  
|**Wartość**|Wymagane **xs:string** atrybutu.<br /><br /> Wartość właściwości.|  
  
### <a name="child-elements"></a>Elementy podrzędne
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne
  
|Element|Opis|  
|-------------|-----------------|  
|[Featureproperties —](../sharepoint/featureproperties-element.md)|Reprezentuje kolekcję wartości właściwości, które są dołączone do funkcji po wdrożeniu programu SharePoint.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat właściwości funkcji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informacje o elementach
  
|||  
|-|-|  
|**Namespace**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nazwa schematu**|Schemat elementu projektu SharePoint|  
|**Sprawdzanie poprawności pliku**|ProjectItemModelSchema.xsd|  
|**Może być pusta.**|Nie|  
  
## <a name="see-also"></a>Zobacz także
 [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  
