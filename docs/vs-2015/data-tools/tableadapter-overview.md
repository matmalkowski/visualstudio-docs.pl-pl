---
title: TableAdapter — Przegląd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DataAccessor
- vbdata.Microsoft.VSDesigner.DataSource.DataAccessor
- TableAdapter
- vs.data.TableAdapter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], table adapters
- TableAdapters, queries
- data [Visual Studio], TableAdapters
- query data in Visual Studio
- TableAdapter.GetData
- TableAdapter.Fill
- data [Visual Studio], datasets
- TableAdapters
- table adapters
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1d5aabd4892011aa5c59abafc5d08840d1c8f5a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684058"
---
# <a name="tableadapter-overview"></a>TableAdapter — Przegląd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapters są wygenerowany przez projektanta składników, które połączenie z bazą danych, wykonywania zapytań lub procedur przechowywanych i wypełnienie ich DataTable zwracanych danych. TableAdapters są również używane do wysyłania zaktualizowanych danych z aplikacji w bazie danych. Może mieć dowolną liczbę zapytań dowolną w metodzie TableAdapter tak długo, jak zwracają danych, który jest zgodny schemat tabeli, z którym jest skojarzona TableAdapter. Na poniższym diagramie przedstawiono, jak TableAdapters wchodzić w interakcje z bazami danych i innych obiektów w pamięci:  
  
 ![Przepływ danych w aplikacji klienckiej](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Gdy TableAdapters są skonstruowane z **Projektanta obiektów Dataset**, wygenerowane klasy TableAdapter nie są generowane jako klas zagnieżdżonych <xref:System.Data.DataSet>. Znajdują się one w oddzielnych przestrzeni nazw specyficzne dla każdego zestawu danych. Na przykład, jeśli masz zestaw danych o nazwie `NorthwindDataSet`, skojarzonych elementów TableAdapter <xref:System.Data.DataTable>s w `NorthwindDataSet` będą miały `NorthwindDataSetTableAdapters` przestrzeni nazw. Aby uzyskać dostęp do określonego TableAdapter programowo, należy zadeklarować nowe wystąpienie klasy TableAdapter. Na przykład:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>Skojarzonego schematu elementu DataTable  
 Podczas tworzenia TableAdapter, początkowego zapytania lub procedura składowana służy do definiowania schematu TableAdapter skojarzonej <xref:System.Data.DataTable>. Wykonanie tego początkowego zapytania lub procedury składowanej przez wywołanie metody TableAdapter `Fill` — metoda (która wypełnia TableAdapter skojarzonej <xref:System.Data.DataTable>). Wszelkie zmiany wprowadzone do zapytanietableadapter główne są odzwierciedlane w schemat tabeli powiązane dane. Na przykład usunięcie kolumny z głównego zapytania usuwa kolumnę z tabeli powiązane dane. Użycie instrukcji języka SQL, zwracając kolumn, które nie znajdują się w głównym zapytania, wszelkie dodatkowe zapytania w metodzie TableAdapter projektanta będzie podejmować próby synchronizować zmiany kolumny między główne zapytanie i wszelkie dodatkowe zapytania. Aby uzyskać więcej informacji, zobacz [porady: edytowanie TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>Polecenia aktualizacji TableAdapter  
 Funkcja aktualizacji TableAdapter jest zależy od tego, ile informacji znajduje się na podstawie głównego zapytania, które podano w Kreatorze TableAdapter. Na przykład adapterów TableAdapter, które są skonfigurowane do pobierania wartości z wielu tabel (sprzężenia), wartości skalarnych, widokach lub wyniki funkcji agregujących nie są wstępnie utworzone za pomocą możliwość wysyłania aktualizacji do podstawowej bazy danych. Jednak należy skonfigurować ręcznie w poleceń INSERT, UPDATE i DELETE **właściwości** okna.  
  
## <a name="tableadapter-queries"></a>Zapytań TableAdapter  
 ![TableAdapter z wieloma zapytaniami](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 TableAdapters może zawierać wiele zapytań do wypełnienia ich tabele powiązane dane. Można zdefiniować dowolną liczbę zapytań dotyczących TableAdapter wymaga aplikacji, tak długo, jak każda kwerenda zwraca dane, który jest zgodny do tego samego schematu jako jej skojarzone dane tabeli. Dzięki temu podczas ładowania danych, który spełnia kryteria zróżnicowane. Na przykład jeśli aplikacja zawiera tabelę klientów, można utworzyć zapytanie, które wypełnia tabelę z każdego klienta, którego nazwa zaczyna się od określonej litery i inne zapytanie, które wypełnia tabelę wszystkich klientów znajdujących się w tym samym stanie. Do wypełnienia `Customers` tabeli z klientami w danym stanie, możesz utworzyć `FillByState` zapytanie, które przyjmuje parametr dla wartości stanu: `SELECT * FROM Customers WHERE State = @State`. Wykonaj zapytanie, wywołując `FillByState` metody i przekazywanie w wartości parametru podobnie do następującego: `CustomerTableAdapter.FillByState("WA")`. Aby uzyskać więcej informacji, zobacz [porady: tworzenie zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
 Oprócz zapytań, które zwracają dane tego samego schematu jako tabela danych TableAdapter można dodać zapytania, które zwracają wartości skalarnych (pojedynczą). Na przykład tworzenia kwerendy, która zwraca liczbę klientów (`SELECT Count(*) From Customers`) jest nieprawidłowa dla `CustomersTableAdapter` nawet, jeśli dane zwrócone, nie jest zgodny ze schematem tabeli.  
  
## <a name="clearbeforefill-property"></a>Właściwość ClearBeforeFill  
 Domyślnie za każdym razem, gdy wykonywania zapytania w celu wypełnienia tabeli danych TableAdapter danych jest wyczyszczone, a tylko wyniki zapytania są ładowane do tabeli. Ustaw TableAdapter `ClearBeforeFill` właściwość `false` Jeśli chcesz dodać lub scalić dane zwrócone w wyniku zapytania do istniejących danych w tabeli danych. Niezależnie od tego, czy możesz wyczyścić dane Musisz jawnie wysyłania aktualizacji w bazie danych, w razie potrzeby. Dlatego pamiętaj, aby zapisać zmiany wprowadzone przed wykonaniem inne zapytanie, które wypełnia tabelę danych w tabeli. Aby uzyskać więcej informacji, zobacz [aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>Dziedziczenie TableAdapter  
 TableAdapters rozszerzają funkcjonalność kart danych w warstwie standardowa poprzez hermetyzację skonfigurowanego <xref:System.Data.Common.DataAdapter>. Domyślnie, dziedziczy TableAdapter <xref:System.ComponentModel.Component> i nie można rzutować <xref:System.Data.Common.DataAdapter> klasy. Rzutowanie TableAdapter do <xref:System.Data.Common.DataAdapter> skutkuje <xref:System.InvalidCastException>. Aby zmienić klasę bazową klasy TableAdapter, możesz wpisać klasę, która pochodzi od klasy <xref:System.ComponentModel.Component> w **klasy bazowej** właściwość obiektu TableAdapter w **Projektanta obiektów Dataset**.  
  
## <a name="tableadapter-methods-and-properties"></a>Właściwości i metody TableAdapter  
 Klasa TableAdapter nie jest częścią [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], i jako takie można nie można go wyszukać w dokumentacji lub **przeglądarki obiektów**. Jest on tworzony w czasie projektowania, używając jednego z kreatorów wymienionych powyżej. Nazwa przypisana do TableAdapter, podczas jego tworzenia opiera się na nazwę tabeli, którą pracujesz. Na przykład, gdy tworzenie TableAdapter na podstawie tabeli w bazie danych o nazwie `Orders`, będą miały postać TableAdapter `OrdersTableAdapter`. Nazwa klasy TableAdapter można zmienić za pomocą **nazwa** właściwość **Projektanta obiektów Dataset**.  
  
 Poniżej przedstawiono najczęściej używanych metod i właściwości działania TableAdapters:  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`TableAdapter.Fill`|Wypełnia TableAdapter skojarzone dane tabeli z wynikami polecenia SELECT TableAdapter. Aby uzyskać więcej informacji, zobacz [porady: wypełnianie zestawu danych danymi](../data-tools/how-to-fill-a-dataset-with-data.md).|  
|`TableAdapter.Update`|Wysyła zmiany w bazie danych i zwraca liczbę całkowitą reprezentującą liczbę wierszy, aktualizacja dotyczy. Aby uzyskać więcej informacji, zobacz [aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Zwraca nowy <xref:System.Data.DataTable> wypełniany danymi.|  
|`TableAdapter.Insert`|Tworzy nowy wiersz w tabeli danych. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie wierszy do DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).|  
|`TableAdapter.ClearBeforeFill`|Określa, czy tabela danych jest opróżniany przed wywołaniem jednego z `Fill` metody.|  
  
## <a name="tableadapter-update-method"></a>Metody TableAdapter aktualizacji  
 TableAdapters polecenia danych do odczytu i zapisu z bazy danych. TableAdapter w początkowej `Fill` zapytania (główną) jest używany jako podstawa do tworzenia schemat tabeli powiązane dane, jak również `InsertCommand`, `UpdateCommand`, i `DeleteCommand` poleceń związanych z `TableAdapter.Update` metody. Oznacza to, że wywołanie TableAdapter `Update` metoda wykonuje instrukcje tworzonych podczas TableAdapter pierwotnie został skonfigurowany, a nie jednego z zapytań dodatkowe dodany z **KreatorakonfiguracjizapytańTableAdapter**.  
  
 Używając TableAdapter skutecznie wykonuje te same operacje za pomocą poleceń, które zazwyczaj będzie wykonywać. Na przykład gdy wywołujesz karty `Fill` metody, karta wykonuje polecenie danych w jego `SelectCommand` właściwości i używa czytnik danych (na przykład <xref:System.Data.SqlClient.SqlDataReader>) można załadować zestawu wyników do tabeli danych. Podobnie, gdy zostanie wywołana karty `Update` metody wykonuje odpowiednie polecenie (w `UpdateCommand`, `InsertCommand`, i `DeleteCommand` właściwości) dla każdej zmianie rekordu w tabeli danych.  
  
> [!NOTE]
>  Jeśli ma wystarczającej ilości informacji w głównym zapytaniu `InsertCommand`, `UpdateCommand`, i `DeleteCommand` poleceń są domyślnie tworzone po wygenerowaniu TableAdapter. Jeśli TableAdapter główne zapytanie jest więcej niż jednej tabeli instrukcji SELECT, jest możliwe, Projektant nie będzie mógł wygenerować `InsertCommand`, `UpdateCommand`, i `DeleteCommand`. Jeśli te polecenia nie są generowane, może wystąpić błąd podczas wykonywania `TableAdapter.Update` metody.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 Oprócz `InsertCommand`, `UpdateCommand`, i `DeleteCommand`, TableAdapters są tworzone za pomocą metod, które mogą być wykonywane bezpośrednio w bazie danych. Te metody (`TableAdapter.Insert`, `TableAdapter.Update`, i `TableAdapter.Delete`) może być wywoływany bezpośrednio do manipulowania danymi w bazie danych. Oznacza to, że może wywoływać te poszczególne metody w kodzie zamiast wywoływania TableAdapter.Update — do obsługi operacji wstawiania, aktualizacji i usuwa oczekujące dla tabeli powiązane dane.  
  
 Jeśli nie chcesz utworzyć te metody bezpośrednie, ustaw TableAdapter **GenerateDbDirectMethods** właściwości `false` (w **właściwości** okno). Dodatkowe zapytania dodane do elementu TableAdapter są autonomiczne zapytań — nie generują one tych metod.  
  
## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter obsługę typów dopuszczających wartości zerowe  
 Elementów TableAdapter obsługuje typy dopuszczające wartości zerowe `Nullable(Of T)` i `T?`. Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku Visual Basic, zobacz [typów wartości dopuszczających wartości zerowe](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku C#, zobacz [przy użyciu typów dopuszczających wartości zerowe](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Porady: łączenie z danymi w bazie danych](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Wskazówki: Łączenie z danymi w bazie danych (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)