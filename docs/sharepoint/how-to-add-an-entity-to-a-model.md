---
title: 'Porady: Dodawanie jednostki do modelu | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EntityTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ec34a6f93625fdb2cb8a1e5fcc5fb5c95d17653b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-entity-to-a-model"></a>Porady: dodawanie jednostki do modelu
  Aby utworzyć jednostkę, Dodaj formant jednostki z programu Visual Studio **przybornika** do projektanta łączności danych biznesowych (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Aby dodać jednostkę do modelu  
  
1.  Tworzenie projektu usługi łączności danych biznesowych lub Otwórz istniejący projekt usługi łączności danych biznesowych. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  W **przybornika**, z **BusinessDataCatalog** pozycję Dodaj **jednostki** formantu do projektanta.  
  
     Nowa jednostka będzie wyświetlany w projektancie. Dodaje programu Visual Studio `<Entity>` — element XML w pliku modelu BDC do projektu. Aby uzyskać więcej informacji na temat atrybutów elementu jednostki, zobacz [jednostki](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  W projektancie, otwórz menu skrótów dla jednostki, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **identyfikator**.  
  
     Nowy identyfikator pojawia się na jednostce.  
  
    > [!NOTE]  
    >  Można zmienić nazwę jednostki i identyfikatorowi **właściwości** okna.  
  
4.  Definiowanie pól jednostki w klasie. Możesz dodać nową klasę w projekcie lub użyj istniejącej klasy utworzony przy użyciu innych narzędzi, takich jak Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych). W poniższym przykładzie przedstawiono klasę jednostki o nazwie kontaktu.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Porady: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Porady: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Porady: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)   
 [Instrukcje: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  