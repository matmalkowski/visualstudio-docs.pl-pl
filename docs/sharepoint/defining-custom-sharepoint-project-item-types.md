---
title: Definiowanie typów elementów projektu SharePoint niestandardowego | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d9b752aa8162f52746b4487b863557af6dd37fd9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765583"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definiowanie niestandardowych typów elementów projektu SharePoint
  Zdefiniuj nowy typ elementu projektu SharePoint, gdy chcesz utworzyć nowy rodzaj elementu projektu SharePoint. Na przykład Visual Studio nie ma SharePoint — elementy projektu do dodawania pól lub akcje niestandardowe w witrynie programu SharePoint. Można definiować własnych typów SharePoint — elementy projektu do tworzenia pól, niestandardowe akcje lub inne składniki programu SharePoint.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Zadania dla Definiowanie typów elementów projektu SharePoint
 Aby zdefiniować typu elementu niestandardowego projektu, kompilacji zestawu rozszerzenia programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Po zdefiniowaniu typu elementu niestandardowego projektu do elementu projektu można również dodać następujące funkcje:  
  
-   Dodawanie pozycji menu skrótów do elementu projektu. Element menu jest wyświetlany, gdy Otwórz menu skrótów dla elementu projektu w **Eksploratora rozwiązań** przez kliknięcie prawym przyciskiem myszy element projektu lub wybierając go, a następnie wybierając **Shift** +  **F10** kluczy. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie pozycji Menu skrótów do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Dodawanie właściwości niestandardowych do elementu projektu. Pojawi się ona w **właściwości** okna po wybraniu elementu projektu w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Aby włączyć inne deweloperom używanie tego elementu projektu w programie Visual Studio, Utwórz plik .spdata — a szablon elementu lub szablon projektu, który jest skojarzony z elementem projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów elementów i szablonów projektu dla SharePoint — elementy projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Zrozumienie relacji między typów elementów projektu i wystąpień elementu projektu
 Podczas definiowania typu elementu projektu SharePoint Visual Studio ładuje rozszerzenia, gdy skojarzone typu elementu projektu zostanie dodany do projektu SharePoint. Na przykład, jeśli należy zdefiniować nową **Akcja niestandardowa** typu elementu projektu, Visual Studio ładuje rozszerzenia, gdy użytkownik dodaje **Akcja niestandardowa** elementu projektu do projektu. Visual Studio używa tego samego wystąpienia rozszerzenie dla wszystkich wystąpień typu elementu projektu skojarzona. W poprzednim przykładzie, jeśli użytkownik dodaje drugi **Akcja niestandardowa** elementu projektu do projektu, to samo wystąpienie elementu rozszerzenia służy do dostosowywania drugiego elementu projektu.  
  
 Dostęp do określonego wystąpienia typu elementu projektu, obsługiwać jeden z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzenia *projectItemTypeDefinition* parametru w implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Na przykład, aby ustalić, po dodaniu elementu projektu typu niestandardowego do projektu, obsługę <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> zdarzeń. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>Zobacz także
 [Porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Porady: Dodawanie właściwości do typu elementu projektu SharePoint niestandardowych](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Porady: Dodawanie pozycji Menu skrótów do typu elementu projektu SharePoint niestandardowych](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
