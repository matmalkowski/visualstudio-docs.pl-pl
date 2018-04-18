---
title: 'Porady: Ustawianie poleceń wdrażania SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8779ba4ee4cf9803982d9849b3af7c83930d8a5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Porady: ustawianie poleceń wdrażania SharePoint
  Proces wdrażania można dostosować, ustawiając polecenia przed wdrożeniem i po wdrożeniu. Te polecenia są uruchamiane przed i po nich inne akcje wdrażania podczas debugowania rozwiązań programu SharePoint z programu Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Aby dodać polecenia przed wdrożeniem  
  
1.  Na pasku menu wybierz **projektu**, * ProjectName ***właściwości**.  
  
2.  Wybierz **SharePoint** kartę.  
  
3.  W **wiersza polecenia przed wdrożeniem** tekst Wprowadź MS-DOS lub MSBuild poleceń, aby dostosować ten krok.  
  
     Na przykład, aby wyświetlić listę zawartości katalogu, ukończenie wdrożenia, wprowadź **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Aby dodać polecenia po wdrożeniu  
  
1.  Na pasku menu wybierz **projektu**, * ProjectName ***właściwości**.  
  
2.  Wybierz **SharePoint** kartę.  
  
3.  W **wiersza polecenia po wdrożeniu** tekst Wprowadź MS-DOS lub MSBuild poleceń, aby dostosować ten krok.  
  
     Na przykład, aby wyświetlić listę zawartości katalogu, po zakończeniu wdrożenia, wprowadź **dir**. Aby użyć zmiennej MSBuild, aby skopiować zestaw z katalogu kompilacji, wprowadź **skopiuj c:\DeploymentDirectory $(targetpath) —**.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania pakowania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  