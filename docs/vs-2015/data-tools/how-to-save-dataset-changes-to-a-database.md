---
title: 'Porady: zapisywanie zmian w zestawie do bazy danych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DbDataAdapter.Update
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- databases, updating
- updating datasets, writing changes to data source
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: dbab29afdfa5dc063e6785c00796f63efba9891b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680987"
---
# <a name="how-to-save-dataset-changes-to-a-database"></a>Porady: zapisywanie zmian w zestawie danych w bazie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po danych w zestawie danych, został zmodyfikowany i zweryfikowany, prawdopodobnie chcesz wysyłać zaktualizowane dane do bazy danych. Aby można było wysłać zmodyfikowanych danych do bazy danych, należy wywołać `Update` metody [TableAdapter](../data-tools/tableadapter-overview.md) lub adapter danych. Karty `Update` metody aktualizacji jednej tabeli danych i wykonuje polecenie poprawne (INSERT, UPDATE lub DELETE) na podstawie <xref:System.Data.DataRow.RowState%2A> każdego wiersza danych w tabeli.  
  
 Podczas zapisywania danych w tabelach pokrewnych, Visual Studio zawiera składnik TableAdapterManager, które pomaga w wykonywaniu zapisuje w odpowiedniej kolejności, w oparciu o ograniczenia kluczy obcych, zdefiniowanych w bazie danych. Aby uzyskać więcej informacji, zobacz [hierarchiczna aktualizacja — Przegląd](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
>  Podjęto próbę zaktualizowania źródłem danych przy użyciu zawartości zestawu danych może powodować błędy, należy umieścić kod, który wywołuje karty `Update` metody wewnątrz `try` / `catch` bloku.  
  
 Dokładne procedurę, aby zaktualizować źródła danych mogą się różnić w zależności od potrzeb biznesowych, ale aplikacja powinna zawierać następujące czynności:  
  
1.  Wykonywanie kodu, który próbuje wysyłania aktualizacji do bazy danych w ramach `try` / `catch` bloku.  
  
2.  Jeśli wystąpił wyjątek, zlokalizuj wiersz danych, które spowodowały błąd. Aby uzyskać więcej informacji, zobacz [porady: Lokalizowanie wierszy tego błędy mają](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3.  Uzgodnij problem w danych wiersza (programowo, jeśli jest to możliwe, lub poprzez przedstawienie nieprawidłowy wiersz użytkownikowi modyfikowanie), a następnie ponownie aktualizacji (<xref:System.Data.DataRow.HasErrors%2A> właściwości <xref:System.Data.DataTable.GetErrors%2A> metody).  
  
## <a name="saving-data-to-a-database"></a>Zapisywanie danych w bazie danych  
 Wywołaj `Update` metody TableAdapter lub danych adaptera, przekazując nazwę tabeli danych, który zawiera wartości, które mają być zapisane w bazie danych. Aby uzyskać więcej informacji na temat zapisywania danych z jednej tabeli danych do bazy danych, zobacz [wskazówki: zapisywanie danych do bazy danych (Single Table)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-tableadapter"></a>Aby zaktualizować bazę danych przy użyciu zestawu danych za pomocą adaptera TableAdapter  
  
-   Ujmij `TableAdapter.Update` metody w ramach `try` / `catch` bloku. Poniższy przykład pokazuje, jak próby aktualizacji z zawartością `Customers` tabelę `NorthwindDataSet`.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-data-adapter"></a>Aby zaktualizować bazę danych przy użyciu zestawu danych za pomocą adaptera danych  
  
-   Ujmij `DataAdapter.Update` metody w ramach `try` / `catch` bloku. Poniższy przykład pokazuje, jak próby aktualizacji do źródła danych z zawartością `Table1` w `DataSet1`.  
  
     [!code-csharp[VbRaddataSaving#26](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#26)]
     [!code-vb[VbRaddataSaving#26](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#26)]  
  
## <a name="updating-two-related-tables-in-a-dataset"></a>Aktualizowanie powiązanych tabel w zestawie danych  
 Podczas aktualizowania tabelach pokrewnych w zestawie danych, należy zaktualizować w prawidłowej sekwencji, aby zmniejszyć prawdopodobieństwo naruszenie ograniczenia integralności referencyjnej. Kolejność wykonywania polecenia zostanie również wykonać indeksy <xref:System.Data.DataRowCollection> w zestawie danych. Aby zapobiec są zgłaszane błędy integralności danych, najlepszym rozwiązaniem jest można zaktualizować bazy danych w następującej kolejności:  
  
1.  Tabela podrzędna: usuwania rekordów.  
  
2.  Tabela nadrzędna: wstawianie, aktualizowanie i usuwanie rekordów.  
  
3.  Tabela podrzędna: wstawiania i aktualizowania rekordów.  
  
 Aby uzyskać szczegółowe informacje na temat zapisywania danych z wielu tabel, zobacz [zapisywanie danych w bazie danych (wiele tabel)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
 Jeśli aktualizujesz dwóch lub więcej powiązanych tabel, należy uwzględnić logika aktualizacji w obrębie transakcji. Transakcja jest procesem, który zapewnia wszystkie powiązane zmiany w bazie danych są pomyślnie przed zatwierdzeniem zmian. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-update-two-related-tables-using-a-tableadapter"></a>Aby zaktualizować powiązanych tabel, za pomocą adaptera TableAdapter  
  
1.  Tworzenie tymczasowych trzy <xref:System.Data.DataTable>s do przechowywania różnych rekordów.  
  
2.  Wywołaj `Update` metodę dla danego podzestawu wierszy z poziomu `try` / `catch` bloku. Jeśli wystąpią błędy aktualizacji, zalecane działanie jest gałęzie i ich rozwiązania.  
  
3.  Zatwierdź zmiany z zestawu danych w bazie danych.  
  
4.  Usuwanie tabel danych tymczasowych, aby zwolnić zasoby.  
  
     [!code-csharp[VbRaddataSaving#27](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#27)]
     [!code-vb[VbRaddataSaving#27](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#27)]  
  
#### <a name="to-update-two-related-tables-using-a-data-adapter"></a>Aby zaktualizować powiązanych tabel, za pomocą adaptera danych  
  
-   Wywołaj `Update` metoda każdej karty danych.  
  
     Poniższy przykład pokazuje, jak zaktualizować źródło danych przy użyciu zestawu danych, który zawiera powiązane tabele. Aby stosować się do sekwencji powyższych trzech tymczasowy <xref:System.Data.DataTable>s, zostanie utworzona w celu przechowywania różnych rekordów. A następnie `Update` metoda zostanie wywołana dla każdego podzestawu wierszy z poziomu `try` / `catch` bloku. Jeśli wystąpią błędy aktualizacji, zalecane działanie jest gałęzie i ich rozwiązania. Następnie zestaw danych zatwierdza zmiany. Na koniec usunięcia tabel danych tymczasowych, aby zwolnić zasoby.  
  
     [!code-csharp[VbRaddataSaving#28](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#28)]
     [!code-vb[VbRaddataSaving#28](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)