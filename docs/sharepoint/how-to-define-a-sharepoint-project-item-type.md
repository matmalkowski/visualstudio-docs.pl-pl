---
title: 'Porady: Definiowanie typu elementu projektu SharePoint | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 4a0470e84b6c85fdb0786cdee27a2d208a594c0d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Porady: definiowanie typu elementu projektu SharePoint
  Definiowanie typu elementu projektu, gdy chcesz utworzyć niestandardowego elementu projektu SharePoint. Aby uzyskać więcej informacji, zobacz [Definiowanie typów elementów projektu SharePoint niestandardowe](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### <a name="to-define-a-project-item-type"></a>Aby zdefiniować typu elementu projektu  
  
1.  Tworzenie projektu biblioteki klas.  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu.  
  
4.  Do klasy, Dodaj następujące atrybuty:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Ten atrybut umożliwia Visual Studio, aby odnaleźć i załadować Twojego <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> typu konstruktora atrybutu.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. W definicji typu elementu projektu ten atrybut określa identyfikator ciągu dla nowego elementu projektu. Zalecane jest użycie formatu *nazwa firmy*. *Nazwa funkcji* można mieć pewność, że wszystkie elementy projektu mają unikatową nazwę.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Ten atrybut Określa ikonę dla tego elementu projektu w **Eksploratora rozwiązań**. Ten atrybut jest opcjonalna. Jeśli nie zastosować do klasy, Visual Studio Wyświetla domyślną ikonę dla elementu projektu. Jeśli ten atrybut zostanie ustawiony, należy przekazać w pełni kwalifikowana nazwa ikony lub mapy bitowej osadzonego w tym zestawem.  
  
5.  W implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody, użyj członkami *projectItemTypeDefinition* parametru Definiowanie zachowania typu elementu projektu. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> obiekt, który zapewnia dostęp do zdarzeń zdefiniowanych w <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfejsów. Aby uzyskać dostęp do określonego wystąpienia typu elementu projektu, obsługę <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzenia, takie jak <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób definiowania typu elementu projektu proste. Ten typ elementu projektu zapisuje komunikat do **dane wyjściowe** okna i **listy błędów** okna, gdy użytkownik dodaje tego typu elementu projektu do projektu.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 W tym przykładzie używane usługa projektu SharePoint można zapisać komunikatu na **dane wyjściowe** okna i **listy błędów** okna. Aby uzyskać więcej informacji, zobacz [przy użyciu usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Wdrażanie elementu projektu  
 Aby włączyć inne deweloperom używanie tego elementu projektu, utworzyć szablon projektu lub szablonu elementu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów elementów i szablonów projektu dla SharePoint — elementy projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Aby wdrożyć elementu projektu, należy utworzyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu, szablon i inne pliki, które chcesz dystrybuować z elementem projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie typów elementów projektu SharePoint niestandardowych](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Porady: Dodawanie właściwości do typu elementu projektu SharePoint niestandardowych](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Instrukcje: Dodawanie pozycji menu skrótów do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  