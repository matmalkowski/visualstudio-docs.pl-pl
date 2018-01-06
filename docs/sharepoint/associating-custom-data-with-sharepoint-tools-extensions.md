---
title: "Kojarzenie danych niestandardowych z programem SharePoint rozszerzeń narzędzi | Dokumentacja firmy Microsoft"
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
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 24525e553fabfd05972cbe2ee59fa1260d3b855b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="associating-custom-data-with-sharepoint-tools-extensions"></a>Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint
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
  
## <a name="adding-and-retrieving-custom-data"></a>Dodawanie i pobieranie danych niestandardowych  
 Aby dodać niestandardowe dane do obiektu w rozszerzeniu narzędzia programu SharePoint, należy pobrać <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość obiektu, który chcesz dodać dane, a następnie użyć <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> metodę, aby dodać dane do obiektu.  
  
 Można pobrać niestandardowych danych z obiektu w rozszerzeniu narzędzia programu SharePoint, należy pobrać <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości tego obiektu i skorzystaj z jednej z następujących metod:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>., Ta metoda zwraca **true** Jeśli obiekt danych nie istnieje, lub **false** Jeśli nie istnieje. Ta metoda służy do pobierania wystąpień typów wartości i typy referencyjne.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>., Ta metoda zwraca dane obiektu, jeśli jej zakończenia, lub **null** Jeśli nie istnieje. Ta metoda służy tylko do pobierania wystąpień typów referencyjnych.  
  
 Poniższy przykład kodu Określa, czy obiekt danych jest już skojarzony z elementem projektu. Jeśli obiekt danych nie jest już skojarzony z elementem projektu, a następnie kod dodaje obiekt do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości elementu projektu. Aby wyświetlić ten przykład w kontekście większego przykładu, zobacz [porady: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>Zobacz też  
 [Koncepcje programowania oraz funkcje dla rozszerzeń narzędzi SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Wskazówki: Rozszerzanie Eksploratora serwera do wyświetlania elementów sieci Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Porady: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Porady: Dodawanie właściwości do typu elementu projektu SharePoint niestandardowych] (.. /SharePoint/How-to-Add-a-Property-to-a-Custom-SharePoint-Project-Item-type.MD   
  