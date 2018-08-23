---
title: 'Porady: aktualizowanie rekordów w bazie danych | Dokumentacja firmy Microsoft'
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
- records, updating
- data [Visual Studio], saving
- records, editing
- databases, updating
- TableAdapter.Update method
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 73ca33f9fb30a178addab6dee136d3b441bd81d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628698"
---
# <a name="how-to-update-records-in-a-database"></a>Porady: aktualizacja rekordów w bazie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć `TableAdapter.Update` metodę, aby aktualizować (edytować) rekordy w bazie danych. `TableAdapter.Update` Metoda zapewnia kilka przeciążeń, które wykonują różne operacje, w zależności od przekazane parametry. Należy zrozumieć wyników wywołania tymi podpisami innej metody.  
  
> [!NOTE]
>  Jeśli aplikacja nie używają adapterów tabel, a następnie obiekty poleceń służy do aktualizowania rekordów w bazie danych (na przykład <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>). Aby uzyskać więcej informacji na temat aktualizowania danych o obiektach poleceń poniżej "Przy użyciu polecenia obiektów rekordy Update".  
  
 W poniższej tabeli opisano różne zachowanie `TableAdapter.Update` metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|Próbuje zapisać wszystkie zmiany w <xref:System.Data.DataTable> w bazie danych. (Obejmuje to usunięcie wszystkich wierszy usunięty z tabeli, dodając wiersze wstawione do tabeli i aktualizowanie wierszy w tabeli, które uległy zmianie.)|  
|`TableAdapter.Update(DataSet)`|Mimo że parametr pobiera zestaw danych, skojarzonej z prób TableAdapter, aby zapisać wszystkie zmiany w metodzie TableAdapter <xref:System.Data.DataTable> w bazie danych. (Obejmuje to usunięcie wszystkich wierszy usunięty z tabeli, dodając wiersze wstawione w tabeli i aktualizowanie wierszy w tabeli, które uległy zmianie.) **Uwaga:** skojarzonej TableAdapter <xref:System.Data.DataTable> jest <xref:System.Data.DataTable> utworzone podczas konfigurowania pierwotnie TableAdapter.|  
|`TableAdapter.Update(DataRow)`|Próbuje zapisać zmiany w wskazany <xref:System.Data.DataRow> w bazie danych.|  
|`TableAdapter.Update(DataRows())`|Próbuje zapisać zmiany w dowolnym wierszu w tablicy <xref:System.Data.DataRow>s do bazy danych.|  
|`TableAdapter.Update("new column values", "original column values")`|Próbuje zapisać zmiany w jednym wierszu, identyfikowany przez oryginalne wartości kolumny.|  
  
 Zazwyczaj używa się `TableAdapter.Update` metody, która przyjmuje <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow>(s), gdy Twoja aplikacja używa zestawów danych wyłącznie do przechowywania danych.  
  
 Zazwyczaj używa się `TableAdapter.Update` metody, która przyjmuje wartości w kolumnie, jeśli aplikacja używa obiektów do przechowywania danych.  
  
 Jeśli Twoje TableAdapter nie ma `Update` metody, która przyjmuje wartości kolumn, oznacza to, że albo Obiekt TableAdapter jest skonfigurowany do używania procedur składowanych lub jego `GenerateDBDirectMethods` właściwość jest ustawiona na `false`. Spróbuj ustawić TableAdapter `GenerateDBDirectMethods` właściwości `true` z poziomu [Projektanta obiektów Dataset](../data-tools/creating-and-editing-typed-datasets.md) , a następnie Zapisz zestaw danych, aby ponownie wygenerować TableAdapter. Jeśli nadal nie ma elementu TableAdapter `Update` metody, która przyjmuje wartości w kolumnie, a następnie tabeli, prawdopodobnie nie zapewnia wystarczającą ilość informacji o schemacie rozróżnienie między poszczególnymi wierszami (na przykład, bez klucza podstawowego jest ustawiona w tabeli).  
  
## <a name="update-existing-records-using-tableadapters"></a>Aktualizowanie istniejących rekordów za pomocą adapterów TableAdapter  
 TableAdapters zapewniają różne sposoby, aby zaktualizować rekordy w bazie danych, w zależności od wymagań aplikacji.  
  
 Jeśli aplikacja używa zestawów danych do przechowywania danych, a następnie po prostu można zaktualizować rekordy w żądany <xref:System.Data.DataTable> , a następnie wywołać `TableAdapter.Update` metody i przekazać albo <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, tablica lub <xref:System.Data.DataRow>s. Powyższej tabeli opisano poszczególne `Update` metody.  
  
