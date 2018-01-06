---
title: "Porady: Dodawanie pozycji Menu skrótów do projektów SharePoint | Dokumentacja firmy Microsoft"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9427d2307a9d9726c2df1032410168c3b5cf1cc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Porady: dodawanie elementu menu skrótów do projektów SharePoint
  Można dodać pozycji menu skrótów do żadnego projektu programu SharePoint. Element menu jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**.  
  
 W następujących krokach założono, że utworzono już rozszerzenia projektu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Aby dodać element menu skrótów do projektów SharePoint  
  
1.  W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metody z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementacji, dojście <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> zdarzenie *projectService* parametru.  
  
2.  W sieci programu obsługi zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> zdarzeń, Dodaj nową <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> do obiektu <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> lub <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> kolekcji parametr argumentów zdarzenia.  
  
3.  W <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> programu obsługi zdarzeń dla nowego <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiektów, wykonywanie zadań będzie wykonywany po kliknięciu elementu menu skrótów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób dodawania pozycji menu skrótów w węzłach projektu SharePoint **Eksploratora rozwiązań**. Gdy użytkownik kliknie prawym przyciskiem myszy węzeł projektu i klika pozycję **zapisać komunikatu w oknie danych wyjściowych** element menu, Visual Studio wyświetla komunikat w **dane wyjściowe** okna. W tym przykładzie Usługa projektu SharePoint są używane do wyświetlania komunikatu. Aby uzyskać więcej informacji, zobacz [przy użyciu usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga projektu biblioteki klas z odwołaniami do zestawów następujące:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie projektów SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Porady: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Instrukcje: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  