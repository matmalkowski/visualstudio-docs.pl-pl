---
title: 'Porady: edytowanie konfiguracji wdrażania SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
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
ms.openlocfilehash: 9640d98522c74fb33f8845e255511a807e03961e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120323"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Porady: edytowanie konfiguracji wdrażania SharePoint
  Można utworzyć konfiguracji wdrożenia lub zmodyfikować istniejącą konfigurację wdrożenia. Na przykład można uruchomić w jednym kroku lub zmienić kolejność kroków procesu wdrażania. Można utworzyć lub zmodyfikować konfiguracje wdrożenia, ponieważ nie można zmienić konfiguracji wbudowanych i programowo dodany.  
  
## <a name="create-a-sharepoint-deployment-configuration"></a>Tworzenie konfiguracji wdrażania SharePoint  
  
#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Aby utworzyć konfiguracji wdrażania SharePoint  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt programu SharePoint, a następnie na pasku menu wybierz **projektu**, * ProjectName ***właściwości**.  
  
2.  Na **SharePoint** , wybierz pozycję **nowy** przycisku.  
  
     **Dodać nową konfigurację wdrożenia** zostanie wyświetlone okno dialogowe.  
  
3.  W **nazwa** tekst Wprowadź nazwę dla konfiguracji wdrażania.  
  
4.  W **dostępne kroki wdrażania** okienku wybierz kroki, które chcesz dodać do konfiguracji wdrożenia, wybierz (**>**) przycisk, a następnie wybierz pozycję **OK** przycisku.  
  
    > [!NOTE]  
    >  Jeśli skonfigurowano polecenia przed wdrożeniem lub polecenia po wdrożeniu tych kroków Uruchom tylko wtedy, gdy zostaną dodane do konfiguracji wdrożenia dostosowane.  
  
## <a name="change-the-active-deployment-configuration"></a>Zmień konfigurację aktywnych wdrożeń  
  
#### <a name="to-change-the-active-deployment-configuration"></a>Aby zmienić konfigurację aktywnych wdrożeń  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt programu SharePoint, a następnie na pasku menu wybierz **projektu** > **\<*ProjectName*> Właściwości**.  
  
2.  Wybierz **SharePoint** kartę.  
  
3.  W **aktywnej konfiguracji wdrożenia** pola listy, wybierz nazwę dla konfiguracji wdrażania, który ma być używany.  
  
## <a name="see-also"></a>Zobacz także
 [Pakiet i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
