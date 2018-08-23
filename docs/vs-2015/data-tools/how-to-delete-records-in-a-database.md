---
title: 'Porady: usuwanie rekordów w bazie danych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- records, deleting
- TableAdapter.Delete method
- databases, deleting records
- deleting data
- TableAdapter.Update method
- saving data
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e594a7c131d7e571a0919a9b96fa368f35cf18d7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676588"
---
# <a name="how-to-delete-records-in-a-database"></a>Porady: usuwanie rekordów znajdujących się w bazie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby usunąć rekordy z bazy danych, użyj `TableAdapter.Update` metody lub `TableAdapter.Delete` metody. Jeśli aplikacja nie korzysta z TableAdapters, można użyć obiektów poleceń do usuwania rekordów z bazy danych (na przykład <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
 `TableAdapter.Update` Metoda jest zwykle używana, gdy Twoja aplikacja używa zestawów danych do przechowywania danych, natomiast `TableAdapter.Delete` metoda jest zwykle używana, gdy aplikacja używa obiektów do przechowywania danych.  
  
 Jeśli Twoje TableAdapter nie ma `Delete` metody, oznacza to, albo Obiekt TableAdapter jest skonfigurowany do korzystania z procedur składowanych, lub jego `GenerateDBDirectMethods` właściwość jest ustawiona na `false`. Spróbuj ustawić TableAdapter `GenerateDBDirectMethods` właściwości `true` z poziomu [Projektanta obiektów Dataset](../data-tools/creating-and-editing-typed-datasets.md) , a następnie Zapisz zestaw danych, aby ponownie wygenerować TableAdapter. Jeśli nadal nie ma elementu TableAdapter `Delete` metody, a następnie tabeli prawdopodobnie nie zapewnia wystarczającą ilość informacji o schemacie rozróżnienie między poszczególnymi wierszami (na przykład, bez klucza podstawowego jest ustawiona w tabeli).  
  
## <a name="delete-records-using-tableadapters"></a>Usuwanie rekordów przy użyciu TableAdapters  
 TableAdapters zapewniają różne sposoby usuwania rekordów z bazy danych w zależności od wymagań aplikacji.  
  
 Jeśli aplikacja używa zestawów danych do przechowywania danych możesz po prostu usunąć rekordy z żądaną <xref:System.Data.DataTable> w <xref:System.Data.DataSet>, a następnie wywołaj `TableAdapter.Update` metody. `TableAdapter.Update` Metoda pobiera wszelkie zmiany w tabeli danych i wysyła te zmiany do bazy danych (w tym wstawione, zaktualizowane oraz usunięte rekordy).  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterupdate-method"></a>Do usuwania rekordów z bazy danych przy użyciu TableAdapter.Update — metoda  
  
-   Usuwanie rekordów z żądaną <xref:System.Data.DataTable> , usuwając <xref:System.Data.DataRow> obiektów z tabeli. Aby uzyskać więcej informacji, zobacz [porady: usuwanie wierszy w DataTable](http://msdn.microsoft.com/library/add481e5-08c7-4923-9276-f036ae29d31e). Po usunięciu wierszy z <xref:System.Data.DataTable>, wywołaj `TableAdapter.Update` metody. Możesz kontrolować ilość danych do aktualizacji, przekazując cały <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, tablicę <xref:System.Data.DataRow>s lub pojedynczej <xref:System.Data.DataRow>. Poniższy kod przedstawia sposób usuwania rekordu z <xref:System.Data.DataTable> , a następnie wywołać `TableAdapter.Update` metodę komunikacji zmiany i usunąć wiersz z bazy danych. (W tym przykładzie użyto bazy danych Northwind `Region` tabeli.)  
  
     [!code-csharp[VbRaddataSaving#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#20)]
     [!code-vb[VbRaddataSaving#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#20)]  
  
 Jeśli aplikacja używa obiektów do przechowywania danych w aplikacji, można użyć TableAdapter dbdirect — metody, aby usunąć dane bezpośrednio z bazy danych. Wywoływanie `Delete` metoda usuwa rekordy z bazy danych na podstawie wartości parametru przekazanego.  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterdelete-method"></a>Do usuwania rekordów z bazy danych przy użyciu TableAdapter.delete — metoda  
  
-   Wywołaj TableAdapter `Delete` jest metoda wartości dla każdej kolumny jako parametry `Delete` metody. (W tym przykładzie użyto bazy danych Northwind `Region` tabeli.)  
  
    > [!NOTE]
    >  Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz użyć.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="delete-records-using-command-objects"></a>Usuwanie rekordów przy użyciu obiektów poleceń  
 Poniższy przykład usuwa rekordy bezpośrednio z bazą danych, używając polecenia obiektów. Aby uzyskać więcej informacji na temat korzystania z obiektów poleceń do wykonania polecenia i procedur składowanych, zobacz [pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md).  
  
#### <a name="to-delete-records-from-a-database-using-command-objects"></a>Do usuwania rekordów z bazy danych przy użyciu polecenia obiektów  
  
-   Utwórz nowy obiekt polecenia, ustaw jego `Connection`, `CommandType`, i `CommandText` właściwości. (W tym przykładzie użyto bazy danych Northwind `Region` tabeli.)  
  
     [!code-csharp[VbRaddataSaving#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#22)]
     [!code-vb[VbRaddataSaving#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#22)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Musi mieć dostęp do bazy danych, z którym próbujesz nawiązać połączenie, a także uprawnienia do usuwania rekordów z tabeli, którą chcesz.  
  
## <a name="see-also"></a>Zobacz też  
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)   
 [Wstawianie nowych rekordów do bazy danych](../data-tools/insert-new-records-into-a-database.md)   
 [Porady: aktualizowanie rekordów w bazie danych](../data-tools/how-to-update-records-in-a-database.md)   
 [Zapisywanie danych z obiektu do bazy danych](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Przegląd aplikacji w programie Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)