---
title: 'Porady: Dodawanie pozycji Menu skrótów do rozszerzenia elementu projektu SharePoint | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 1a3e92d3131fb52342eb2d5ee10abd13a9dd005e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756048"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Porady: Dodawanie pozycji menu skrótów do rozszerzenia elementu projektu SharePoint
  Element menu skrótów można dodać do istniejącego elementu projektu SharePoint przy użyciu rozszerzenia elementu projektu. Element menu jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy element projektu w **Eksploratora rozwiązań**.  
  
 W następujących krokach założono, że utworzono już rozszerzenia elementu projektu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Aby dodać element menu skrótów w rozszerzenia elementu projektu  
  
1.  W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementacji, dojście <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> zdarzenie *projectItemType* parametru.  
  
2.  W sieci programu obsługi zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> zdarzeń, Dodaj nową <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> do obiektu <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> lub <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> kolekcji parametr argumentów zdarzenia.  
  
3.  W <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> programu obsługi zdarzeń dla nowego <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiektów, wykonywanie zadań będzie wykonywany po kliknięciu elementu menu skrótów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób dodawania pozycji menu skrótów do elementu projektu odbiorcy zdarzeń. Po kliknięciu elementu projektu w **Eksploratora rozwiązań** i klika pozycję **zapisać komunikatu w oknie danych wyjściowych** element menu, Visual Studio wyświetla komunikat w **danych wyjściowych**okna.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]  
  
 W tym przykładzie używane usługa projektu SharePoint można zapisać komunikatu na **dane wyjściowe** okna. Aby uzyskać więcej informacji, zobacz [korzystania z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga projektu biblioteki klas z odwołaniami do zestawów następujące:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Porady: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Porady: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Rozszerzanie elementów projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Wskazówki: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
