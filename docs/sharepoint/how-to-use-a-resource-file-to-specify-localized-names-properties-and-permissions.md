---
title: "Porady: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnienia | Dokumentacja firmy Microsoft"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
ms.assetid: 72bb744d-818b-4e5a-9da2-295412025680
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a8b61477ae3b588b2aeadf1c9d99618151825f8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  