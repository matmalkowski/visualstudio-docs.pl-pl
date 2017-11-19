---
title: "Wypełnianie zbiorów danych przy użyciu TableAdapters | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f93a0d11435a060806a89db48b2c9e81efebe3f3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="fill-datasets-by-using-tableadapters"></a>Wypełnianie zbiorów danych przy użyciu TableAdapters
Składnik TableAdapter wypełnia zestawu danych danymi z bazy danych, na podstawie co najmniej jednego zapytania lub procedur składowanych, które określisz. TableAdapters można również wykonywać dodawania, aktualizacji i usuwania bazy danych, aby zachować zmiany wprowadzone do zestawu danych. Można również wydać polecenia globalne, które nie są związane z żadną z tabel.  
  
> [!NOTE]
>  TableAdapters są generowane przez projektantów Visual Studio. Jeśli programowe tworzenie zestawów danych, użyj DataAdapter jest klasą .NET Framework.  
  
 Aby uzyskać szczegółowe informacje o operacjach TableAdapter możesz pominąć bezpośrednio do jednej z poniższych tematów:  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Tworzenie i konfigurowanie TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Jak używać projektantów do tworzenia i konfigurowania TableAdapters|  
|[Tworzenie parametrycznych zapytań TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Jak użytkownicy mogą podać argumenty procedur TableAdapter lub zapytania|  
|[Bezpośredni dostęp do bazy danych za pomocą TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Sposób użycia metody Dbdirect TableAdapters|  
|[Wyłączanie ograniczeń w czasie wypełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Jak pracować z ograniczenia foreign key podczas aktualizowania danych|  
|[Jak rozszerzanie funkcjonalności TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Jak dodać niestandardowego kodu do TableAdapters|  
|[Odczytywanie danych XML do zestawu danych](../data-tools/read-xml-data-into-a-dataset.md)|Jak pracować z XML|  
  
<a name="tableadapter-overview"></a>  
  
## <a name="tableadapter-overview"></a>TableAdapter — Przegląd  
 TableAdapters są wygenerowany przez projektanta składników nawiązać połączenia z bazą danych, wykonywania kwerend lub procedur składowanych, które wypełnienie ich DataTable zwróconych danych. TableAdapters również wysyłać zaktualizowane dane z aplikacji w bazie danych. Można uruchomić dowolną liczbę zapytania można dowolnie w metodzie TableAdapter tak długo, jak zwracają dane były zgodne ze schematem tabeli, z którym skojarzony jest TableAdapter. Na poniższym diagramie przedstawiono sposób TableAdapters interakcji z baz danych i innych obiektów w pamięci:  
  
 ![Przepływ danych w aplikacji klienckiej](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Gdy TableAdapters zostały zaprojektowane z **Projektant obiektów Dataset**, nie zostały wygenerowane klasy TableAdapter jako zagnieżdżonych klas <xref:System.Data.DataSet>. Znajdują się one w oddzielnych przestrzeniach nazw, które są specyficzne dla każdego zestawu danych. Na przykład, jeśli masz zestawu danych o nazwie `NorthwindDataSet`, TableAdapters, które są skojarzone z <xref:System.Data.DataTable>s w `NorthwindDataSet` w `NorthwindDataSetTableAdapters` przestrzeni nazw. Aby uzyskać dostęp do konkretnej TableAdapter programowo, należy zadeklarować nowe wystąpienie klasy TableAdapter. Na przykład:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
 [!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]  
  
## <a name="associated-datatable-schema"></a>Skojarzony schemat DataTable  
 Gdy utworzysz TableAdapter, użyj początkowego zapytania lub skojarzonym procedury składowanej do definiowania schematu TableAdapter <xref:System.Data.DataTable>. Uruchom to zapytanie początkowej lub procedury składowanej przez wywołanie metody TableAdapter `Fill` — metoda (która wypełnia TableAdapter powiązanych <xref:System.Data.DataTable>). Wszelkie zmiany wprowadzone w głównym zapytaniu TableAdapter są odzwierciedlane w schemat tabeli skojarzonych danych. Na przykład usunięcie kolumny z główne zapytanie spowoduje również usunięcie kolumny z tabeli skojarzonych danych. Użycie instrukcji SQL, które zwracają kolumn, które nie znajdują się w głównym zapytaniu, żadnych dodatkowych zapytań w TableAdapter projektanta próbuje przeprowadzić synchronizację zmian kolumny między zapytań głównych i dodatkowych zapytań. 
  
## <a name="tableadapter-update-commands"></a>Polecenia aktualizacji TableAdapter  
 Funkcja aktualizacji TableAdapter jest zależne od tego, ile informacje są dostępne w głównym zapytaniu w Kreatorze TableAdapter. Na przykład TableAdapters skonfigurowanych do pobierania wartości z wielu tabel (sprzężenia), wartości skalarnych, widoki lub wyniki funkcje agregujące nie są początkowo tworzone umożliwia wysyłanie aktualizacji z powrotem do podstawowej bazy danych. Jednak należy skonfigurować ręcznie w polecenia INSERT, UPDATE i DELETE **właściwości** okna.  
  
## <a name="tableadapter-queries"></a>TableAdapter— Zapytania  
 ![TableAdapter z wieloma zapytaniami](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 TableAdapters może zawierać wielu zapytań do wypełnienia tabel ich skojarzonych danych. Można zdefiniować tyle zapytania dotyczące TableAdapter wymaga aplikacji, tak długo, jak każda kwerenda zwraca dane, zgodne do tego samego schematu jako jego tabeli skojarzone dane. Ta funkcja umożliwia TableAdapter załadować różne wyniki na podstawie różnych kryteriów.  
  
 Na przykład jeśli aplikacja zawiera tabelę z nazwy klientów, można utworzyć kwerendę, która wypełnia tabelę przy użyciu nazwy każdego odbiorcy, która rozpoczyna się od określonej litery, a druga które wypełnia tabelę z wszystkich klientów, które znajdują się w tym samym stanie. Aby wypełnić `Customers` tabeli z klientami w danym stanie, można utworzyć `FillByState` kwerendę, która przyjmuje parametr dla wartości stanu w następujący sposób: `SELECT * FROM Customers WHERE State = @State`. Uruchom zapytanie, wywołując `FillByState` — metoda i przekazywanie wartości parametru, takie jak to: `CustomerTableAdapter.FillByState("WA")`.  
  
 Oprócz dodania zapytań, które zwracają dane tego samego schematu jako element TableAdapter tabeli danych, można dodać zapytania, które zwracają wartości skalarnych (jeden). Na przykład zapytanie zwracające liczbę klientów (`SELECT Count(*) From Customers`) jest nieprawidłowa dla `CustomersTableAdapter,` mimo że zwrócone dane są niezgodne schemat tabeli.  
  
## <a name="clearbeforefill-property"></a>Właściwość ClearBeforeFill  
 Domyślnie każdym uruchomieniu zapytanie w celu wypełnienia tabeli danych TableAdapter istniejące dane są usuwane, a tylko wyniki zapytania są ładowane do tabeli. Ustaw element TableAdapter `ClearBeforeFill` właściwości `false` Jeśli chcesz dodać lub scalanie danych, która jest zwracana w wyniku zapytania do istniejących danych w tabeli danych. Niezależnie od tego, czy możesz wyczyścić dane Musisz jawnie wysyłanie aktualizacji w bazie danych, jeśli chcesz utrwalić je. Dlatego pamiętaj, aby zapisać zmiany danych w tabeli przed uruchomieniem innego zapytania, które wypełnia tabelę. Aby uzyskać więcej informacji, zobacz [aktualizowanie danych za pomocą TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>Dziedziczenie TableAdapter  
 TableAdapters rozszerzanie funkcjonalności danych standardowych kart hermetyzując skonfigurowany <xref:System.Data.Common.DataAdapter> klasy. Domyślnie dziedziczy TableAdapter <xref:System.ComponentModel.Component> klasy i nie można rzutować na <xref:System.Data.Common.DataAdapter> klasy. Rzutowanie TableAdapter do <xref:System.Data.Common.DataAdapter> klasy powoduje <xref:System.InvalidCastException> błędu. Aby zmienić klasy podstawowej TableAdapter, można określić klasę, która jest pochodną <xref:System.ComponentModel.Component> w **klasy podstawowej** właściwości TableAdapter w **Projektant obiektów Dataset**.  
  
## <a name="tableadapter-methods-and-properties"></a>Właściwości i metody TableAdapter  
 Klasa TableAdapter nie jest częścią [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Oznacza to, że nie można go odszukać w dokumentacji lub **przeglądarki obiektów**. Jest on tworzony w czasie projektowania, używając jednego z kreatorów wymienionych poniżej. Nazwa przypisana do TableAdapter, podczas jej tworzenia opiera się na nazwę tabeli, do której pracujesz. Na przykład po utworzeniu TableAdapter na podstawie tabeli w bazie danych o nazwie `Orders`, nosi nazwę TableAdapter `OrdersTableAdapter`. Nazwa klasy TableAdapter można zmienić za pomocą **nazwa** właściwości w **Projektant obiektów Dataset**.  
  
 Poniżej przedstawiono typowe metody i właściwości TableAdapters:  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`TableAdapter.Fill`|Wypełnia tabelę skojarzone dane TableAdapter z wynikami polecenia SELECT TableAdapter.|  
|`TableAdapter.Update`|Wysyła zmiany z powrotem do bazy danych i zwraca liczbę całkowitą reprezentującą liczbę wierszy objętych aktualizacji. Aby uzyskać więcej informacji, zobacz [aktualizowanie danych za pomocą TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Zwraca nowy <xref:System.Data.DataTable> , które są wypełnione z danymi.|  
|`TableAdapter.Insert`|Tworzy nowy wiersz w tabeli danych. Aby uzyskać więcej informacji, zobacz [wstawianie nowych rekordów do bazy danych](../data-tools/insert-new-records-into-a-database.md).|  
|`TableAdapter.ClearBeforeFill`|Określa, czy tabela danych jest opróżniany przed wywołaniem jedną z `Fill` metody.|  
  
## <a name="tableadapter-update-method"></a>Metoda aktualizacji TableAdapter  
 TableAdapters polecenia danych do odczytu i zapisu z bazy danych. TableAdapter obiektu początkowej `Fill` kwerendy (głównego) jest używana jako podstawy do tworzenia schematu tabeli skojarzone dane, jak również `InsertCommand`, `UpdateCommand`, i `DeleteCommand` poleceń, które są skojarzone z `TableAdapter.Update` metody. Wywoływanie TableAdapter `Update` metody uruchamia instrukcje, które zostały utworzone podczas TableAdapter pierwotnie skonfigurowane, nie jest elementem dodatkowych zapytań, które zostało dodane z **Kreator konfiguracji zapytania TableAdapter**.  
  
 Użycie TableAdapter, efektywnie wykonuje te same operacje z poleceniami, które zazwyczaj będzie wykonywać. Na przykład, jeśli wywołasz karty `Fill` metody, karta uruchamia polecenie danych jego `SelectCommand` właściwości i używa czytnika danych (na przykład <xref:System.Data.SqlClient.SqlDataReader>) można załadować zestawu w tabeli danych wyników. Podobnie jeśli wywołasz karty `Update` metody, uruchamia odpowiednie polecenie (w `UpdateCommand`, `InsertCommand`, i `DeleteCommand` właściwości) dla każdej zmianie rekordu w tabeli danych.  
  
> [!NOTE]
>  Jeśli ma wystarczającej ilości informacji w głównym zapytaniu `InsertCommand`, `UpdateCommand`, i `DeleteCommand` poleceń jest tworzonych domyślnie podczas generowania TableAdapter. Jeśli zapytanietableadapter głównej jest więcej niż jednej tabeli instrukcji SELECT, prawdopodobnie projektant nie będzie mógł wygenerować `InsertCommand`, `UpdateCommand`, i `DeleteCommand`. Jeśli te polecenia nie są generowane, zostanie zgłoszony błąd podczas uruchamiania `TableAdapter.Update` metody.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 Oprócz `InsertCommand`, `UpdateCommand`, i `DeleteCommand`, TableAdapters są tworzone za pomocą metod, które mogą być uruchamiane bezpośrednio w bazie danych. Te metody (`TableAdapter.Insert`, `TableAdapter.Update`, i `TableAdapter.Delete`) można wywołać bezpośrednio do manipulowania danymi w bazie danych. Oznacza to, że w kodzie zamiast wywoływać metodę można wywołać tych poszczególnych metod `TableAdapter.Update` do obsługi operacji wstawiania, aktualizacji i usunięć, oczekujące dla tabeli skojarzonych danych.  
  
 Jeśli nie chcesz utworzyć te metody bezpośredniego, należy ustawić element TableAdapter **GenerateDbDirectMethods** właściwości `false` (w **właściwości** okno). Dodatkowych zapytań, które są dodawane do elementu TableAdapter są autonomiczne zapytania — nie generują one tych metod.  
  
## <a name="tableadapter-support-for-nullable-types"></a>Obsługa TableAdapter typy dopuszczające wartości zerowe  
 Typy dopuszczające wartości zerowe obsługuje TableAdapters `Nullable(Of T)` i `T?`. Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku Visual Basic, zobacz [typy dopuszczające wartości zerowe wartości](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku C#, zobacz [przy użyciu typów dopuszczających wartości zerowe](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).  
  
<a name="tableadaptermanager-reference"></a>  
  
## <a name="tableadaptermanager-reference"></a>Odwołanie TableAdapterManager  
 Domyślnie `TableAdapterManager` klasy jest generowany po utworzeniu zestawu danych, który zawiera powiązane tabele. Aby zapobiec klasy generowane, zmień wartość `Hierarchical Update` właściwości zestawu danych na wartość false. Podczas przeciągania tabeli, która ma relację na powierzchnię projektu formularza systemu Windows lub programu WPF strony Visual Studio deklaruje zmienną członkowską klasy. Nie używaj wiązania z danymi, trzeba ręcznie zadeklarować zmienną.  
  
 `TableAdapterManager` Klasa nie jest częścią [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. W związku z tym nie można go wyszukać w dokumentacji. Jest on tworzony w czasie projektowania, jako część procesu tworzenia zestawu danych.  
  
 Poniżej przedstawiono często używanych metod i właściwości `TableAdapterManager` klasy:  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`UpdateAll`— Metoda|Zapisuje wszystkie dane ze wszystkich tabel danych.|  
|`BackUpDataSetBeforeUpdate`Właściwość|Określa, czy należy utworzyć kopię zapasową zestawu danych, przed wykonaniem `TableAdapterManager.UpdateAll` metody. Wartość logiczna.|  
|*tableName* `TableAdapter` właściwości|Reprezentuje `TableAdapter`. Wygenerowany `TableAdapterManager` zawiera właściwość dla każdego `TableAdapter` zarządza. Na przykład zestaw danych z tabeli Klienci i zamówienia jest generowana za pomocą `TableAdapterManager` zawierający `CustomersTableAdapter` i `OrdersTableAdapter` właściwości.|  
|`UpdateOrder`Właściwość|Określa kolejność poszczególnych insert, update i polecenia usuwania. Ustaw tę wartość na jedną z wartości w `TableAdapterManager.UpdateOrderOption` wyliczenia.<br /><br /> Domyślnie `UpdateOrder` ustawiono **InsertUpdateDelete**. Oznacza to, które wstawia, a następnie aktualizuje i usuwa są wykonywane dla wszystkich tabel w zestawie danych.|

## <a name="security"></a>Zabezpieczenia  
Jeśli używasz polecenia danych z ustawioną właściwość CommandType <xref:System.Data.CommandType.Text>, należy dokładnie sprawdzić informacje wysyłane przez klienta przed przekazaniem go do bazy danych. Złośliwi użytkownicy mogą stanowić próbę wysyłania (Wstaw) zmodyfikowany lub dodatkowe instrukcje SQL w celu uzyskania nieautoryzowanego dostępu lub uszkodzenia bazy danych. Przed przeniesieniem danych wejściowych użytkownika do bazy danych zawsze Sprawdź, czy informacje są prawidłowe. Najlepszym rozwiązaniem jest zawsze używaj zapytań sparametryzowanych lub procedur składowanych, gdy jest to możliwe.  
  
## <a name="see-also"></a>Zobacz także
[Narzędzia zestawu danych](../data-tools/dataset-tools-in-visual-studio.md)