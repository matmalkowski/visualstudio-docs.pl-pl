---
title: 'Porady: Dodawanie właściwości do typu elementu projektu SharePoint niestandardowego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8a74fbffd5a1d8e9c5e660961d93f7181e51827a
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757009"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Porady: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint
  Podczas definiowania niestandardowego typu elementu projektu SharePoint można dodać właściwości do elementu projektu. Pojawi się ona w **właściwości** okna po wybraniu elementu projektu w **Eksploratora rozwiązań**.  
  
 W następujących krokach założono mają własne typu elementu projektu SharePoint już zdefiniowany. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Aby dodać właściwość do definicji typu elementu projektu  
  
1.  Definiowanie klasy, z publicznej właściwości, która reprezentuje właściwość dodawanego do typu elementu niestandardowego projektu. Jeśli chcesz dodać wiele właściwości do typu elementu niestandardowego projektu, można zdefiniować wszystkie właściwości w tej samej lub różnych klas.  
  
2.  W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementacji, dojście <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenie *projectItemTypeDefinition* parametru.  
  
3.  W obsłudze zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzeń, dodać wystąpienia klasy właściwości niestandardowe, aby <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> kolekcji parametr argumentów zdarzenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób dodawania właściwości o nazwie **przykład właściwości** do niestandardowego elementu typu projektu.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]  
  
### <a name="understand-the-code"></a>Kodu  
 Aby upewnić się, że to samo wystąpienie elementu `CustomProperties` klasa jest używana zawsze <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenie, przykładowy kod jest zapisywany właściwości obiektu do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości czasu pierwszego elementu projektu, to zdarzenie występuje. Kod pobiera tego obiektu, gdy to zdarzenie wystąpi ponownie. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość do zapisania danych z elementów projektu, zobacz [rozszerzeń narzędzi kojarzenie danych niestandardowych z programem SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Aby utrwalić zmiany wartości właściwości **ustawić** dostępu dla `ExampleProperty` zapisuje nową wartość do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiektu skojarzonego z właściwości. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości do utrwalenia danych z elementów projektu, zobacz [zapisywać danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Określ zachowanie właściwości niestandardowe  
 Można określić, jak właściwości niestandardowej pojawia się i zachowuje się tak **właściwości** okna przez zastosowanie atrybutów z <xref:System.ComponentModel> przestrzeni nazw do definicji property. Następujące atrybuty są przydatne w wielu scenariuszach:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Określa nazwę właściwości, która jest wyświetlana w **właściwości** okna.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Określa ciąg opisu, który pojawia się w dolnej części **właściwości** okna, jeśli właściwość jest zaznaczone.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Określa wartość domyślną właściwości.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Określa niestandardowy konwersji między ciąg, który jest wyświetlany w **właściwości** okno i wartość właściwości innych niż ciąg.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Określa niestandardowego edytora do zmodyfikowania właściwości.  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 Te przykłady kodu wymagają projektu biblioteki klas z odwołaniami do zestawów następujące:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>Wdrażanie elementu projektu  
 Aby włączyć inne deweloperom używanie tego elementu projektu, utworzyć szablon projektu lub szablonu elementu projektu. Aby uzyskać więcej informacji, zobacz [elementu Tworzenie szablonów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Aby wdrożyć elementu projektu, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu, szablon i inne pliki, które chcesz dystrybuować z elementem projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Porady: Dodawanie pozycji menu skrótów do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  
