---
title: "Rozszerzanie elementów projektu SharePoint | Dokumentacja firmy Microsoft"
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
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f17e43e2fe98e36939c91b37e72b185cb14d09e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="extending-sharepoint-project-items"></a>Rozszerzanie pozycji projektu SharePoint
  Tworzenie rozszerzenia elementu projektu umożliwia dodawanie funkcji do typu elementu projektu SharePoint, która jest już zainstalowana w programie Visual Studio. Na przykład można utworzyć rozszerzenia wbudowanych **odbiorcy zdarzeń** lub **definicji listy** elementy projektu w programie Visual Studio lub można utworzyć rozszerzenia dla typu elementu niestandardowego projektu. Można również utworzyć rozszerzenie dla wszystkich typów elementów projektu SharePoint.  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>Zadania dla rozszerzanie elementów projektu SharePoint  
 Aby rozszerzyć elementu projektu, kompilacji zestawu rozszerzenia programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejsu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Podczas rozszerzania element projektu do elementu projektu można również dodać następujące funkcje:  
  
-   Dodawanie pozycji menu skrótów do elementu projektu. Element menu jest wyświetlany, gdy Otwórz menu skrótów dla elementu projektu w **Eksploratora rozwiązań**. Otwórz menu skrótów, klikając prawym przyciskiem myszy element projektu lub wybierając go, a następnie wybierając Shift + F10 kluczy. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie pozycji Menu skrótów do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Dodawanie właściwości niestandardowych do elementu projektu. Pojawi się ona w **właściwości** okna po wybraniu elementu projektu w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 Aby uzyskać wskazówki, który demonstruje sposób tworzenia, wdrażania i testowania rozszerzenia elementu projektu, zobacz [wskazówki: rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## <a name="understanding-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Opis relacji między rozszerzenia elementu projektu i wystąpień elementu projektu  
 Podczas tworzenia rozszerzenia elementu projektu programu Visual Studio ładuje rozszerzenia, gdy skojarzony typu elementu projektu zostanie dodany do projektu SharePoint. Na przykład w przypadku utworzenia rozszerzenia **odbiorcy zdarzeń** elementy projektu programu Visual Studio ładuje rozszerzenia, gdy użytkownik dodaje **odbiorcy zdarzeń** elementu projektu do projektu. Visual Studio używa tego samego wystąpienia rozszerzenie dla wszystkich wystąpień typu elementu projektu skojarzona. W poprzednim przykładzie, jeśli użytkownik dodaje drugi **odbiorcy zdarzeń** elementu projektu do projektu, to samo wystąpienie elementu rozszerzenia służy do dostosowywania drugiego elementu projektu.  
  
 Dostęp do określonego wystąpienia typu elementu projektu rozszerzania, obsługiwać jeden z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzenia *projectItemType* parametru w implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody. Na przykład, aby ustalić, po dodaniu tego typu są rozszerzenia elementu projektu do projektu, obsługę <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> zdarzeń. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## <a name="identifiers-for-sharepoint-project-items"></a>Identyfikatory elementów projektu SharePoint  
 Każdy element projektu SharePoint ma odpowiedni identyfikator ciągu. Identyfikator elementu projektu należy sprawdzić, czy należy wykonać następujące zadania:  
  
-   Tworzenie rozszerzenia elementu projektu. W takim przypadku należy podać identyfikator dla elementu projektu, który ma zostać rozszerzony do konstruktora obiektu <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Aby utworzyć rozszerzenia elementu projektu wszystkie typy, należy przekazać  **\***  wartość ciągu.  
  
-   Dodaj element projektu do projektu programowo. W takim przypadku należy podać identyfikator elementu projektu do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> metody.  
  
 W poniższej tabeli wymieniono identyfikatory elementów projektu programu SharePoint, które są dołączone do programu Visual Studio.  
  
|Nazwa elementu projektu|Identyfikator ciągu|  
|-----------------------|-----------------------|  
|Model wykazu danych biznesowych|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Typ zawartości|Microsoft.VisualStudio.SharePoint.ContentType|  
|Odbiorcy zdarzeń|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Pusty Element|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Listy definicji<br /><br /> Definicji listy z typu zawartości|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Wystąpienia listy|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Moduł|Microsoft.VisualStudio.SharePoint.Module|  
|Sekwencyjny przepływ pracy<br /><br /> Przepływ pracy automatu stanów|Microsoft.VisualStudio.SharePoint.Workflow|  
|Definicji witryny|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Wizualny składnik Web Part|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web Part|Microsoft.VisualStudio.SharePoint.WebPart|  
|Formularz skojarzenia przepływu pracy|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Porady: Dodawanie pozycji Menu skrótów do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Porady: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Wskazówki: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  