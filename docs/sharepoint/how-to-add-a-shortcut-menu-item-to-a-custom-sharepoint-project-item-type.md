---
title: 'Porady: Dodawanie pozycji Menu skrótów do typu elementu projektu SharePoint niestandardowego | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 580839936cfa42b4e76999809cd8917f3eb4f041
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755505"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Porady: Dodawanie pozycji menu skrótów do niestandardowego typu elementu projektu SharePoint
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
  
 W tym przykładzie używane usługa projektu SharePoint można zapisać komunikatu na **dane wyjściowe** okna. Aby uzyskać więcej informacji, zobacz [korzystania z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga projektu biblioteki klas z odwołaniami do zestawów następujące:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>Wdrażanie elementu projektu  
 Aby włączyć inne deweloperom używanie tego elementu projektu, utworzyć szablon projektu lub szablonu elementu projektu. Aby uzyskać więcej informacji, zobacz [elementu Tworzenie szablonów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Aby wdrożyć elementu projektu, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu, szablon i inne pliki, które chcesz dystrybuować z elementem projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Porady: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
 
