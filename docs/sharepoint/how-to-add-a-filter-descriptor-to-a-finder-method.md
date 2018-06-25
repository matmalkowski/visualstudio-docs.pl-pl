---
title: 'Porady: dodawanie opisu filtru do metody wyszukiwania | Dokumentacja firmy Microsoft'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 63374f4d96c86ea3eafbd4c6fa3fbe3d1f5a5899
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755602"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Porady: dodawanie opisu filtru do metody wyszukiwania
  Deskryptory filtrów umożliwiają użytkownikom modelu do przekazania wartości do metod przed ich wykonanie. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Jeden typowy scenariusz jest użytkowników w programie SharePoint chcesz pobrać wystąpienia typu zawartości zewnętrznej, które spełniają pewne kryteria. Aby obsługiwać ten scenariusz, dodawanie opisu filtru do metody wyszukiwania.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Aby dodać opisu filtru do metody wyszukiwania  
  
1.  W **szczegóły metody usługi łączności danych biznesowych** okna, rozwiń węzeł metody wyszukiwania, rozwiń **parametry** węzeł, a następnie dodaj parametr wejściowy. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  W **szczegóły metody** okna, wybierz deskryptor typu parametru.  
  
3.  Na pasku menu wybierz **widoku** > **okna właściwości**.  
  
4.  W **właściwości** ustaw **nazwy typu** dla właściwości typu danych, który jest odpowiedni dla filtru.  
  
     Na przykład filtr może użyć Data zamówienia Aby ograniczyć liczbę zamówień zwracany przez metodę. Do obsługi tego filtru **nazwy typu** musi mieć ustawioną właściwość deskryptor typu **System.DateTime**.  
  
5.  W **szczegóły metody** okna, rozwiń węzeł **deskryptory filtrów** węzła.  
  
6.  W **dodawanie opisu filtru** wybierz **Utwórz Deskryptor filtru**.  
  
     Nowy Deskryptor filtru pojawia się poniżej **deskryptory filtrów** węzła.  
  
7.  Na pasku menu wybierz **widoku** > **okna właściwości**.  
  
8.  W **właściwości** okna, wybierz **typu** właściwości.  
  
9. Na liście, które pojawiają się **typu** właściwości, filtrowania wzorzec, który chcesz wybrać.  
  
     Na przykład, aby utworzyć filtr, który używa Data zamówienia Aby ograniczyć liczbę zamówień zwracane w metody wyszukiwania, wybierz **porównanie**. Filtr porównania gwarantuje, że metody wyszukiwania zwraca tylko te wystąpienia, które spełniają określony warunek. Aby uzyskać więcej informacji o każdym wzorzec filtrowania, zobacz [typy filtrów obsługiwany przez BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. W **właściwości** okna, wybierz **skojarzony typ deskryptory** właściwości.  
  
11. Na liście, które pojawiają się **skojarzony typ deskryptory** właściwości, wybierz deskryptora typu, który został utworzony we wcześniejszej części tej procedury. Filtr odnosi się do parametru wejściowego metody wyszukiwania.  
  
12. Dodaj kod do metody wyszukiwania, która zwraca dane. Parametr wejściowy służy jako warunek w zapytania select.  
  
     Poniższy przykład zwraca zamówień sprzedaży, które mają daty określonej kolejności.  
  
    > [!NOTE]  
    >  Zastąp wartość `ServerName` nazwę serwera.  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>Zobacz także
 [Porady: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)   
 [Porady: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Porady: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Porady: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  
