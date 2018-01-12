---
title: "Rozszerzanie projektów SharePoint | Dokumentacja firmy Microsoft"
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 403ff3793dfd5ae4211444868af8c37dbd908672
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="extending-sharepoint-projects"></a>Rozszerzanie projektów SharePoint
  Tworzenie rozszerzenia projektu, jeśli chcesz dostosować funkcje na poziomie projektu projektów programu SharePoint. Na przykład można dodać właściwości niestandardowe projektu lub odpowiadanie na zdarzenia na poziomie projektu, które są wywoływane, gdy użytkownik rozwija rozwiązania SharePoint w Visual Studio.  
  
## <a name="creating-project-extensions"></a>Tworzenie rozszerzenia projektu  
 Aby rozszerzyć elementu projektu, kompilacji zestawu rozszerzenia programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfejsu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Podczas tworzenia rozszerzenia projektu do projektów SharePoint można również dodać następujące funkcje:  
  
-   Dodawanie pozycji menu skrótów. Element menu jest wyświetlany, gdy Otwórz menu skrótów węzła projektu SharePoint w **Eksploratora rozwiązań** prawym przyciskiem myszy węzeł lub wybierając go, a następnie wybierając Shift + F10 kluczy. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie pozycji Menu skrótów do projektów SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Dodawanie właściwości niestandardowych. Pojawi się ona w **właściwości** okna po wybraniu projektu SharePoint w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Aby uzyskać wskazówki, na którym przestawiono tworzenie, wdrażanie i testowanie rozszerzenia projektu, zobacz [wskazówki: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## <a name="understanding-the-relationship-between-project-extensions-and-project-instances"></a>Opis relacji między rozszerzeniami projektu i wystąpień projektu  
 Podczas tworzenia rozszerzenia projektu rozszerzenia ładuje po otwarciu dowolnego rodzaju projektu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]zawiera kilka szablonów projektu programu SharePoint, takie jak definicje list, typy zawartości i odbiorcy zdarzeń. Istnieje jednak tylko jeden typ projektu programu SharePoint. Typy projektów, które są widoczne w **nowy projekt** okno dialogowe są tylko te szablony, które razem pakietu jeden lub więcej elementów projektu SharePoint. Ponieważ istnieje tylko jeden typ projektu programu SharePoint, rozszerzeń utworzonych dla jednego projektu mają zastosowanie do wszystkich projektów programu SharePoint. Na przykład nie można utworzyć rozszerzenia, które dotyczą tylko **typu zawartości** projektu.  
  
 Dostęp do wystąpienia określonego projektu, obsługiwać jeden z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> zdarzenia *projectService* parametru w implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metody. Na przykład, aby określić, gdy projekt programu SharePoint zostanie dodany do rozwiązania, obsługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> zdarzeń. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Porady: Dodawanie pozycji Menu skrótów do projektów SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Porady: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Wskazówki: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Definiowanie typów elementów projektu SharePoint niestandardowych](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Rozszerzanie elementów projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  