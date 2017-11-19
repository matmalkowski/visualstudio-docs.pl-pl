---
title: "Projectitemfile — Element | Dokumentacja firmy Microsoft"
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
helpviewer_keywords: ProjectItemFile element
ms.assetid: 68d44d31-625a-4f02-b998-463ac0ffb2ef
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 023d2f64dc3f05d518add1cd4bf6c3415f435985
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  