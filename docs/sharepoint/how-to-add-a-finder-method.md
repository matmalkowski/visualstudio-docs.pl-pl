---
title: 'Porady: Dodawanie metody wyszukiwania | Dokumentacja firmy Microsoft'
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
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3c7233f344282b5ce5793f7b6733e5e657534023
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756983"
---
# <a name="how-to-add-a-finder-method"></a>Porady: Dodawanie metody wyszukiwania
  Aby włączyć usługi łączności danych biznesowych (BDC) wyświetlić listę jednostek w części sieci web lub na liście, należy utworzyć *wyszukiwania* metody. Metody wyszukiwania jest specjalne metody, która zwraca kolekcję wystąpień jednostek. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Aby utworzyć metody wyszukiwania  
  
1.  Na **projektanta BDC**, wybierz jednostki.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Na pasku menu wybierz **widoku** > **inne okna** > **szczegóły metody usługi łączności danych biznesowych**.  
  
     **Szczegóły metody usługi łączności danych biznesowych** zostanie otwarte okno. Aby uzyskać więcej informacji na temat **szczegóły metody usługi łączności danych biznesowych** okna, zobacz [omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  W **Dodaj metodę** wybierz **Utwórz metody wyszukiwania**.  
  
     Visual Studio dodaje metody, parametr zwrotnego i deskryptor typu.  
  
4.  Skonfiguruj deskryptor typu jako deskryptor typu kolekcji jednostki. Aby uzyskać więcej informacji o sposobie tworzenia deskryptor typu kolekcji jednostki, zobacz [porady: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Nie trzeba wykonać ten krok, jeśli dodano określonej metody wyszukiwania do jednostki. Deskryptor typu zdefiniowanego w metody wyszukiwania korzysta z programu Visual Studio.  
  
5.  W **Eksploratora rozwiązań**, otwórz menu skrótów w pliku kodu usługi, który został wygenerowany dla obiektu, a następnie wybierz **kod widoku**. Aby uzyskać więcej informacji o pliku kodu usługi, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Dodaj kod do metody wyszukiwania. Kod będzie wykonywał następujące zadania:  
  
    -   Pobiera dane ze źródła danych.  
  
    -   Zwraca listę jednostek z usługą BDC.  
  
     Poniższy przykład zwraca zbiór `Contact` jednostek przy użyciu danych z przykładowej bazy danych AdventureWorks programu SQL Server.  
  
    > [!NOTE]  
    >  Zastąp wartość `ServerName` nazwę serwera.  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>Zobacz także
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Porady: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Porady: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Porady: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Porady: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Porady: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Porady: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)  
  
  
