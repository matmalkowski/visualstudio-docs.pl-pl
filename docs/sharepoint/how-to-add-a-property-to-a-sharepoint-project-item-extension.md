---
title: "Porady: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint | Dokumentacja firmy Microsoft"
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b8077a7c00b8eadcea6daa80cb30a181803616d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Porady: dodawanie właściwości do rozszerzenia elementu projektu SharePoint
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
  
### <a name="understanding-the-code"></a>Opis kodu  
 Aby upewnić się, że to samo wystąpienie elementu `CustomProperties` klasa jest używana zawsze <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenie, przykładowy kod dodaje właściwości obiektu do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości czasu pierwszego elementu projektu, to zdarzenie występuje. Kod pobiera tego obiektu, gdy to zdarzenie wystąpi ponownie. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość do skojarzenia danych z elementów projektu, zobacz [kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Aby utrwalić zmiany wartości właściwości **ustawić** dostępu dla `ExampleProperty` zapisuje nową wartość do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiektu skojarzonego z właściwości. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości do utrwalenia danych z elementów projektu, zobacz [zapisywania danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Określanie zachowania właściwości niestandardowych  
 Można określić, jak właściwości niestandardowej pojawia się i zachowuje się tak **właściwości** okna przez zastosowanie atrybutów z <xref:System.ComponentModel> przestrzeni nazw do definicji property. Następujące atrybuty są przydatne w wielu scenariuszach:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Określa nazwę właściwości, która jest wyświetlana w **właściwości** okna.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Określa ciąg opisu, który pojawia się w dolnej części **właściwości** okna, jeśli właściwość jest zaznaczone.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Określa wartość domyślną właściwości.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Określa niestandardowy konwersji między ciąg, który jest wyświetlany w **właściwości** okno i wartość właściwości innych niż ciąg.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Określa niestandardowego edytora do zmodyfikowania właściwości.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poniższe przykłady wymagają projektu biblioteki klas z odwołaniami do zestawów następujące:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Porady: Dodawanie pozycji Menu skrótów do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Rozszerzanie elementów projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Przewodnik: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  