---
title: 'Porady: Dodawanie pliku zasobu | Dokumentacja firmy Microsoft'
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
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 47cae5fac3ddbcbc34535176701d0293ae4f66ba
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-resource-file"></a>Porady: dodawanie pliku zasobu
  Polecenia służące do dodawania plików zasobów znajduje się w menu skrótów węzła rozwiązania, a funkcja węzłów w Eksploratorze rozwiązań. Aby uzyskać więcej informacji, zobacz [lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Aby dodać plik zasobów globalnych rozwiązania programu SharePoint  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otwórz rozwiązanie programu SharePoint.  
  
2.  W **Eksploratora rozwiązań**, wybierz węzeł projektu programu SharePoint, a następnie na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okna dialogowego wybierz **globalnego pliku zasobów** szablonu, a następnie wybierz pozycję **Dodaj** przycisku.  
  
    > [!NOTE]  
    >  Szablon elementu projektu globalnego pliku zasobów pojawi się tylko w przypadku wybrania elementu projektu SharePoint.  
  
4.  W **dodawania zasobów** oknie dialogowym Wybierz kultury dla pliku zasobów, takich jak angielski (Stany Zjednoczone).  
  
     Ten krok powoduje dodanie pliku zasobu globalnego do rozwiązania w formacie zasobów*x***.** *kultury***.** ResX, takich jak Resource1.en US.resx.  
  
5.  Gdy **Edytor zasobów** otworzy się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dodać zasoby do pliku zasobów.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Aby dodać plik zasobów funkcji do funkcji SharePoint  
  
1.  Jeśli rozwiązania programu SharePoint nie jest już otwarty w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otwórz rozwiązanie.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla nazwy funkcji w obszarze **funkcje** węzeł, a następnie wybierz pozycję **dodawania zasobów funkcji**.  
  
     Ten krok powoduje dodanie pliku zasobu do funkcji w formacie, *ResourceFileName***.** *kultury***.** ResX, takich jak Feature1.en US.resx.  
  
3.  Gdy **Edytor zasobów** otworzy się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dodać zasoby do pliku zasobów.  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  