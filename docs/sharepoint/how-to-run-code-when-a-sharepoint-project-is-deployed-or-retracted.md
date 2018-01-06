---
title: "Porady: uruchamianie kodu, gdy projekt SharePoint jest wdrożony lub wycofany | Dokumentacja firmy Microsoft"
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
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b452d28b1fc8173435b4de993561b59a680b0fed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Porady: uruchamianie kodu, gdy projekt SharePoint jest wdrożony lub wycofany
  Jeśli chcesz wykonanie dodatkowych zadań, gdy projekt SharePoint jest wdrożony lub wycofany może obsłużyć zdarzenia, które są generowane przez program Visual Studio. Aby uzyskać więcej informacji, zobacz [rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Do uruchomienia kodu, gdy projekt SharePoint jest wdrożony lub wycofany  
  
1.  Tworzenie rozszerzenia elementu projektu, rozszerzenia projektu lub definicji typu elementu projektu. Więcej informacji znajduje się w następujących tematach:  
  
    -   [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  W rozszerzeniu dostępu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu. Aby uzyskać więcej informacji, zobacz [porady: pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Obsługa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> zdarzeń usługi projektu.  
  
4.  W przypadku programów obsługi, użyj <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> parametr, aby uzyskać informacje o bieżącej sesji wdrożenia. Na przykład można określić, który projekt jest w bieżącej sesji, wdrożenia i czy jest on wdrożony lub wycofany.  
  
 Poniższy przykład kodu pokazuje sposób obsługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> zdarzenia w rozszerzeniu projektu. To rozszerzenie zapisuje komunikat dodatkowe do **dane wyjściowe** okna, jeśli wdrożenie momencie rozpoczęcia i zakończenia dla projektu programu SharePoint.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Instrukcje: Uruchamianie kodu w trakcie kroków wdrożeniowych](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  