---
title: Edytowanie danych w zestawach danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1ad74243c70b4ca7aaa8460759abbc898d30bb9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757152"
---
# <a name="edit-data-in-datasets"></a>Edytowanie danych w zestawach danych
Taki sam sposób, jak edytować dane w tabeli w dowolnej bazy danych można edytować dane w tabelach danych. Proces może obejmować, wstawianie, aktualizowanie i usuwanie rekordów w tabeli. W formularzu powiązane z danymi można określić pola, które są można edytować użytkownika. W takich przypadkach infrastruktury wiązania danych obsługuje wszystkie śledzenia zmian, aby zmiany mogą być wysyłane w bazie danych później. Jeśli programowo wprowadź zmiany do danych i chcesz wysłać te zmiany z powrotem do bazy danych, należy użyć obiektów i metod, które wykonują śledzenia zmian dla Ciebie.

Oprócz zmiana danych rzeczywistych, możesz także zbadać <xref:System.Data.DataTable> aby zwrócić określone wiersze danych. Na przykład może wyszukać poszczególne wiersze, określonych wersji wierszy (oryginalny i proponowanych), wiersze, które zostały zmienione lub wierszy zawierających błędy.

## <a name="to-edit-rows-in-a-dataset"></a>Aby edytować wierszy w zestawie danych
Aby edytować istniejący wiersz w <xref:System.Data.DataTable>, musisz zlokalizować <xref:System.Data.DataRow> chcesz edytować, a następnie przypisz zaktualizowanej wartości do kolumny.

Jeśli nie znasz indeks wiersza chcesz edytować, użyj `FindBy` metody, aby przeprowadzić wyszukiwanie według klucza podstawowego:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Jeśli znasz indeks wiersza, mogą uzyskiwać dostęp do i umożliwia edytowanie wierszy w następujący sposób:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Aby wstawić nowe wiersze do zestawu danych
Aplikacji, które zwykle korzystają z formantów powiązanych z danymi na dodawanie nowych rekordów za pośrednictwem **Dodaj nowy** znajdującego się na [formantu BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Aby ręcznie dodać nowych rekordów do zestawu danych, należy utworzyć nowy wiersz danych przez wywołanie metody w elemencie DataTable. Następnie należy dodać do wiersza <xref:System.Data.DataRow> kolekcji (<xref:System.Data.DataTable.Rows%2A>) z <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Aby zachować informacje wymagane przez zestaw danych do wysyłania aktualizacji do źródła danych, użyj <xref:System.Data.DataRow.Delete%2A> sposób usuwania wierszy w tabeli danych. Na przykład, jeśli aplikacja używa TableAdapter (lub <xref:System.Data.Common.DataAdapter>), TableAdapter `Update` metoda usuwa wierszy w bazie danych, które mają <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState.Deleted>.

Jeśli aplikacja nie wymaga wysyłać aktualizacje źródła danych, istnieje możliwość usuwania rekordów, uzyskując bezpośrednio dostęp do zbierania danych wiersza (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Aby usunąć rekordy z tabeli danych

-   Wywołanie <xref:System.Data.DataRow.Delete%2A> metody <xref:System.Data.DataRow>.

     Ta metoda nie fizycznie Usuń rekord. Zamiast tego oznacza rekordu do usunięcia.

    > [!NOTE]
    >  Jeśli właściwość count <xref:System.Data.DataRowCollection>, wynikowa liczba zawiera rekordy, które zostały oznaczone do usunięcia. Aby uzyskać dokładne liczba rekordów, które nie są oznaczone do usunięcia, można przeglądać kolekcji patrzeć <xref:System.Data.DataRow.RowState%2A> właściwości każdego rekordu. (Rekordy oznaczona do usunięcia mają <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState.Deleted>.) Alternatywnie możesz utworzyć widok danych z zestawu danych, który filtry oparte na stanie wiersza i uzyskać właściwości z tego miejsca.

Poniższy przykład przedstawia sposób wywołania <xref:System.Data.DataRow.Delete%2A> metodę, aby oznaczyć w pierwszym wierszu w `Customers` tabeli jako usunięte:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Ustal, czy są zmienionych wierszy
Podczas wprowadzania zmian rekordów w zestawie danych, informacje dotyczące tych zmian są przechowywane do momentu je zatwierdzić. Zatwierdź zmiany po wywołaniu `AcceptChanges` metodę tabeli zestawu danych lub danych, albo po wywołaniu `Update` metody TableAdapter lub danych karty.

Zmiany są śledzone dwie metody w każdym wierszu danych:

-   Każdy wiersz danych zawiera informacje powiązane z jego <xref:System.Data.DataRow.RowState%2A> (na przykład <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>, lub <xref:System.Data.DataRowState.Unchanged>).

-   Każdy wiersz danych zawiera wiele wersji tego wiersza (<xref:System.Data.DataRowVersion>), wersja oryginalna (przed zmianą) i bieżącej wersji (po wprowadzeniu zmian). W okresie, gdy zmiany oczekujące (czas, kiedy może odpowiadać na <xref:System.Data.DataTable.RowChanging> zdarzeń), innej wersji — proponowane wersji — jest również dostępna.

<xref:System.Data.DataSet.HasChanges%2A> Metoda zestawu danych zwraca `true` Jeśli wprowadzono zmiany w zestawie danych. Po określeniu, czy istnieją zmienionych wierszy, można wywołać `GetChanges` metody <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> do zwrócenia zestaw zmienionych wierszy.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Aby określić, czy wprowadzono zmiany do wszystkich wierszy

-   Wywołanie <xref:System.Data.DataSet.HasChanges%2A> wierszy zmienić metody zestawu danych do sprawdzenia.

Poniższy przykład przedstawia sposób sprawdzić wartość zwrotną z elementu <xref:System.Data.DataSet.HasChanges%2A> metody wykrywania, czy istnieją wszelkich zmienionych wierszy w zestawie danych o nazwie `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Określanie typu zmian
Możesz również sprawdzić, aby zobaczyć, jaki typ zmiany wprowadzono w zestawie danych przez przekazanie wartości z <xref:System.Data.DataRowState> wyliczeniu, aby <xref:System.Data.DataSet.HasChanges%2A> metody.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Aby określić, jakiego rodzaju zmiany zostały wprowadzone do wiersza

-   Przekaż <xref:System.Data.DataRowState> do wartości <xref:System.Data.DataSet.HasChanges%2A> metody.

Poniższy przykład przedstawia sposób sprawdzania zestawu danych o nazwie `NorthwindDataset1` ustalenie, jeśli jakiekolwiek nowe wiersze zostały dodane do niej:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Aby zlokalizować wierszy zawierających błędy
Podczas pracy z poszczególnych kolumn i wierszy danych, mogą wystąpić błędy. Możesz sprawdzić `HasErrors` właściwości w celu określenia, czy występują błędy w <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow>.

1.  Sprawdź `HasErrors` właściwość, aby sprawdzić, czy w zestawie danych są błędy.

2.  Jeśli `HasErrors` właściwość jest `true`, iterowania po kolekcji tabel, a następnie za pomocą wiersze, aby znaleźć wiersza z powodu błędu.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Zobacz także

- [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)