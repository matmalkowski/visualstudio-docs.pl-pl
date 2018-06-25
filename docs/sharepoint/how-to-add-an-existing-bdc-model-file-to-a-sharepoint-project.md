---
title: 'Porady: Dodawanie istniejącego modelu BDC do projektu SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8f7508cf8c66343894c16da7ff840bd275abb65c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755901"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Porady: Dodawanie istniejącego modelu BDC do projektu SharePoint
  Można dostosować, pakiet i Wdróż ponownie modelu łączności danych biznesowych (BDC) w programie Visual Studio, aby dodać plik modelu (*.bdcm*) do każdego projektu farmy programu SharePoint. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Aby dodać plik modelu BDC do projektu SharePoint  
  
1.  W **Eksploratora rozwiązań**, wybierz folder dla projektu programu SharePoint.  
  
2.  Na pasku menu wybierz **projektu** > **Dodaj istniejący element**.  
  
3.  W **Dodaj istniejący element** okno dialogowe, przejdź do lokalizacji pliku definicji modelu, który chcesz dodać do projektu, wybierz plik, a następnie wybierz **Dodaj** przycisku.  
  
     Jeśli model nie definiuje *Linia biznesowych (LOB) System typu zestawu .NET*, **zestawu .NET dodać LOB** zostanie otwarte okno dialogowe.  
  
4.  Jeśli zostanie wyświetlone okno dialogowe, wykonaj jedną z następujących czynności:  
  
    -   Aby napisać kod niestandardowy i zdefiniuj metadanych dla modelu importowany, wybierz za pomocą projektanta **tak** przycisku, nazwy systemu, a następnie wybierz **OK** przycisku.  
  
    -   W przeciwnym razie wybierz **nr** przycisk, a następnie wybierz pozycję **OK** przycisku.  
  
     **Modelu łączności danych biznesowych** element został dodany do projektu.  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Porady: Tworzenie modelu BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Porady: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Porady: Dołączanie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
 
