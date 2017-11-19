---
title: "Odwołanie do schematu elementu projektu SharePoint | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
ms.assetid: 12b63cbc-bf94-4175-bfa8-2117943d00d1
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67f9d29ff18f4ec12653838d25dc3951a53757bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sharepoint-project-item-schema-reference"></a>Element projektu SharePoint — Odwołanie do schematu
  Visual Studio będzie korzystać schematu elementu projektu SharePoint do sprawdzania poprawności zawartości .spdata — pliki. Plik .spdata — określa zawartości i zachowanie elementu projektu SharePoint. Aby uzyskać więcej informacji o zawartości programu SharePoint — elementy projektu, zobacz [Tworzenie szablonów elementów i szablonów projektu dla SharePoint — elementy projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Schemat elementu projektu SharePoint o nazwie ProjectItemModelSchema.xsd i jest instalowany domyślnie w lokalizacji % Program Files (11.0\Xml\Schemas x86)%\Microsoft programu Visual Studio.  
  
 Element główny jest [ProjectItem](../sharepoint/projectitem-element.md) elementu. W poniższej tabeli opisano wszystkie elementy z definicją w schemacie.  
  
|Element|Opis|  
|-------------|-----------------|  
|[Extensiondata —](../sharepoint/extensiondata-element.md)|Reprezentuje kolekcję elementów danych niestandardowych, które są skojarzone z elementem projektu programu SharePoint.|  
|[Extensiondataitem —](../sharepoint/extensiondataitem-element.md)|Reprezentuje element danych niestandardowych, który jest skojarzony z elementem projektu programu SharePoint, w formacie klucza i wartości. Klucz i wartość muszą być ciągami.|  
|[Featureproperties —](../sharepoint/featureproperties-element.md)|Reprezentuje kolekcję wartości właściwości, które są dołączone do funkcji po wdrożeniu programu SharePoint. Po wdrożeniu funkcji można uzyskać dostępu do wartości właściwości, w kodzie.|  
|[FeatureProperty —](../sharepoint/featureproperty-element.md)|Reprezentuje właściwości niestandardowej, która jest zawarta w funkcji po wdrożeniu programu SharePoint. Po wdrożeniu funkcji można uzyskać dostępu do właściwości, w kodzie.|  
|[Pliki](../sharepoint/files-element.md)|Określa pliki do wdrożenia z elementu projektu SharePoint, takich jak plik element funkcji lub wyjście projektu.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint.|  
|[Projectitemfile —](../sharepoint/projectitemfile-element.md)|Reprezentuje plik programu SharePoint, takich jak plik element funkcji, aby dołączyć z elementem projektu po wdrożeniu programu SharePoint.|  
|[Projectitemfolder —](../sharepoint/projectitemfolder-element.md)|Reprezentuje zamapowany folder.|  
|[Projectoutputfile —](../sharepoint/projectoutputfile-element.md)|Reprezentuje dane wyjściowe projektu do dołączenia do elementu projektu po wdrożeniu programu SharePoint.|  
|[SafeControl —](../sharepoint/safecontrol-element.md)|Reprezentuje kontrolki ASPX lub składnik Web Part jest oznaczony jako bezpieczny dla każdego użytkownika uzyskiwać dostęp do dowolnej strony ASPX w witrynie programu SharePoint.|  
|[SafeControls —](../sharepoint/safecontrols-element.md)|Reprezentuje kolekcję ASPX kontrolek i składników Web Part, które są wyznaczone jako bezpieczne dla każdego użytkownika uzyskiwać dostęp do dowolnej strony ASPX w witrynie programu SharePoint.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  