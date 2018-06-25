---
title: 'Porady: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1af848f432183153707b2debfed563f3a00d4156
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758102"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Porady: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint
  Rozszerzenia elementu projektu umożliwia dodawanie właściwości do dowolnego elementu projektu SharePoint, która jest już zainstalowana w programie Visual Studio. Pojawi się ona w **właściwości** okna po wybraniu elementu projektu w **Eksploratora rozwiązań**.  
  
 W następujących krokach założono, że utworzono już rozszerzenia elementu projektu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-property-to-a-project-item-extension"></a>Aby dodać właściwości do rozszerzenia elementu projektu  
  
1.  Definiowanie klasy, z właściwością publiczny odpowiadający właściwości, które dodajesz do typu elementu projektu. Jeśli chcesz dodać wiele właściwości do typu elementu projektu, można zdefiniować wszystkie właściwości w tej samej lub różnych klas.  
  
2.  W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementacji, dojście <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenie *projectItemType* parametru.  
  
3.  W obsłudze zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzeń, dodać wystąpienia klasy właściwości, aby <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> kolekcji parametr argumentów zdarzenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób dodawania właściwości o nazwie **przykład właściwości** do elementu projektu odbiorcy zdarzeń.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### <a name="understand-the-code"></a>Kodu  
 Aby upewnić się, że to samo wystąpienie elementu `CustomProperties` klasa jest używana zawsze <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenie, przykładowy kod dodaje właściwości obiektu do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości czasu pierwszego elementu projektu, to zdarzenie występuje. Kod pobiera tego obiektu, gdy to zdarzenie wystąpi ponownie. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość do skojarzenia danych z elementów projektu, zobacz [rozszerzeń narzędzi kojarzenie danych niestandardowych z programem SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Aby utrwalić zmiany wartości właściwości **ustawić** dostępu dla `ExampleProperty` zapisuje nową wartość do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiektu skojarzonego z właściwości. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości do utrwalenia danych z elementów projektu, zobacz [zapisywać danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Określ zachowanie właściwości niestandardowe  
 Można określić, jak właściwości niestandardowej pojawia się i zachowuje się tak **właściwości** okna przez zastosowanie atrybutów z <xref:System.ComponentModel> przestrzeni nazw do definicji property. Następujące atrybuty są przydatne w wielu scenariuszach:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Określa nazwę właściwości, która jest wyświetlana w **właściwości** okna.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Określa ciąg opisu, który pojawia się w dolnej części **właściwości** okna, jeśli właściwość jest zaznaczone.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Określa wartość domyślną właściwości.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Określa niestandardowy konwersji między ciąg, który jest wyświetlany w **właściwości** okno i wartość właściwości innych niż ciąg.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Określa niestandardowego edytora do zmodyfikowania właściwości.  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 Poniższe przykłady wymagają projektu biblioteki klas z odwołaniami do zestawów następujące:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Porady: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Porady: Dodawanie pozycji menu skrótów do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Rozszerzanie elementów projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Wskazówki: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  
