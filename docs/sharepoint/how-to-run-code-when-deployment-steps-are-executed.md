---
title: "Porady: uruchamianie kodu w trakcie kroków wdrożeniowych | Dokumentacja firmy Microsoft"
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ad603c9f303cd5bf2b3dc317efddd2694e10a867
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Porady: uruchamianie kodu w trakcie kroków wdrożeniowych
  Jeśli chcesz, dodatkowe zadania do wykonania kroku wdrożenia w projekcie programu SharePoint, można obsługiwać zdarzenia, które są wywoływane przez SharePoint — elementy projektu przed i po Visual Studio wykonuje każdy krok wdrożenia. Aby uzyskać więcej informacji, zobacz [rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>Do uruchomienia kodu po kroków wdrożeniowych  
  
1.  Tworzenie rozszerzenia elementu projektu, rozszerzenia projektu lub definicji typu elementu projektu. Więcej informacji znajduje się w następujących tematach:  
  
    -   [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  W rozszerzeniu, obsługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> zdarzenia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> obiektu (w rozszerzenia elementu projektu lub rozszerzenia projektu) lub <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> obiektu (w definicji typu elementu projektu).  
  
3.  W przypadku programów obsługi, użyj <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> i <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> parametry, aby uzyskać informacje na temat kroku wdrożenia. Na przykład można określić kroku wdrożenia, który jest wykonywany i określa, czy rozwiązanie jest wdrożony lub wycofany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób obsługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> zdarzenia do rozszerzenia dla elementu projektu wystąpienia listy. To rozszerzenie zapisuje komunikat dodatkowe do **dane wyjściowe** okna, jeśli program Visual Studio odtwarzania puli aplikacji podczas wdrażania i wycofania rozwiązania.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Instrukcje: Uruchamianie kodu, gdy projekt SharePoint jest wdrożony lub wycofany](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  