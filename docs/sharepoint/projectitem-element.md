---
title: Projectitem — Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f6d273e0fa980e25c8b8d0c7ea6b1a8eb5d537c9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692044"
---
# <a name="projectitem-element"></a>ProjectItem — Element
  Reprezentuje element projektu programu SharePoint. Ten element wymaganego głównego elementu pliku the.spdata.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"  
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"  
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"  
    SupportedTrustLevels = "Trust levels that the project item supports"  
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"  
    Type="Identifier for the project item">  
  <Files>...</Files>  
  <ProjectItemFolder>...</ProjectItemFolder>  
  <SafeControls>...</SafeControls>  
  <FeatureProperties>...</FeatureProperties>  
  <ExtensionData>...</ExtensionData>  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**DefaultFile**|Opcjonalne **xs: ciąg** atrybutu.<br /><br /> Ścieżka względna, włącznie z nazwą pliku, plik, który zostanie otwarty w edytorze programu Visual Studio podczas otwierania elementu projektu SharePoint w **Eksploratora rozwiązań**. Ścieżka jest względna z folderu, który zawiera `.spdata` pliku.|  
|**FeatureReceiverClass**|Opcjonalne **xs:string** atrybutu.<br /><br /> Pełna nazwa klasy odbiorcy funkcji dla tego elementu projektu SharePoint. Aby uzyskać więcej informacji o funkcji odbiorcy, temacie [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Opcjonalne **xs:string** atrybutu.<br /><br /> Określa w pełni kwalifikowana nazwa zestawu, który definiuje Odbiorca funkcji, dla tego elementu projektu SharePoint. Aby uzyskać więcej informacji o funkcji odbiorcy, temacie [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Aby uzyskać więcej informacji na temat zestawu w pełni kwalifikowanej nazwy, zobacz [nazwy zestawu](/dotnet/framework/app-domains/assembly-names).|  
|**SupportedTrustLevels**|Opcjonalne **xs:string** atrybutu.<br /><br /> Określa poziomy zaufania, które obsługuje ten element projektu programu SharePoint. Ta wartość może być jedną z następujących ciągów: piaskownicy, FullTrust, lub wszystkich. Wartość określa wszystkie Sandboxed i FullTrust.<br /><br /> W niestandardowego typu elementu projektu SharePoint, wartość tego atrybutu odpowiada wartość, która zostanie przypisana do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> właściwości w implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Jeśli określisz innej wartości dla tego atrybutu, Visual Studio zastępuje wartość tak, aby Określa on taki sam poziom zaufania, którą można określić w <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> właściwości.|  
|**SupportedDeploymentScopes**|Opcjonalne **xs:string** atrybutu.<br /><br /> Określa zakresów wdrożenia, które obsługuje ten element projektu programu SharePoint. Ta wartość jest rozdzielana przecinkami ciąg, który składa się z co najmniej jeden z następujących ciągów: farmy, witryny, sieci Web, aplikacji sieci Web lub pakietu. Na przykład: `Web, Site`<br /><br /> W niestandardowego typu elementu projektu SharePoint, wartość tego atrybutu odpowiada wartość, która zostanie przypisana do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> właściwości w implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Jeśli określisz innej wartości dla tego atrybutu, Visual Studio zastępuje wartość tak, aby Określa on taki sam poziom zaufania, którą można określić w <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> właściwości.|  
|**Typ**|Wymagane **xs:string** atrybutu.<br /><br /> Identyfikator elementu projektu SharePoint. W przypadku niestandardowego typu elementu projektu SharePoint, identyfikator jest ciąg, który jest przekazywany do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Listę identyfikatorów dla wbudowanych elementów projektu SharePoint uwzględnionych w programie Visual Studio, zobacz [rozszerzanie elementów projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Extensiondata —](../sharepoint/extensiondata-element.md)|Element opcjonalny.<br /><br /> Reprezentuje kolekcję elementów danych niestandardowych, które są skojarzone z elementem projektu programu SharePoint.<br /><br /> Może zawierać tylko jeden **extensiondata —** elementu.|  
|[Featureproperties —](../sharepoint/featureproperties-element.md)|Element opcjonalny.<br /><br /> Reprezentuje kolekcję wartości właściwości, które są dołączone do funkcji po wdrożeniu programu SharePoint.<br /><br /> Może zawierać tylko jeden **featureproperties —** elementu.|  
|[Pliki](../sharepoint/files-element.md)|Opcjonalne **FileCollectionType** elementu.<br /><br /> Określa pliki do wdrożenia z elementu projektu SharePoint, takich jak funkcja elementu pliki i dane wyjściowe projektów zależnych programu SharePoint.<br /><br /> Zawiera **pliki** lub **projectitemfolder —** elementu, ale nie oba.|  
|[Projectitemfolder —](../sharepoint/projectitemfolder-element.md)|Opcjonalne **ProjectItemFolderType** elementu.<br /><br /> Reprezentuje zamapowany folder.<br /><br /> Zawiera **pliki** lub **projectitemfolder —** elementu, ale nie oba.|  
|[SafeControls —](../sharepoint/safecontrols-element.md)|Element opcjonalny.<br /><br /> Reprezentuje kolekcję ASPX kontrolek i składników Web Part, które są wyznaczone jako bezpieczne dla każdego użytkownika uzyskiwać dostęp do dowolnej strony ASPX w witrynie programu SharePoint.<br /><br /> Może zawierać tylko jeden **SafeControls** elementu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
 Brak.  
  
## <a name="element-information"></a>Informacje o elementach  
  
|||  
|-|-|  
|**Namespace**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nazwa schematu**|Schemat elementu projektu SharePoint|  
|**Sprawdzanie poprawności pliku**|ProjectItemModelSchema.xsd|  
|**Może być pusta.**|Nie|  
  
## <a name="see-also"></a>Zobacz też  
 [Element projektu SharePoint — dokumentacja schematu](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  