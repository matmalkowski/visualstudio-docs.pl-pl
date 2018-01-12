---
title: "Porady: Ustawianie poleceń wdrażania SharePoint | Dokumentacja firmy Microsoft"
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
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2f465deaaca406c28aab177434e72de9746fb101
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Porady: ustawianie poleceń wdrażania SharePoint
  Proces wdrażania można dostosować, ustawiając polecenia przed wdrożeniem i po wdrożeniu. Te polecenia są uruchamiane przed i po nich inne akcje wdrażania podczas debugowania rozwiązań programu SharePoint z programu Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Aby dodać polecenia przed wdrożeniem  
  
1.  Na pasku menu wybierz **projektu**, *ProjectName***właściwości**.  
  
2.  Wybierz **SharePoint** kartę.  
  
3.  W **wiersza polecenia przed wdrożeniem** tekst Wprowadź MS-DOS lub MSBuild poleceń, aby dostosować ten krok.  
  
     Na przykład, aby wyświetlić listę zawartości katalogu, ukończenie wdrożenia, wprowadź **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Aby dodać polecenia po wdrożeniu  
  
1.  Na pasku menu wybierz **projektu**, *ProjectName***właściwości**.  
  
2.  Wybierz **SharePoint** kartę.  
  
3.  W **wiersza polecenia po wdrożeniu** tekst Wprowadź MS-DOS lub MSBuild poleceń, aby dostosować ten krok.  
  
     Na przykład, aby wyświetlić listę zawartości katalogu, po zakończeniu wdrożenia, wprowadź **dir**. Aby użyć zmiennej MSBuild, aby skopiować zestaw z katalogu kompilacji, wprowadź **skopiuj c:\DeploymentDirectory $(targetpath) —**.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania pakowania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  