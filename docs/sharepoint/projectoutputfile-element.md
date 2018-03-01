---
title: "Projectoutputfile — Element | Dokumentacja firmy Microsoft"
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
- ProjectOutputFile element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 5b57f00960629d65f264f22532a16202d6ae5d7a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile — Element
  Reprezentuje dane wyjściowe oddzielny projekt zawierający element projektu po wdrożeniu programu SharePoint.  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>Typ  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Identyfikator projektu**|Wymagane **xs:string** atrybutu.<br /><br /> Identyfikator GUID projektu zależnych, który zawiera dane wyjściowe, które chcesz dołączyć. Odpowiada to **ProjectGuid** elementu w pliku projektu zależnych.|  
|**ProjectPath**|Wymagane **xs:string** atrybutu.<br /><br /> Ścieżka względna, łącznie z nazwą pliku projektu, zależnych projektu, którego dane wyjściowe, które chcesz dołączyć. Ta ścieżka jest określana względem folderze głównym projektu programu SharePoint, który zawiera element projektu programu SharePoint.|  
|**Docelowy**|Opcjonalne **xs:string** atrybutu.<br /><br /> Ścieżka, gdzie ma zostać wdrożona na serwerze programu SharePoint odnoszącego się do folderu głównego wdrożenia wyjście projektu zależnych. Folder główny wdrożenia jest określana przez typ wdrożenia, określony przez **typu** atrybutu.<br /><br /> Aby uzyskać więcej informacji, zobacz opisy **Deployment ścieżkę** i **główny wdrożenia** właściwości programu SharePoint projektu elementów w [opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Typ**|Wymagane **xs:string** atrybutu.<br /><br /> Typ wdrożenia do użycia dla danych wyjściowych projektu zależnych. Aby uzyskać więcej informacji na temat możliwych wartości, zobacz opis **typu wdrożenia** właściwości SharePoint — elementy projektu w [opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Pliki](../sharepoint/files-element.md)|Określa pliki do dołączenia do elementu projektu SharePoint po wdrożeniu programu SharePoint.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj **projectoutputfile —** element, aby dołączyć dane wyjściowe projektu wdrażania elementu projektu SharePoint. Możesz określić inny projekt lub tego samego projektu, który zawiera element projektu. Aby uzyskać więcej informacji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informacje o elementach  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nazwa schematu**|Schemat elementu projektu SharePoint|  
|**Sprawdzanie poprawności pliku**|ProjectItemModelSchema.xsd|  
|**Może być pusta.**|Nie|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Opakowanie i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  