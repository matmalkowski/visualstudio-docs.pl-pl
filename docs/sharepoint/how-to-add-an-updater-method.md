---
title: 'Porady: Dodawanie metody Updater | Dokumentacja firmy Microsoft'
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
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3004e6b83f98ccf82e6086c4669618ef4fb48c8c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755746"
---
# <a name="how-to-add-an-updater-method"></a>Porady: Dodawanie metody Updater
  Umożliwia użytkownikom zaktualizować dane biznesowe na liście programu SharePoint zewnętrznego przez utworzenie *Updater* metody. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-an-updater-method"></a>Aby utworzyć metody Updater  
  
1.  W Projektancie BDC wybierz jednostkę.  
  
2.  Na pasku menu wybierz **widoku** > **inne okna** > **szczegóły metody usługi łączności danych biznesowych**.  
  
     Zostanie otwarte okno Szczegóły metody usługi łączności danych biznesowych. Aby uzyskać więcej informacji dotyczących tego okna, zobacz [omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  W **Dodaj metodę** wybierz **Utwórz metody Updater**.  
  
     Visual Studio dodaje następujące elementy do modelu. Te elementy są wyświetlane w oknie Szczegóły metody usługi łączności danych biznesowych.  
  
    -   Metody o nazwie **aktualizacji**.  
  
    -   Parametr wejściowy dla metody.  
  
    -   Deskryptor typu dla parametru. Visual Studio korzysta domyślnie deskryptor typu jednostki zdefiniowany dla metody wyszukiwania (na przykład: Skontaktuj się z).  
  
    -   Wystąpienia metody dla metody.  
  
     Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
    > [!NOTE]  
    >  Jeśli identyfikator typu jednostki reprezentuje pola w tabeli bazy danych, który jest automatycznie generowany, ustaw **pola wstępne Updater** właściwości **True**.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów w pliku kodu usługi, który został wygenerowany dla obiektu, a następnie wybierz **kod widoku**.  
  
     Otworzy się w pliku kodu usługi jednostki **edytora kodu**. Aby uzyskać więcej informacji dotyczących tego pliku, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Dodaj kod do metody aktualizacji w celu aktualizacji danych. Poniższy przykład aktualizuje informacje o kontakt w przykładowej bazie danych AdventureWorks programu SQL Server.  
  
    > [!NOTE]  
    >  Zastąp wartość `ServerName` nazwę serwera.  
  
     [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>Zobacz także
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Porady: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)   
 [Porady: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Porady: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Porady: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Porady: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Porady: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Porady: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)  
  
 
