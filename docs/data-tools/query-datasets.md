---
title: "Zapytanie zestawów danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 10e37db09efab78b3048ddeab4096325ba00802f
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="query-datasets"></a>Zestawy danych zapytania
Aby wyszukiwać określone rekordy w zestawie danych, użyj metody FindBy DataTable, zapis własnych instrukcji foreach do pętli kolekcji wierszy tabeli lub użyj [LINQ do DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
## <a name="dataset-case-sensitivity"></a>Uwzględniana wielkość liter zestawu danych  
W zestawie danych, bez uwzględniania wielkości liter domyślnie są nazwy tabel i kolumn, oznacza to, tabelę w zestawie danych o nazwie "Klientów" można także określane jako "klienci". Konwencje nazewnictwa w wielu baz danych, w tym program SQL Server jest zgodny. W programie SQL Server domyślne zachowanie to, że nazwy elementów danych nie można rozróżnić tylko wielkością liter.  
  
> [!NOTE]
>  W przeciwieństwie do zestawów danych dokumentów XML uwzględniana jest wielkość liter, nazwy zdefiniowanych w schematach elementów danych jest rozróżniana wielkość liter. Na przykład protokół schematu umożliwia schematu do definiowania tabeli o nazwie "Klientów" oraz różnych tabeli o nazwie "klienci". Może to spowodować konflikty nazw podczas schemat, który zawiera elementy, które różnią się tylko wielkością liter służy do generowania klasy dataset.  
  
Uwzględniana wielkość liter, można jednak czynnikiem interpretacji danych wewnątrz elementu dataset. Na przykład jeśli filtrowanie danych w tabeli zestawu danych, kryteria wyszukiwania mogą zwracać różne wyniki, w zależności od tego, czy wynik porównania jest rozróżniana wielkość liter. Można kontrolować uwzględniana wielkość liter, filtrowanie, wyszukiwanie i sortowanie przez ustawienie dataset <xref:System.Data.DataSet.CaseSensitive%2A> właściwości. Domyślnie wszystkie tabele w zestawie danych dziedziczą wartość tej właściwości. (Można zmienić tej właściwości dla każdej pojedynczej tabeli, ustawiając w tabeli <xref:System.Data.DataTable.CaseSensitive%2A> właściwości.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Lokalizowanie określonego wiersza w tabeli danych  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Aby odnaleźć wiersza typizowanego zestaw danych z wartości klucza podstawowego  
  
-   Aby zlokalizować wiersza, należy wywołać silnie typizowaną `FindBy` metody, która używa klucza podstawowego tabeli.  
  
     W poniższym przykładzie `CustomerID` kolumna jest kluczem podstawowym `Customers` tabeli. Oznacza to, że wygenerowany `FindBy` jest metoda `FindByCustomerID`. W przykładzie pokazano, jak przypisać określony <xref:System.Data.DataRow> ze zmienną za pomocą wygenerowany `FindBy` metody.  
  
     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Aby odnaleźć wiersza nietypizowanego zestawu danych z wartości klucza podstawowego  
  
-   Wywołanie <xref:System.Data.DataRowCollection.Find%2A> metody <xref:System.Data.DataRowCollection> kolekcji, przekazując klucza podstawowego jako parametr.  
  
     Poniższy przykład przedstawia sposób zadeklarować nowy wiersz o nazwie `foundRow` i przypisz jej wartość zwracaną <xref:System.Data.DataRowCollection.Find%2A> metody. Jeśli zostanie znaleziony taki klucz podstawowy, zawartość indeks kolumny 1 są wyświetlane w oknie komunikatu.  
  
     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]  
  
## <a name="find-rows-by-column-values"></a>Znajdź wiersz według wartości w kolumnie  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Aby znaleźć na podstawie wartości w kolumnie wszystkie wiersze  
  
-   Tabele danych są tworzone za pomocą <xref:System.Data.DataTable.Select%2A> metodę, która zwraca tablicę <xref:System.Data.DataRow>s oparte na wyrażeniu przekazany do <xref:System.Data.DataTable.Select%2A> metody. Aby uzyskać więcej informacji o tworzeniu prawidłowe wyrażenia, zobacz sekcję "Składni wyrażeń" strony <xref:System.Data.DataColumn.Expression%2A> właściwości.  
  
     Poniższy przykład przedstawia użycie <xref:System.Data.DataTable.Select%2A> metody <xref:System.Data.DataTable> zlokalizować określonych wierszy.  
  
     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]  
  
## <a name="access-related-records"></a>Dostęp do powiązanych rekordów  
Gdy są powiązane tabele w zestawie danych, <xref:System.Data.DataRelation> obiektu można udostępnić powiązane rekordy z innej tabeli. Na przykład zestaw danych zawierający `Customers` i `Orders` tabele mogą być udostępniane.  
  
Można użyć <xref:System.Data.DataRelation> obiekt do zlokalizowania powiązanych rekordów przez wywołanie metody <xref:System.Data.DataRow.GetChildRows%2A> metody <xref:System.Data.DataRow> w tabeli nadrzędnej. Ta metoda zwraca tablicę rekordów podrzędnych. Lub możesz wywołać <xref:System.Data.DataRow.GetParentRow%2A> metody <xref:System.Data.DataRow> w tabeli podrzędnej. Ta metoda zwraca pojedynczą <xref:System.Data.DataRow> między tabelą nadrzędną.  
  
Ta strona zawiera przykłady użycia typizowane zbiory danych. Aby dowiedzieć się, jak nawigowanie po relacjach w nietypizowane zbiory danych, zobacz [nawigowanie po DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).  
  
> [!NOTE]
>  Jeśli pracujesz w aplikacji formularzy systemu Windows i korzysta z funkcji powiązania danych, aby wyświetlić dane, wygenerowany przez projektanta formularza może zapewnić za mało funkcjonalność aplikacji. Aby uzyskać więcej informacji, zobacz [powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). W szczególności, zobacz [relacje w zestawach danych](relationships-in-datasets.md).  
  
W poniższych przykładach kodu pokazują, jak przechodzić w górę i w dół relacje w typizowanych zbiorach danych. Użyj przykłady kodu wpisany <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) i wygenerowanego FindBy*PrimaryKey* (`FindByCustomerID`) metody do wyszukiwania żądanego wiersza i zwracać powiązane rekordy. Przykłady skompilować i działa poprawnie tylko wtedy, gdy:  
  
-   Wystąpienie zestawu danych o nazwie `NorthwindDataSet` z `Customers` tabeli.  
  
-   `Orders` Tabeli.  
  
-   Relacja o nazwie `FK_Orders_Customers`dotyczące dwóch tabel.  
  
Ponadto obie tabele muszą zostać wypełnione z danymi dla wszystkich rekordów, które ma zostać zwrócona.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Aby powrócić rejestruje rekord nadrzędny wybranego elementu podrzędnego  
  
-   Wywołanie <xref:System.Data.DataRow.GetChildRows%2A> metody określonej `Customers` danych wiersza, a następnie zwraca tablicę wiersze z `Orders` tabeli:  
  
     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Aby przywrócić rekord nadrzędny wybranego podrzędnego rekordu  
  
-   Wywołanie <xref:System.Data.DataRow.GetParentRow%2A> metody określonej `Orders` wiersz danych i zwracany pojedynczy wiersz z tabeli `Customers` tabeli:  
  
     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Zobacz także
[Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  