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
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d5692195f340ce347df0bc6f8ad2d60225f24e6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
  