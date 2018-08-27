---
title: 'Porady: Dodawanie pliku zasobu | Dokumentacja firmy Microsoft'
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
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3406e65ad96b93cd21890d61270c0ed989ad496c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756574"
---
# <a name="how-to-add-a-resource-file"></a>Porady: Dodawanie pliku zasobów
  Polecenia służące do dodawania plików zasobów znajduje się w menu skrótów węzła rozwiązania, a funkcja węzłów w Eksploratorze rozwiązań. Aby uzyskać więcej informacji, zobacz [rozwiązań SharePoint lokalizowanie](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Aby dodać plik zasobów globalnych rozwiązania programu SharePoint  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otwórz rozwiązanie programu SharePoint.  
  
2.  W **Eksploratora rozwiązań**, wybierz węzeł projektu programu SharePoint, a następnie na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okna dialogowego wybierz **globalnego pliku zasobów** szablonu, a następnie wybierz pozycję **Dodaj** przycisku.  
  
    > [!NOTE]  
    >  Szablon elementu projektu globalnego pliku zasobów pojawi się tylko w przypadku wybrania elementu projektu SharePoint.  
  
4.  W **dodawania zasobów** oknie dialogowym Wybierz kultury dla pliku zasobów, takich jak angielski (Stany Zjednoczone).  
  
     Ten krok powoduje dodanie pliku zasobu globalnego do rozwiązania w formacie zasobów * x ***.*** kultura ***.** ResX, takich jak *Resource1.en US.resx*.  
  
5.  Gdy **Edytor zasobów** otworzy się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dodać zasoby do pliku zasobów.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Aby dodać plik zasobów funkcji do funkcji SharePoint  
  
1.  Jeśli rozwiązania programu SharePoint nie jest już otwarty w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otwórz rozwiązanie.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla nazwy funkcji w obszarze **funkcje** węzeł, a następnie wybierz pozycję **dodawania zasobów funkcji**.  
  
     Ten krok powoduje dodanie pliku zasobu do funkcji w formacie, * ResourceFileName ***.*** kultura ***.** ResX, takich jak *Feature1.en US.resx*.  
  
3.  Gdy **Edytor zasobów** otworzy się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dodać zasoby do pliku zasobów.  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
 
