---
title: "Porady: pobieranie usługi projektu SharePoint | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: b1abdf4a48d05285a7394469dd391caf48981f9f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Porady: pobieranie usługi projektu SharePoint
  Aby dostęp do usługi projektu SharePoint w następujących rozwiązań:  
  
-   Rozszerzenie systemu projektu SharePoint, takie jak rozszerzenia projektu, rozszerzenia elementu projektu lub definicji typu elementu projektu. Aby uzyskać więcej informacji o tych typach rozszerzeń, zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Rozszerzenie **połączeń SharePoint** w węźle **Eksploratora serwera**. Aby uzyskać więcej informacji o tych typach rozszerzeń, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Innego typu rozszerzenia programu Visual Studio, takich jak pakiet VSPackage.  
  
## <a name="retrieving-the-service-in-project-system-extensions"></a>Trwa pobieranie usług w rozszerzeniach systemu projektu  
 W dowolnej rozszerzenia systemu projektu SharePoint uzyskujesz dostęp za pomocą usługi projektu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektu.  
  
 Usługa projektu można również pobierać za pomocą poniższych procedur.  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Można pobrać usługi w rozszerzeniu projektu  
  
1.  W implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfejsu, Znajdź <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metody.  
  
2.  Użyj *projectService* parametr, aby uzyskać dostęp do usługi.  
  
     Poniższy przykładowy kod przedstawia sposób korzystania z usługi projektu można zapisać komunikatu na **dane wyjściowe** okna i **listy błędów** okna w rozszerzeniu prostego projektu.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     Aby uzyskać więcej informacji o tworzeniu rozszerzenia projektu, zobacz [porady: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Aby pobrać usługę w rozszerzenia elementu projektu  
  
1.  W implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejsu, Znajdź <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody.  
  
2.  Użyj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> właściwość *projectItemType* parametru można pobrać usługi.  
  
     Poniższy przykładowy kod przedstawia sposób korzystania z usługi projektu można zapisać komunikatu na **dane wyjściowe** okna i **listy błędów** okna proste rozszerzenia **definicji listy** elementu projektu.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     Aby uzyskać więcej informacji o tworzeniu rozszerzenia elementu projektu, zobacz [porady: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Aby pobrać usługę w definicji typu elementu projektu  
  
1.  W implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu, Znajdź <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody.  
  
2.  Użyj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> właściwość *typeDefinition* parametru można pobrać usługi.  
  
     Poniższy przykładowy kod przedstawia sposób korzystania z usługi projektu można zapisać komunikatu na **dane wyjściowe** okna i **listy błędów** okna w definicji typu elementu projektu proste.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     Aby uzyskać więcej informacji na temat definiowania typów elementów projektu, zobacz [porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="retrieving-the-service-in-server-explorer-extensions"></a>Trwa pobieranie usług w rozszerzenia Eksploratora serwera  
 W rozszerzeniu **połączeń SharePoint** w węźle **Eksploratora serwera**, uzyskać dostęp do usługi projektu za pomocą <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> obiektu.  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Można pobrać usługi w rozszerzeniu Eksploratora serwera  
  
1.  Pobierz <xref:System.IServiceProvider> obiekt z <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> obiektu w Twoje rozszerzenie.  
  
2.  Użyj <xref:System.IServiceProvider.GetService%2A> metody, aby zażądać <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu.  
  
     Poniższy przykładowy kod przedstawia sposób korzystania z usługi projektu można zapisać komunikatu na **dane wyjściowe** okna i **listy błędów** okno z menu skrótów, które rozszerzenie dodaje do listy węzłów w **Eksploratora serwera**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     Aby uzyskać więcej informacji na temat rozszerzania **połączeń SharePoint** w węźle **Eksploratora serwera**, zobacz [porady: rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="retrieving-the-service-in-other-visual-studio-extensions"></a>Trwa pobieranie usług w innych rozszerzeń programu Visual Studio  
 Możesz pobrać pakiet VSPackage lub dowolnego rozszerzenia programu Visual Studio, który ma dostęp do usługi projektu <xref:EnvDTE80.DTE2> obiektu w modelu obiektu automatyzacji, takich jak Kreator szablonu projektu, który implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu.  
  
 W pakiet VSPackage, możesz poprosić <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu przy użyciu jednej z następujących metod:  
  
-   <xref:System.IServiceProvider.GetService%2A> Metody zarządzanych pakiet VSPackage, która jest pochodną <xref:Microsoft.VisualStudio.Shell.Package> klasy. Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie usługi](../extensibility/how-to-get-a-service.md).  
  
-   Statycznych <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody. Aby uzyskać więcej informacji, zobacz [GetGlobalService użyj](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).  
  
 Rozszerzenia programu Visual Studio, który ma dostęp do <xref:EnvDTE80.DTE2> obiektu, możesz poprosić o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu za pomocą <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metody <xref:Microsoft.VisualStudio.Shell.ServiceProvider> obiektu. Aby uzyskać więcej informacji, zobacz [pobieranie usługi z obiektu DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Porady: uzyskiwanie usługi](../extensibility/how-to-get-a-service.md)   
 [Instrukcje: korzystanie z kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  