---
title: 'Porady: Tworzenie rozszerzenia elementu projektu SharePoint | Dokumentacja firmy Microsoft'
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
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c8e9faaf0b38623347c2b6e8ff7351f625416e82
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Porady: tworzenie rozszerzenia elementu projektu SharePoint
  Tworzenie rozszerzenia elementu projektu, jeśli chcesz dodać funkcję do elementu projektu SharePoint, która jest już zainstalowana w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [rozszerzanie elementów projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
### <a name="to-create-a-project-item-extension"></a>Aby utworzyć rozszerzenia elementu projektu  
  
1.  Tworzenie projektu biblioteki klas.  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejsu.  
  
4.  Do klasy, Dodaj następujące atrybuty:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Ten atrybut umożliwia Visual Studio, aby odnaleźć i załadować Twojego <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> typu konstruktora atrybutu.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. W rozszerzenia elementu projektu ten atrybut identyfikuje element projektu, który ma zostać rozszerzony. Identyfikator elementu projektu należy przekazać do konstruktora atrybutu. Aby uzyskać listę identyfikatorów elementów projektu, które są dołączone do programu Visual Studio, zobacz [rozszerzanie elementów projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  W implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody, użyj członkami *projectItemType* parametru Definiowanie zachowania Twoje rozszerzenie. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> obiekt, który zapewnia dostęp do zdarzeń zdefiniowanych w <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfejsów. Dostęp do określonego wystąpienia czy rozszerzanie typu elementu projektu, obsługę <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzenia, takie jak <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób tworzenia prostego rozszerzenia dla elementu projektu odbiorcy zdarzeń. Zawsze użytkownik dodaje odbiorcy zdarzeń element projektu do projektu SharePoint, to rozszerzenie zapisuje komunikat do **dane wyjściowe** okna i **listy błędów** okna.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 W tym przykładzie używane usługa projektu SharePoint można zapisać komunikatu na **dane wyjściowe** okna i **listy błędów** okna. Aby uzyskać więcej informacji, zobacz [przy użyciu usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie elementów projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Wskazówki: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  