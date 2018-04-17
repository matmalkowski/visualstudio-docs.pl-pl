---
title: Korzystanie z usługi projektu SharePoint | Dokumentacja firmy Microsoft
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
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: efe2e2073ead64bfbc697b9d6c824066af947580
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-sharepoint-project-service"></a>Korzystanie z usługi projektu SharePoint
  System projektu SharePoint obejmuje projektu usługi, która służy do wykonywania zadań związanych z systemem projektu. Usługa projektu jest <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu.  
  
 Można uzyskać dostępu do usługi projektu SharePoint w dowolnym rozszerzeniem narzędzia programu SharePoint. Można także przejść w innych rodzajów rozszerzeń programu Visual Studio, takie jak dodatków i VSPackages. Aby uzyskać więcej informacji, zobacz [porady: pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
## <a name="project-service-features"></a>Funkcje usługi projektu  
 W poniższej tabeli wymieniono zadania, które można wykonywać za pomocą usługi projektu SharePoint i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> metody lub właściwości można używać do wykonywania poszczególnych zadań.  
  
|Zadanie|Elementu członkowskiego do użycia|  
|----------|-------------------|  
|Dostęp do żadnego projektu programu SharePoint, która jest otwarta w programie Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> Właściwość.|  
|Dostęp do wszystkich typów elementów projektu SharePoint, które są dostępne (w tym typów elementów projektu wbudowanych i niestandardowych).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> Właściwość.|  
|Dostęp do wszystkich kroków wdrażania, które są dostępne dla projektów programu SharePoint (w tym kroki wdrażania wbudowanych i niestandardowych).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> Właściwość.|  
|Dostęp do zdarzeń, które są wywoływane, gdy projektant refaktoryzuje kodu w projekcie programu SharePoint.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> Właściwość.|  
|Wykonaj niestandardowy *polecenia SharePoint* , który odwołuje się do modelu obiektów serwera programu SharePoint. Aby uzyskać więcej informacji na temat poleceń programu SharePoint, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> Właściwość.|  
|Konwertuj typu w systemu projektu SharePoint do typu w modelu obiektu automatyzacji programu Visual Studio lub model obiektów integracji i na odwrót. Aby uzyskać więcej informacji, zobacz [konwertowanie między SharePoint typami systemu projektu i inne typy projektów Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> Metoda.|  
|Zapisz komunikaty do **dane wyjściowe** okna lub **listy błędów** okna w programie Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> Właściwość.|  
|Dostęp do innych usług, które są dostępne w programie Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> Właściwość.|  
|Pobrać ścieżki do folderu instalacji lokalnej witryny programu SharePoint służący do debugowania rozwiązania.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> Właściwość.|  
|Określić, czy [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] lub [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] jest zainstalowany na komputerze.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> Właściwość.|  
|Sprawdzanie poprawności funkcji lub pakietu rozwiązania programu SharePoint.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> Właściwość.|  
  
## <a name="see-also"></a>Zobacz też  
 [Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Porady: pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Omówienie programu SharePoint modelu programowania rozszerzeń narzędzi](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Porady: Pobierz usługi z obiektu DTE](http://msdn.microsoft.com/library/bb166401.aspx)  
  
  