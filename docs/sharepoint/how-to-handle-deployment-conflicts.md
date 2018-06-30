---
title: 'Porady: Obsługa konfliktów wdrożenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d7c30a7c634c30c9fe3e92ef988d7d8fc043cf6b
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120594"
---
# <a name="how-to-handle-deployment-conflicts"></a>Porady: Obsługa konfliktów wdrożenia
  Możesz podać kodu do obsługi wdrożenia konfliktów dla elementu projektu SharePoint. Może na przykład określić, czy wszystkie pliki w bieżącym elemencie projektu już istnieje w lokalizacji wdrożenia, a następnie usuń wdrożonych plików, przed wdrożeniem bieżącego elementu projektu. Aby uzyskać więcej informacji na temat konflikty wdrażania, zobacz [rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-handle-a-deployment-conflict"></a>Do obsługi konfliktów wdrożenia  
  
1.  Tworzenie rozszerzenia elementu projektu, rozszerzenia projektu lub definicji typu elementu projektu. Więcej informacji znajduje się w następujących tematach:  
  
    -   [Porady: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Porady: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Porady: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  W rozszerzeniu, obsługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> zdarzenie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> obiektu (w rozszerzenia elementu projektu lub rozszerzenia projektu) lub <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> obiektu (w definicji typu elementu projektu).  
  
3.  W obsłudze zdarzeń ustalić, czy jest konflikt między elementu projektu, który jest wdrażany i wdrożone rozwiązanie w witrynie programu SharePoint, na podstawie kryteriów, które są stosowane do danego scenariusza. Można użyć <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> właściwość parametru argumenty zdarzeń do analizowania elementu projektu, który jest wdrażany i analizować plików w lokalizacji wdrożenia przez wywołanie polecenia SharePoint zdefiniowanego w tym celu.  
  
     Dla wielu typów konfliktów najpierw można określić kroku wdrożenia, który jest wykonywany. Można to zrobić za pomocą <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> właściwość parametru argumenty zdarzeń. Chociaż zazwyczaj warto wykrywania konfliktów podczas wbudowane <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> kroku wdrożenia, możesz sprawdzić konflikty podczas wykonywania kroku wszystkie wdrożenia.  
  
4.  Jeśli istnieje konflikt, użyj <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metody <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> właściwości argumenty zdarzeń, aby utworzyć nową <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> obiektu. Ten obiekt reprezentuje konflikt wdrażania. W przypadku wywołania do <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metody również określić metodę, która jest wywoływana w celu rozwiązania konfliktu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia podstawowy proces obsługi konflikt wdrażania w rozszerzenia elementu projektu dla elementów projektu definicji listy. Aby obsłużyć konflikt wdrażania do innego typu elementu projektu, przekazać inny ciąg do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Aby uzyskać więcej informacji, zobacz [rozszerzyć SharePoint — elementy projektu](../sharepoint/extending-sharepoint-project-items.md).  
  
 Dla uproszczenia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> obsługi zdarzeń w tym przykładzie przyjęto założenie, że istnieje konflikt wdrażania (czyli zawsze jest dodawany nowy <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> obiektu) i `Resolve` metoda po prostu zwraca **true** z informacją, że Konflikt został rozwiązany. W rzeczywistym scenariuszu sieci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> obsługi zdarzeń czy najpierw ustalić, czy istnieje konflikt między plikiem w bieżącym elemencie projektu i pliku w lokalizacji wdrożenia, a następnie dodaj <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> obiekt tylko, jeśli istnieje konflikt. Na przykład może użyć `e.ProjectItem.Files` właściwości w obsłudze zdarzeń do analizowania plików elementu projektu, i może wywołać polecenie programu SharePoint do analizowania plików w lokalizacji wdrożenia. Podobnie, w rzeczywistym scenariuszu `Resolve` metody może wywołać polecenie programu SharePoint, aby rozwiązać konflikt w witrynie programu SharePoint. Aby uzyskać więcej informacji o tworzeniu polecenia SharePoint, zobacz [porady: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Rozszerzanie elementów projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Porady: uruchamianie kodu, gdy kroków wdrożeniowych](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Porady: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
