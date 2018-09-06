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
ms.openlocfilehash: f06c26f2f274615058c46ecd45a6d73757b78db9
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43774797"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Porady: edytowanie konfiguracji wdrażania SharePoint
  Można utworzyć konfiguracji wdrożenia lub Modyfikuj istniejącą konfigurację wdrożenia. Na przykład możesz uruchomić jednym kroku lub zmiana kolejności kroków w procesie wdrażania. Można tworzyć lub modyfikować konfiguracje wdrożenia, ponieważ nie można zmienić konfiguracji programowo dodanych i wbudowane.  
  
## <a name="create-a-sharepoint-deployment-configuration"></a>Tworzenie konfiguracji wdrażania SharePoint  
  
#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Aby utworzyć konfiguracji wdrażania SharePoint  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt programu SharePoint, a następnie na pasku menu wybierz **projektu**, _ProjectName_**właściwości**.  
  
2.  Na **SharePoint** kartę, wybrać **New** przycisku.  
  
     **Dodawanie nowej konfiguracji wdrożenia** pojawi się okno dialogowe.  
  
3.  W **nazwa** tekstu wprowadź nazwę dla konfiguracji wdrażania.  
  
4.  W **dostępne kroki związane z wdrażaniem** okienku wybierz kroki, które chcesz dodać do konfiguracji wdrożenia, wybierz (**>**) przycisk, a następnie wybierz **OK** przycisku.  
  
    > [!NOTE]  
    >  Po skonfigurowaniu polecenia przed wdrożeniem lub polecenia po wdrożeniu te kroki uruchamiane tylko wtedy, gdy należy dodać je do konfiguracji wdrożenia dostosowane.  
  
## <a name="change-the-active-deployment-configuration"></a>Zmiana konfiguracji aktywnego wdrożenia  
  
#### <a name="to-change-the-active-deployment-configuration"></a>Zmiana konfiguracji aktywnego wdrożenia  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt programu SharePoint, a następnie na pasku menu wybierz **projektu** > **\<*ProjectName*> Właściwości**.  
  
2.  Wybierz **SharePoint** kartę.  
  
3.  W **aktywnej konfiguracji wdrożenia** pola listy, wybierz nazwę konfiguracji wdrożenia, którego chcesz używać.  
  
## <a name="see-also"></a>Zobacz także
 [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
