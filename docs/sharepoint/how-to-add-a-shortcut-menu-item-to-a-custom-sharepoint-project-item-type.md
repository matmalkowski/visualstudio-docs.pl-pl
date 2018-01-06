---
title: "Porady: Dodawanie pozycji Menu skrótów do typu elementu projektu SharePoint niestandardowego | Dokumentacja firmy Microsoft"
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
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6875b03c86580328f2e29f701b77c07d646ffca1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Porady: dodawanie pozycji menu skrótów do niestandardowego typu elementu projektu SharePoint
  Podczas definiowania niestandardowego typu elementu projektu SharePoint można dodać pozycji menu skrótów do elementu projektu. Element menu jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy element projektu w **Eksploratora rozwiązań**.  
  
 W następujących krokach założono mają własne typu elementu projektu SharePoint już zdefiniowany. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Aby dodać element menu skrótów do typu elementu niestandardowego projektu  
  
1.  W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementacji, dojście <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> zdarzenie *projectItemTypeDefinition* parametru.  
  
2.  W sieci programu obsługi zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> zdarzeń, Dodaj nową <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> do obiektu <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> lub <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> kolekcji parametr argumentów zdarzenia.  
  
3.  W <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> programu obsługi zdarzeń dla nowego <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiektów, wykonywać zadania, aby wykonać po wybraniu elementu menu skrótów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób dodawania elementu menu kontekstowego do typu elementu niestandardowego projektu. Gdy użytkownik otwiera menu skrótów dla elementu projektu w **Eksploratora rozwiązań** i wybiera **zapisać komunikatu w oknie danych wyjściowych** element menu, Visual Studio wyświetla komunikat w **danych wyjściowych**  okna.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]  
  
 W tym przykładzie używane usługa projektu SharePoint można zapisać komunikatu na **dane wyjściowe** okna. Aby uzyskać więcej informacji, zobacz [przy użyciu usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga projektu biblioteki klas z odwołaniami do zestawów następujące:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Wdrażanie elementu projektu  
 Aby włączyć inne deweloperom używanie tego elementu projektu, utworzyć szablon projektu lub szablonu elementu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów elementów i szablonów projektu dla SharePoint — elementy projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Aby wdrożyć elementu projektu, należy utworzyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu, szablon i inne pliki, które chcesz dystrybuować z elementem projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Porady: Dodawanie właściwości do typu elementu projektu SharePoint niestandardowych](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  