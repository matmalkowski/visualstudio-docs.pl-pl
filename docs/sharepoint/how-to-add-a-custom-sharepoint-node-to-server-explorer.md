---
title: 'Porady: Dodawanie niestandardowego węzła SharePoint do Eksploratora serwera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47b51070a3f3368dbff636858c9a2e1ebf2e9f80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Porady: dodawanie niestandardowego węzła SharePoint do Eksploratora serwera
  Można dodać niestandardowe węzłów w obszarze **połączeń SharePoint** w węźle **Eksploratora serwera**. Jest to przydatne, jeśli chcesz wyświetlić dodatkowe składniki programu SharePoint, które nie są wyświetlane w **Eksploratora serwera** domyślnie. Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Aby dodać niestandardowe węzeł, należy najpierw utworzyć klasę, która definiuje nowy węzeł. Następnie utwórz rozszerzenie dodaje węzeł jako element podrzędny istniejący węzeł.  
  
### <a name="to-define-the-new-node"></a>Aby zdefiniować nowy węzeł  
  
1.  Tworzenie projektu biblioteki klas.  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejsu.  
  
4.  Do klasy, Dodaj następujące atrybuty:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Ten atrybut umożliwia Visual Studio, aby odnaleźć i załadować Twojego <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> typu konstruktora atrybutu.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. W definicji węzła ten atrybut określa identyfikator ciągu dla nowego węzła. Zalecane jest użycie formatu *nazwa firmy*. *Nazwa węzła* aby upewnić się, że wszystkie węzły mają unikatowy identyfikator.  
  
5.  W implementacji <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> metody, użyj członkami *typeDefinition* parametr, aby skonfigurować działanie nowego węzła. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> obiekt, który zapewnia dostęp do zdarzeń zdefiniowanych w <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfejsu.  
  
     Poniższy przykład kodu pokazuje sposób definiowania nowego węzła. W przykładzie założono, że projekt zawiera ikonę o nazwie CustomChildNodeIcon jako osadzony zasób.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Aby dodać nowy węzeł jako element podrzędny istniejący węzeł  
  
1.  W tym samym projekcie jako definicję węzła, Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejsu.  
  
2.  Dodaj <xref:System.ComponentModel.Composition.ExportAttribute> do klasy atrybutu. Ten atrybut umożliwia Visual Studio, aby odnaleźć i załadować Twojego <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> typu konstruktora atrybutu.  
  
3.  Dodaj <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> do klasy atrybutu. W rozszerzeniu węzeł ten atrybut określa identyfikator ciągu dla typu węzła, który ma zostać rozszerzony.  
  
     Aby określić typy wbudowanego węzła dostarczane przez program Visual Studio, należy przekazać jeden z następujących wartości wyliczenia do konstruktora atrybutu:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Użyj tych wartości, aby określić węzły połączenia lokacji (węzły, które wyświetlanie adresów URL witryny), lokacji węzłów lub innych węzłów nadrzędnych w **Eksploratora serwera**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Użyć tych wartości, aby określić jedną z wbudowanych węzły, które reprezentują poszczególnych składników w witrynie programu SharePoint, na przykład węzeł, który reprezentuje listy, pola lub typu zawartości.  
  
4.  W implementacji <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metoda, dojście <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> zdarzenie <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> parametru.  
  
5.  W <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> program obsługi zdarzeń, dodać nowego węzła do kolekcji węzły podrzędne <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> obiektu uwidocznionego przez parametr argumenty zdarzeń.  
  
     W poniższym przykładzie pokazano, jak dodać nowy węzeł jako element podrzędny węzła witryny programu SharePoint w **Eksploratora serwera**.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>Kompletny przykład  
 W poniższym przykładzie kodu przedstawiono kompletny kod, aby zdefiniować prosty węzeł i dodaj go jako element podrzędny węzła witryny programu SharePoint w **Eksploratora serwera**.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W przykładzie założono, że projekt zawiera ikonę o nazwie CustomChildNodeIcon jako osadzony zasób. W tym przykładzie również wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploying-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć **Eksploratora serwera** rozszerzenia, Utwórz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Porady: rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  