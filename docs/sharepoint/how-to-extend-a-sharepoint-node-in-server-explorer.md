---
title: "Porady: rozszerzanie węzła SharePoint w Eksploratorze serwera | Dokumentacja firmy Microsoft"
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
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 063586b6a4a839b8500ea3ef1729331bf82338ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Porady: rozszerzanie węzła SharePoint w Eksploratorze serwera
  Można rozszerzyć węzłów w **połączeń SharePoint** w węźle **Eksploratora serwera**. Jest to przydatne, jeśli chcesz dodać nowe węzły podrzędne, elementy menu skrótów lub właściwości do istniejący węzeł. Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Aby rozszerzyć węzła SharePoint w Eksploratorze serwera  
  
1.  Tworzenie projektu biblioteki klas.  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejsu.  
  
4.  Dodaj <xref:System.ComponentModel.Composition.ExportAttribute> do klasy atrybutu. Ten atrybut umożliwia Visual Studio, aby odnaleźć i załadować Twojego <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> typu konstruktora atrybutu.  
  
5.  Dodaj <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> do klasy atrybutu. Ten atrybut określa identyfikator ciągu dla typu węzła, który ma zostać rozszerzony.  
  
     Aby określić typy wbudowanego węzła dostarczane przez program Visual Studio, należy przekazać jeden z następujących wartości wyliczenia do konstruktora atrybutu:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Użyj tych wartości, aby określić węzły połączenia lokacji (węzły, które wyświetlanie adresów URL witryny), lokacji węzłów lub innych węzłów nadrzędnych w **Eksploratora serwera**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Użyć tych wartości, aby określić jedną z wbudowanych węzły, które reprezentują poszczególnych składników w witrynie programu SharePoint, na przykład węzeł, który reprezentuje listy, pola lub typu zawartości.  
  
6.  W implementacji <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metody, użyj członkami *nodeType* parametru w celu dodawania funkcji do węzła. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> obiekt, który zapewnia dostęp do zdarzeń zdefiniowanych w <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfejsu. Na przykład można obsługiwać następujące zdarzenia:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Obsługa tego zdarzenia, aby dodać nowe węzły podrzędne węzła. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie niestandardowego węzła SharePoint do Eksploratora serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Obsługa tego zdarzenia, aby dodać element menu skrótów niestandardowych do węzła.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Obsługa tego zdarzenia, aby dodać właściwości niestandardowe do węzła. Właściwości są wyświetlane w **właściwości** okna po wybraniu węzła.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób tworzenia dwa różne typy rozszerzeń węzła:  
  
-   Rozszerzenie dodaje elementu menu kontekstowego dla węzłów witryny programu SharePoint. Po kliknięciu elementu menu przedstawia nazwę węzła, który został kliknięty.  
  
-   Rozszerzenie dodaje właściwość niestandardowa o nazwie **ContosoExampleProperty** na każdym węźle, który reprezentuje pole o nazwie **treści**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
 To rozszerzenie dodaje właściwości można edytować ciągu do węzłów. Można również utworzyć niestandardowe właściwości, które zawiera tylko do odczytu danych z serwera programu SharePoint. Na przykład, który pokazuje, jak to zrobić, zobacz [wskazówki: rozszerzanie Eksploratora serwera do części sieci Web wyświetlaną](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploying-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć **Eksploratora serwera** rozszerzenia, Utwórz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dodawanie niestandardowego węzła SharePoint do Eksploratora serwera](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Wskazówki: Rozszerzanie Eksploratora serwera do wyświetlania elementów sieci Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  