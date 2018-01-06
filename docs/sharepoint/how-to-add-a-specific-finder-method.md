---
title: 'Porady: Dodawanie metody wyszukiwania | Dokumentacja firmy Microsoft'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6a5dbff1d4a4c739ce8ecab0807e2d74c62f999e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-specific-finder-method"></a>Porady: dodawanie określonej metody wyszukiwania
  Można zwrócić wystąpienia pojedynczej jednostki, tworząc *określonej metody wyszukiwania* metody. Usługa łączności danych biznesowych (BDC) wykonuje metody wyszukiwania po wybraniu jednostki w części sieci web danych biznesowych lub listy zewnętrznej. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-specific-finder-method"></a>Aby utworzyć określonej metody wyszukiwania  
  
1.  W Projektancie BDC wybierz jednostkę.  
  
     Aby uzyskać informacje na temat dodać jednostkę do projektanta usługi łączności danych biznesowych w programie Visual Studio, zobacz [porady: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Na pasku menu wybierz **widoku**, **inne okna**, **szczegóły metody usługi łączności danych biznesowych**.  
  
     **Szczegóły metody usługi łączności danych biznesowych** zostanie otwarte okno. Aby uzyskać więcej informacji dotyczących tego okna, zobacz [omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  W **Dodaj metodę** wybierz **utworzyć określonej metody wyszukiwania**.  
  
     Visual Studio dodaje następujące elementy do modelu. Te elementy są wyświetlane w **szczegóły metody usługi łączności danych biznesowych** okna.  
  
    -   Metoda.  
  
    -   Parametr wejściowy dla metody.  
  
    -   Parametr zwrotnego dla metody.  
  
    -   Deskryptor typu dla każdego parametru.  
  
    -   Wystąpienia metody dla metody.  
  
     Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Otwórz program Visual Studio **właściwości** okna.  
  
5.  Skonfiguruj deskryptora typu dla parametru zwrotnego jako deskryptor typu jednostki. Aby uzyskać informacje o sposobie tworzenia deskryptor typu jednostki, zobacz [porady: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Nie masz wykonać ten krok, jeśli dodano metody wyszukiwania do jednostki. Deskryptor typu zdefiniowanego w Finder — metoda korzysta z programu Visual Studio.  
  
    > [!NOTE]  
    >  Jeśli pole identyfikatora typu jednostki reprezentuje pola w tabeli bazy danych, który jest automatycznie generowany, ustaw **tylko do odczytu** właściwości pola Identyfikator **True**.  
  
6.  W **szczegóły metody** okna, wybierz wystąpienie metody metody.  
  
7.  W **okna właściwości**ustaw **zwraca nazwę parametru** właściwość na nazwę zwracanego parametru metody. Aby uzyskać więcej informacji o właściwościach wystąpienia metody, zobacz [wystąpienia metody](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8.  W **Eksploratora rozwiązań**, otwórz menu skrótów w pliku kodu usługi, który został wygenerowany dla obiektu, a następnie wybierz **kod widoku**.  
  
     Plik kodu usługi jednostki zostanie otwarty w edytorze kodu. Aby uzyskać więcej informacji o pliku kodu usługi jednostki, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Dodaj kod do metody wyszukiwania. Kod będzie wykonywał następujące zadania:  
  
    -   Pobiera rekord ze źródła danych.  
  
    -   Zwraca jednostkę do usługi BDC.  
  
     Poniższy przykład zwraca kontaktu z przykładowej bazy danych AdventureWorks programu SQL Server.  
  
    > [!NOTE]  
    >  Zastąp wartość `ServerName` nazwę serwera.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Porady: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)   
 [Porady: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Porady: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Porady: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Porady: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)  
  
  