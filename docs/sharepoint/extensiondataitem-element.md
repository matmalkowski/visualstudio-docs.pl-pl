---
title: "Extensiondataitem — Element | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 65911101f7484b5e97d63df713c3e580c6964fe7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem — Element
  Reprezentuje element danych niestandardowych, który jest skojarzony z elementem projektu programu SharePoint, w formacie klucza i wartości. Klucz i wartość muszą być ciągami.  
  
## <a name="syntax"></a>Składnia  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Key**|Wymagane **xs:string** atrybutu.<br /><br /> Klucz, który jest używany do przechowywania i pobierania elementu danych.|  
|**Wartość**|Wymagane **xs:string** atrybutu.<br /><br /> Wartość elementu danych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Extensiondata —](../sharepoint/extensiondata-element.md)|Reprezentuje kolekcję elementów danych niestandardowych, które są skojarzone z elementem projektu programu SharePoint.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy Skojarz dane niestandardowe z elementu projektu SharePoint za pomocą <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiektu Visual Studio zapisuje dane na nowe **extensiondataitem —** elementu w pliku .spdata — dla elementu projektu. Aby uzyskać więcej informacji, zobacz [zapisywania danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Informacje o elementach  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nazwa schematu**|Schemat elementu projektu SharePoint|  
|**Sprawdzanie poprawności pliku**|ProjectItemModelSchema.xsd|  
|**Może być pusta.**|Nie|  
  
## <a name="see-also"></a>Zobacz też  
 [Element projektu SharePoint — dokumentacja schematu](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  