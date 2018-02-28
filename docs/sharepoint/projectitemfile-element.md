---
title: "Projectitemfile — Element | Dokumentacja firmy Microsoft"
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
- ProjectItemFile element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 7c222c25417f9a33f28871c94d8dd0d9353e1e76
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="projectitemfile-element"></a>ProjectItemFile — Element
  Reprezentuje plik programu SharePoint, takich jak plik element funkcji, aby dołączyć z elementem projektu po wdrożeniu programu SharePoint.  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>Typ  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Źródło**|Wymagane **xs:string** atrybutu.<br /><br /> Nazwa pliku do wdrożenia z elementem projektu.|  
|**Docelowy**|Opcjonalne **xs:string** atrybutu.<br /><br /> Ścieżka, w którym zostanie wdrożony plik w programie SharePoint, odnoszącego się do folderu głównego wdrożenia. Folder główny wdrożenia jest określana przez typ wdrożenia, określony przez **typu** atrybutu. Jeśli **docelowej** atrybut nie jest określony, plik zostanie wdrożony do folderu o podanej nazwie w **źródła** atrybutu.<br /><br /> Aby uzyskać więcej informacji, zobacz opisy **Deployment ścieżkę** i **główny wdrożenia** właściwości programu SharePoint projektu elementów w [opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Typ**|Wymagane **xs:string** atrybutu.<br /><br /> Typ wdrożenia dla pliku. Aby uzyskać więcej informacji na temat możliwych wartości, zobacz opis **typu wdrożenia** właściwości SharePoint — elementy projektu w [opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Pliki](../sharepoint/files-element.md)|Określa pliki do dołączenia do elementu projektu SharePoint po wdrożeniu programu SharePoint.|  
  
## <a name="remarks"></a>Uwagi  
 Pliki programu SharePoint, które są zwykle przywoływany w **projectitemfile —** elementy zawierają pliki elementu funkcji (Elements.xml), pliki schematów listy definicji (Schema.xml) oraz składnik Web Part plików definicji dla części sieci Web (.webpart).  
  
## <a name="element-information"></a>Informacje o elementach  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nazwa schematu**|Schemat elementu projektu SharePoint|  
|**Sprawdzanie poprawności pliku**|ProjectItemModelSchema.xsd|  
|**Może być pusta.**|Nie|  
  
## <a name="see-also"></a>Zobacz też  
 [Element projektu SharePoint — dokumentacja schematu](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  