#### <a name="to-update-records-in-a-database-with-the-tableadapterupdate-method-that-takes-dataset-datatable-datarow-or-datarows"></a>Aby zaktualizować rekordy w bazie danych przy użyciu TableAdapter.Update — metoda, która przyjmuje DataSet, DataTable, DataRow lub DataRows()  
  
1.  Może edytować rekordy w żądany <xref:System.Data.DataTable> przez bezpośrednią edycję <xref:System.Data.DataRow> w <xref:System.Data.DataTable>. Aby uzyskać więcej informacji, zobacz [porady: edytowanie wierszy w DataTable](http://msdn.microsoft.com/library/d5eea200-9bfa-4956-bf7c-08dd6fb6663c).  
  
2.  Po edycji wiersze <xref:System.Data.DataTable>, wywołaj `TableAdapter.Update` metody. Możesz kontrolować ilość danych, które można zaktualizować przez przekazanie albo cały <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, tablicę <xref:System.Data.DataRow>s lub pojedynczej <xref:System.Data.DataRow>.  
  
     Poniższy kod przedstawia sposób edytowania rekordu w <xref:System.Data.DataTable> , a następnie wywołać `TableAdapter.Update` metodę, aby zapisać zmiany w bazie danych. (W tym przykładzie użyto tabeli Region bazy danych Northwind.)  
  
     [!code-csharp[VbRaddataSaving#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#17)]
     [!code-vb[VbRaddataSaving#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#17)]  
  
 Jeśli aplikacja używa obiektów do przechowywania danych w aplikacji, możesz użyć TableAdapter `DBDirect` metody służące do wysyłania danych z obiektów bezpośrednio do bazy danych. Te metody umożliwiają poszczególne wartości dla każdej kolumny są przekazywane jako parametry metody. Wywołanie tej metody aktualizuje istniejący rekord w bazie danych przy użyciu wartości kolumn, przekazana do metody.  
  
 W poniższej procedurze użyto Northwind `Region` tabeli jako przykład.  
  
#### <a name="to-update-records-in-a-database-using-the-tableadapterupdate-method-that-takes-column-values"></a>Do aktualizowania rekordów w bazie danych przy użyciu TableAdapter.Update — metoda, która przyjmuje wartości w kolumnie  
  
-   Wywołaj TableAdapter `Update` jest metoda nowymi i oryginalnymi wartości dla każdej kolumny jako parametry.  
  
    > [!NOTE]
    >  Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz użyć.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
## <a name="update-records-using-command-objects"></a>Aktualizowanie rekordów przy użyciu obiektów poleceń  
 Poniższy przykład aktualizuje istniejące rekordy bezpośrednio w bazie danych przy użyciu polecenia obiektów. Aby uzyskać więcej informacji na temat korzystania z obiektów poleceń do wykonania polecenia i procedur składowanych, zobacz [pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md).  
  
 W poniższej procedurze użyto Northwind `Region` tabeli jako przykład.  
  
#### <a name="to-update-existing-records-in-a-database-using-command-objects"></a>Aby zaktualizować istniejące rekordy w bazie danych przy użyciu polecenia obiektów  
  
-   Utwórz nowy obiekt polecenia; Ustaw jego `Connection`, `CommandType`, i `CommandText` właściwości, a następnie otwórz połączenie i wykonaj polecenie.  
  
     [!code-csharp[VbRaddataSaving#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#19)]
     [!code-vb[VbRaddataSaving#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#19)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Musi mieć dostęp do bazy danych, z którym próbujesz nawiązać połączenie, a także uprawnienia do aktualizowania rekordów w tabeli, którą chcesz.  
  
## <a name="see-also"></a>Zobacz też  
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)   
 [Porady: usuwanie rekordów w bazie danych](../data-tools/how-to-delete-records-in-a-database.md)   
 [Wstawianie nowych rekordów do bazy danych](../data-tools/insert-new-records-into-a-database.md)   
 [Zapisywanie danych z obiektu do bazy danych](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Przegląd aplikacji w programie Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)