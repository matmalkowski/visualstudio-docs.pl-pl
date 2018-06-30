---
title: 'Porady: wykonywanie polecenia SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ce195dd34c7c0b509f9de4cbe2cfd14d9a477f87
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120611"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Porady: wykonywanie polecenia SharePoint
  Jeśli chcesz użyć modelu obiektów serwera w rozszerzeniu narzędzia programu SharePoint, należy utworzyć niestandardowego *polecenia SharePoint* do wywołania interfejsu API. Po zdefiniowaniu polecenia i wdrożyć ją z rozszerzeniem narzędzia programu SharePoint, rozszerzenie można wykonać polecenie do wywołania w modelu obiektów programu SharePoint server. Można wykonać polecenia, użyj jednej z metod parametr ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu.  
  
 Aby uzyskać więcej informacji dotyczących przeznaczenia polecenia SharePoint, zobacz [wywołują modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-execute-a-sharepoint-command"></a>Do wykonania polecenia SharePoint  
  
1.  Rozszerzenie narzędzia programu SharePoint, uzyskanie <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu. Sposób otrzymasz <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu zależy od typu rozszerzenia tworzenia:  
  
    -   W rozszerzeniach systemu projektu SharePoint, należy użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> właściwości.  
  
         Aby uzyskać więcej informacji na temat rozszerzeń systemu projektu, zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   W rozszerzeniu **połączeń SharePoint** w węźle **Eksploratora serwera**, użyj <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> właściwości. Aby uzyskać <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> obiektów, użyj <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> właściwości.  
  
         Aby uzyskać więcej informacji na temat **Eksploratora serwera** rozszerzenia, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   W kodzie, który nie jest częścią rozszerzeń narzędzi SharePoint, takich jak Kreator szablonu projektu, należy użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> właściwości.  
  
         Aby uzyskać więcej informacji na temat pobierania usługi projektu, zobacz [korzystania z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Wywoływanie jednego z metody parametr ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu. Podaj nazwę polecenia, które chcesz wykonać, aby pierwszy argument metody parametr ExecuteCommand. Jeśli polecenie ma niestandardowy parametr, do drugiego argumentu metody parametr ExecuteCommand przekazać tego parametru.  
  
     Ma innego przeciążenia parametr ExecuteCommand dla każdego podpisu obsługiwanych poleceń. W poniższej tabeli wymieniono obsługiwane podpisy i które przeciążenia dla każdego podpisu.  
  
    |Polecenie podpisu|Parametr ExecuteCommand przeciążenia do użycia|  
    |-----------------------|------------------------------------|  
    |Polecenie ma tylko wartość domyślna <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr i brak wartości zwracanej.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Polecenie ma tylko wartość domyślna <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr i wartość zwracaną.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Polecenie zawiera dwa parametry (wartość domyślna <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> i niestandardowych parametru) i brak wartości zwracanej.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Polecenie ma dwa parametry i wartości zwracanej.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób użycia <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> przeciążenia do wywołania `Contoso.Commands.UpgradeSolution` polecenia, które jest opisane w [porady: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 `Execute` w poniższym przykładzie metoda jest implementacją <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> metody <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfejsu w niestandardowego kroku wdrożenia. Aby wyświetlić ten kod w kontekście większego przykładu, zobacz [wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Należy zauważyć następujące szczegółowe informacje o wywołaniu <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> metody:  
  
-   Pierwszy parametr określa polecenie, które ma zostać wywołana. Ten ciąg jest zgodna z wartością, który jest przekazywany do <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> w definicji polecenia.  
  
-   Drugi parametr jest wartością, który chcesz przekazać do niestandardowy drugi parametr polecenia. W takim przypadku jest pełna ścieżka *WSP* pliku, który jest uaktualniany do witryny programu SharePoint.  
  
-   Ten kod nie zostały spełnione niejawne <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> do polecenia parametr. Ten parametr jest przekazywany do polecenia automatycznie po wywołaniu polecenia z rozszerzeniem systemu projektu SharePoint lub rozszerzenie **połączeń SharePoint** w węźle **Eksploratora serwera**. W przypadku innych typów rozwiązań, takich jak Kreator szablonu projektu, który implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu, ten parametr jest **null**.  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do zestawu Microsoft.VisualStudio.SharePoint.  
  
## <a name="see-also"></a>Zobacz także
 [Wywołują modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Porady: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Wskazówki: Rozszerzanie Eksploratora serwera do wyświetlania elementów sieci web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
