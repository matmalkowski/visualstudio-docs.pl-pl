---
title: 'Porady: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnienia | Dokumentacja firmy Microsoft'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58c8d74e29144a525eb33031fb98e25051d0305f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Porady: korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości oraz uprawnień
  Przy użyciu pliku zasobu, można podać zlokalizowanych nazw, definiowanie właściwości i stosować obiektów tor uprawnienia, które są zdefiniowane w modelu łączności danych biznesowych (BDC). Aby podać te informacje, należy dodać **zasobów łączności danych biznesowych** elementu do projektu, który zawiera **modelu łączności danych biznesowych** elementu. Następnie określisz nazwy, właściwości oraz uprawnienia, edytując kod XML w pliku zasobu.  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Aby dodać plik zasobów BDC do projektu SharePoint  
  
1.  W **Eksploratora rozwiązań**, rozwiń folder dla projektu programu SharePoint, a następnie wybierz folder, który zawiera model usługi łączności danych biznesowych.  
  
2.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
3.  Rozwiń węzeł **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
4.  W **Dodaj nowy element** oknie dialogowym wybierz **element zasobu usługi łączności danych biznesowych**.  
  
5.  W **nazwa** polu, określ nazwę pliku zasobu, a następnie wybierz **Dodaj** przycisku.  
  
     Plik zasobów, który ma rozszerzenie .bdcr jest dodawane do projektu i otwarte do edycji.  
  
6.  Dodaj XML do definiowania zlokalizowanych nazw, właściwości i uprawnienia, które chcesz zastosować modelu usługi łączności danych biznesowych.  
  
     Aby uzyskać informacje na temat definiowania tych elementów, zobacz [modelu i pliki zasobów](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dodawanie istniejącego modelu BDC do projektu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Porady: Tworzenie modelu BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Porady: Dołączanie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrowanie danych biznesowych z SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  