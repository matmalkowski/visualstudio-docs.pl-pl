---
title: "Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera | Dokumentacja firmy Microsoft"
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
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 879d34828e4619ac9a538f9db7cf1acef7b830b0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera
  W programie Visual Studio można nawiązać lokalnych witryn programu SharePoint na komputerze dewelopera przy użyciu **połączeń SharePoint** w węźle**Eksploratora serwera** okna. Ten węzeł Wyświetla wielu składników lokalnych witryn programu SharePoint w hierarchicznym widoku drzewa. Na przykład można wyświetlić listy, biblioteki dokumentów i typy zawartości w lokacji lokalnej. Aby uzyskać więcej informacji o korzystaniu z **Eksploratora serwera** nawiązać lokalnych witryn programu SharePoint, zobacz [przeglądanie Eksploratora przy użyciu serwera programu SharePoint połączeń](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Można rozszerzyć **połączeń SharePoint** węzła przez tworzenie rozszerzeń dla istniejących węzłów lub przez tworzenie niestandardowego typu i dodanie go do hierarchii z węzłów.  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Zadania dla rozszerzanie węzła połączeń SharePoint  
 Aby rozszerzyć istniejący węzeł, tworzenia rozszerzenia programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejsu. Podczas rozszerzania węzła do węzła, takie jak własne elementy menu skrótów lub właściwości niestandardowe można dodać funkcji. Aby uzyskać więcej informacji, zobacz [porady: rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Do utworzenia typu niestandardowego, tworzenia rozszerzenia programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejsu. Tworzenie niestandardowego węzła, jeśli chcesz wyświetlić składniki witryny programu SharePoint, które nie są wyświetlane w **Eksploratora serwera** domyślnie. Na przykład **Eksploratora serwera** jest nie wyświetlania galerii składników Web Part w witrynie programu SharePoint przez domyślny, ale można dodać niestandardowe węzła, w tym. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie niestandardowego węzła SharePoint do Eksploratora serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) i [wskazówki: rozszerzanie Eksploratora serwera do części sieci Web wyświetlaną](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="adding-custom-properties-to-nodes"></a>Dodawanie właściwości niestandardowych do węzłów  
 Rozszerzanie węzła lub utworzenie typu niestandardowego, można dodać właściwości niestandardowe do węzła. Właściwości są wyświetlane w **właściwości** okna po wybraniu węzła.  
  
 Istnieją dwa typy właściwości niestandardowe, które można dodać do węzła:  
  
-   Właściwości, które wyświetlić zestaw danych tylko do odczytu z witryny programu SharePoint. Dane w tym artykule opisano składnik programu SharePoint, która reprezentuje węzeł. Aby uzyskać wskazówki, które pokazuje, jak to zrobić, zobacz [wskazówki: rozszerzanie Eksploratora serwera do części sieci Web wyświetlaną](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Właściwości wyświetlanych danych niestandardowych odczytu/zapisu. Na przykład kodu, który pokazuje, jak to zrobić, zobacz [porady: rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="getting-data-for-built-in-nodes"></a>Pobieranie danych dla wbudowanego węzłów  
 Obejmują wszystkie węzły wbudowanych dostarczane przez program Visual Studio niektóre dane dotyczące składnik programu SharePoint, które reprezentują. Węzeł, który reprezentuje listę w witrynie programu SharePoint umożliwia na przykład niektóre dane dotyczące listy, takie jak tytuł i adres URL domyślny widok listy.  
  
 Aby uzyskać dostęp do tych danych, należy pobrać obiekt danych z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> obiekt, który reprezentuje węzeł planuje się. Typ obiektu danych zależy od typu węzła.  
  
 Poniższy przykład kodu pokazuje, jak można pobrać obiektu danych dla węzła listy. Aby wyświetlić ten przykład w kontekście większego przykładu, zobacz [porady: pobieranie danych dla wbudowanego węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 W poniższej tabeli wymieniono typy obiektów danych dla każdego typu wbudowanego węzła.  
  
|Typ węzła|Typ obiektu danych|  
|---------------|----------------------|  
|Węzeł witryny programu SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Typ zawartości|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Funkcja|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Pole|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|Lista|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Szablon listy|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Widok listy (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Skojarzenia przepływu pracy|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Szablon przepływu pracy|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości, zobacz [kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Rozszerzanie Eksploratora serwera do wyświetlania elementów sieci Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Porady: rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Porady: Dodawanie niestandardowego węzła SharePoint do Eksploratora serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Porady: pobieranie danych dla wbudowanego węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  