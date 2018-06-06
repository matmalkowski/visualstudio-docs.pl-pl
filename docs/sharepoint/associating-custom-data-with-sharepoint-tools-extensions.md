---
title: Kojarzenie danych niestandardowych z programem SharePoint rozszerzeń narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 051285d1a2b3fc1c32a813fbfd8aa778befa0545
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764878"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint
  Niestandardowe dane można dodać do niektórych obiektów w rozszerzeń narzędzi SharePoint. Jest to przydatne, gdy znajdują się dane w jednym z rozszerzenia, które ma dostęp do później z poziomu innego kodu w Twoje rozszerzenie. Zamiast Implementowanie niestandardowych sposób przechowywania i uzyskać dostęp do danych, można skojarzyć dane z obiektu w rozszerzenia i następnie pobierają dane z tego samego obiektu później.  
  
 Dodawanie niestandardowych danych do obiektów jest również przydatne, jeśli chcesz zachować dane, które ma zastosowanie do określonego elementu w programie Visual Studio. Rozszerzeń narzędzi SharePoint są ładowane tylko raz w programie Visual Studio, więc rozszerzenia może działać na kilka różnych elementów (takich jak projekty, projektu elementy, lub **Eksploratora serwera** węzłów) w dowolnym momencie. Jeśli masz niestandardowe dane, które ma zastosowanie tylko do określonego elementu, możesz dodać dane do obiektu, który reprezentuje element.  
  
 Po dodaniu niestandardowych danych do obiektów w rozszerzeń narzędzi SharePoint danych nie jest trwały. Dane są dostępne tylko podczas cykl życia obiektu. Po obiektu jest odzyskana przez wyrzucanie elementów bezużytecznych, dane zostaną utracone.  
  
 W rozszerzeniach systemu projektu SharePoint można także zapisać dane ciąg będzie nadal występować po rozszerzenie zostanie zwolniona. Aby uzyskać więcej informacji, zobacz [zapisywania danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="objects-that-can-contain-custom-data"></a>Obiekty, które mogą zawierać niestandardowe dane
 Niestandardowe dane można dodać do każdego obiektu w modelu obiektów programu SharePoint narzędzia, która implementuje <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfejsu. Ten interfejs definiuje tylko jedną właściwość <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, która jest kolekcja obiektów danych niestandardowych. Następujące typy wdrożenia <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="add-and-retrieve-custom-data"></a>Dodaj i pobrać niestandardowych danych
 Aby dodać niestandardowe dane do obiektu w rozszerzeniu narzędzia programu SharePoint, należy pobrać <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość obiektu, który chcesz dodać dane, a następnie użyć <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> metodę, aby dodać dane do obiektu.  
  
 Można pobrać niestandardowych danych z obiektu w rozszerzeniu narzędzia programu SharePoint, należy pobrać <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości tego obiektu i skorzystaj z jednej z następujących metod:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Ta metoda zwraca **true** Jeśli obiekt danych nie istnieje, lub **false** Jeśli nie istnieje. Ta metoda służy do pobierania wystąpień typów wartości i typy referencyjne.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Ta metoda zwraca dane obiektu, jeśli jej zakończenia, lub **null** Jeśli nie istnieje. Ta metoda służy tylko do pobierania wystąpień typów referencyjnych.  
  
 Poniższy przykład kodu Określa, czy obiekt danych jest już skojarzony z elementem projektu. Jeśli obiekt danych nie jest już skojarzony z elementem projektu, a następnie kod dodaje obiekt do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości elementu projektu. Aby wyświetlić ten przykład w kontekście większego przykładu, zobacz [porady: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>Zobacz także
 [Koncepcje programowania oraz funkcje dla rozszerzeń narzędzi SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Wskazówki: Rozszerzanie Eksploratora serwera do wyświetlania elementów sieci Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Porady: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Instrukcje: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
   
 