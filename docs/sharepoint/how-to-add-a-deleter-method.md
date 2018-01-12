---
title: 'Porady: Dodawanie metody Deleter | Dokumentacja firmy Microsoft'
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
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5e2ac47b315189dc2f0f7196db46aeb17ed08480
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-deleter-method"></a>Porady: dodawanie metody Deleter
  Aby umożliwić użytkownikowi końcowemu usunąć rekord danych z listy zewnętrznej w witrynie programu SharePoint, dodając *Deleter* metody do modelu. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-deleter-method"></a>Aby utworzyć metody Deleter  
  
1.  W Projektancie BDC wybierz jednostkę.  
  
2.  Na pasku menu wybierz **widoku**, **inne okna**, **szczegóły metody usługi łączności danych biznesowych**.  
  
     **Szczegóły metody usługi łączności danych biznesowych** zostanie otwarte okno. Aby uzyskać więcej informacji dotyczących tego okna, zobacz [omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  W **Dodaj metodę** wybierz **Utwórz metody Deleter**.  
  
     Visual Studio dodaje następujące elementy do modelu. Te elementy są wyświetlane w **szczegóły metody usługi łączności danych biznesowych** okna.  
  
    -   Metodę o nazwie **usunąć**.  
  
    -   Parametr wejściowy dla metody.  
  
    -   Deskryptor typu dla parametru.  
  
    -   Wystąpienia metody dla metody.  
  
     Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów w pliku kodu usługi, który został wygenerowany dla obiektu, a następnie wybierz **kod widoku**.  
  
     Plik kodu usługi jednostki zostanie otwarty w edytorze kodu. Aby uzyskać więcej informacji o pliku kodu usługi jednostki, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Dodaj kod do metody Deleter, aby usunąć rekord. Poniższy przykład umożliwia usunięcie elementu wiersza z zamówienia za pomocą przykładowej bazy danych AdventureWorks programu SQL Server.  
  
    > [!NOTE]  
    >  Metoda w tym przykładzie używa dwóch parametrów wejściowych.  
  
    > [!NOTE]  
    >  Zastąp wartość `ServerName` nazwę serwera.  
  
     [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Porady: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)   
 [Porady: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Porady: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Porady: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Porady: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)  
  
  