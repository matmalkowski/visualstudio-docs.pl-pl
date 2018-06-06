---
title: Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 64de38fe796ce3c1e0d333a22582ad2973e1c4d2
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765362"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio
  W niektórych przypadkach może być obiektem systemu projektu SharePoint i chcesz używać funkcji odpowiedni obiekt w modelu obiektu automatyzacji programu Visual Studio lub model obiektów integracji, albo na odwrót. W takich przypadkach można użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metoda usługa projektu SharePoint, aby przekonwertować obiekt do innego obiektu modelu.  
  
 Na przykład może być <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiekt, ale chcesz używać metod, które są dostępne tylko na <xref:EnvDTE.Project> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> obiektu. W takim przypadku można użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodę, aby przekonwertować <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> do <xref:EnvDTE.Project> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 Aby uzyskać więcej informacji na temat modelu obiektu automatyzacji programu Visual Studio i model obiektów integracji programu Visual Studio, zobacz [omówienie programowania modelu z rozszerzeniami narzędzi SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="types-of-conversions"></a>Konwersje typów
 Poniższa tabela zawiera listę typów, które tej metody można konwertować między systemu projektu SharePoint a innymi modelami obiektu Visual Studio.  
  
|Typ systemu projektu SharePoint|Odpowiednie typy w modelach obiektu automatyzacji i integracji|  
|------------------------------------|-------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> lub<br /><br /> Wszelkie interfejs w modelu obiektu integracji programu Visual Studio, który jest implementowany przez obiekt COM dla projektu. Te interfejsy zawierają <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (lub interfejsu pochodnego), i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. Lista głównych interfejsy implementowane przez projekty, zobacz [projektu modelu podstawowe składniki](/visualstudio/extensibility/internals/project-model-core-components).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> lub<br /><br /> A<xref:System.UInt32> wartość (nazywanych również VSITEMID), która identyfikuje element członkowski projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> go zawiera. Tę wartość można przekazać do *itemid* parametru niektórych <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób użycia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodę, aby przekonwertować <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> do obiektu <xref:EnvDTE.Project>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]  
  
 Ten przykład wymaga:  
  
-   Rozszerzenie zawiera odwołanie do systemu projektu SharePoint *EnvDTE.dll* zestawu. Aby uzyskać więcej informacji, zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Kod, który rejestruje `projectService_ProjectAdded` można obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> zdarzenie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu. Na przykład zobacz [porady: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Zobacz także
 [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Porady: pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Omówienie modelu programowania rozszerzeń narzędzi SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
