---
title: 'Porady: Tworzenie modelu BDC | Dokumentacja firmy Microsoft'
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
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
ms.assetid: e8b888d4-a531-4d13-9ebf-efbbd33eebc6
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: da7bb2ea8918a0a01716ed090253af8f2f28dbbe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-bdc-model"></a>Porady: tworzenie modelu BDC
  Dla tego rodzaju elementu przy użyciu szablonu, a następnie dodając modelu do żadnego projektu programu SharePoint, można utworzyć modelu łączności danych biznesowych (BDC). Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md). Aby uzyskać więcej informacji na temat projektowania modelu, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>Aby utworzyć projekt usługi łączności danych biznesowych  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
    > [!NOTE]  
    >  Jeśli środowiskiem IDE wybrano opcję Użyj ustawienia środowiska deweloperskiego Visual Basic, wybierz **pliku**, **nowy projekt**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
2.  W obszarze albo **Visual Basic** lub **Visual C#**, wybierz **Office i SharePoint**, **rozwiązań SharePoint**.  
  
3.  W **szablony** okienku wybierz **SharePoint 2013 — pusty projekt** elementu, a następnie wybierz pozycję **OK** przycisku.  
  
     **Kreator dostosowania programu SharePoint** otwiera.  
  
4.  Na **określić poziom lokacji i zabezpieczeń dla debugowania** , podaj adres URL witryny programu SharePoint na komputerze lokalnym, wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz pozycję **Zakończ** przycisku.  
  
     Testuj modelu w określonej witrynie programu SharePoint.  
  
    > [!IMPORTANT]  
    >  Ponieważ BDC modele obsługują wyłącznie rozwiązaniami farmy, należy wdrożyć projekt jako rozwiązanie farmy.  
  
     Pusty projekt SharePoint jest tworzony.  
  
5.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
6.  W **Dodaj nowy element** oknie dialogowym wybierz **Office i SharePoint** węzła.  
  
7.  Na liście szablonów programu SharePoint, wybierz **modelu łączności danych biznesowych (farmy rozwiązania tylko)**.  
  
8.  W **nazwa** polu, określ nazwę modelu usługi łączności danych biznesowych, a następnie wybierz **Dodaj** przycisku.  
  
     A **modelu łączności danych biznesowych** element został dodany do projektu. Domyślnie model zostanie wyświetlony w Projektancie usługi łączności danych biznesowych. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Porady: Dodawanie istniejącego modelu BDC do projektu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Porady: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Porady: Dołączanie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  