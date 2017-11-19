---
title: "Porady: pobieranie danych dla wbudowanego węzła SharePoint w Eksploratorze serwera | Dokumentacja firmy Microsoft"
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
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b61003516d7551c99f6e265ca2eeced9226958df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Porady: pobieranie danych dla wbudowanego węzła SharePoint w Eksploratorze serwera
  Dla każdego wbudowanego węzła SharePoint w **Eksploratora serwera**, można pobrać danych dla podstawowy składnik programu SharePoint, która reprezentuje węzeł. Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak można pobrać danych na liście programu SharePoint źródłowego węzła listy reprezentuje w **Eksploratora serwera**. Domyślnie lista węzły mają **Wyświetl w przeglądarce** elementu menu kontekstowego, które można kliknąć, aby otworzyć na listach w przeglądarce sieci Web. W tym przykładzie rozszerza listy węzłów, dodając **widoku w programie Visual Studio** elementu menu kontekstowego, którego kliknięcie spowoduje otwarcie listy bezpośrednio w programie Visual Studio. Kod uzyskuje dostęp do danych listy dla węzła uzyskać adres URL na liście, aby otworzyć w programie Visual Studio.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 W tym przykładzie używane usługa projektu SharePoint, aby uzyskać <xref:EnvDTE.DTE> obiekt, który jest używany do otwierania list w programie Visual Studio. Aby uzyskać więcej informacji na temat usługi projektu SharePoint, zobacz [przy użyciu usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Aby uzyskać więcej informacji na temat podstawowych zadań do tworzenia rozszerzeń dla węzła SharePoint, zobacz [porady: rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do następujących zestawów:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć **Eksploratora serwera** rozszerzenia, Utwórz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Porady: rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  