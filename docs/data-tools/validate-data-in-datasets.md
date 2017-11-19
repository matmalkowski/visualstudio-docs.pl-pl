---
title: "Sprawdzanie poprawności danych w zestawach danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 0f328cbaac03680885bdbda97dff7bc9ac3cf2cf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="validate-data-in-datasets"></a>Sprawdzanie poprawności danych w zestawach danych
Sprawdzanie poprawności danych jest proces potwierdzania wartości wprowadzanego do obiektów danych są zgodne z ograniczeniami w ramach schematu zestawu danych. Proces weryfikacji również potwierdza, że te wartości są następujące reguły, które zostały utworzone dla aplikacji. Jest dobrym rozwiązaniem, aby sprawdzić poprawność danych przed ich wysłaniem aktualizacje do źródłowej bazy danych. Zmniejsza to błędy, a także potencjalnych liczby rund między aplikacją i bazy danych.  
  
Można potwierdzić, czy dane, które są zapisywane do zestawu danych jest prawidłowa, tworząc sprawdzanie poprawności do zestawu danych sam. Zestaw danych można sprawdzić danych niezależnie od tego, jak jest wykonywana aktualizacja — czy bezpośrednio przez formanty w postaci, w ramach składnika, lub w inny sposób. Ponieważ zestaw danych jest częścią aplikacji (w przeciwieństwie do wewnętrznej bazie danych), jest logiczną miejsce do kompilacji sprawdzania poprawności specyficznych dla aplikacji.  
  
Najlepszym miejscem, aby dodać sprawdzania poprawności do aplikacji znajduje się w pliku częściowej klasy dataset. W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], otwórz **Projektant obiektów Dataset** i kliknij dwukrotnie kolumna lub tabela, dla której chcesz utworzyć sprawdzania poprawności. Ta akcja powoduje automatyczne utworzenie <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> obsługi zdarzeń. 
  
## <a name="validate-data"></a>Sprawdzanie poprawności danych  
 Sprawdzanie poprawności w zestawie danych można zrobić w następujący sposób:  
  
-   Tworząc własne sprawdzania poprawności specyficznych dla aplikacji, które sprawdza, czy wartości w kolumnie poszczególnych danych podczas zmiany.  Aby uzyskać więcej informacji, zobacz [porady: Sprawdzanie poprawności danych podczas zmiany kolumn](validate-data-in-datasets.md).  
  
-   Tworząc własne weryfikacji specyficzne dla aplikacji, które sprawdza, czy dane wartości podczas całej danych zmienia wiersza. Aby uzyskać więcej informacji, zobacz [porady: Sprawdzanie poprawności danych podczas zmiany wiersza](validate-data-in-datasets.md).  
  
-   Tworząc klucze i ograniczenia unique i tak dalej jako część definicji rzeczywiste schemat zestawu danych. 
  
-   Przez ustawienie właściwości <xref:System.Data.DataColumn> obiektu, takie jak <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, i <xref:System.Data.DataColumn.Unique%2A>.  
  
Kilka zdarzeń są wywoływane przez <xref:System.Data.DataTable> obiektu, gdy występuje zmiany w rekordzie:  
  
-   <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzenia są generowane podczas i po każdej zmianie do pojedynczej kolumny. <xref:System.Data.DataTable.ColumnChanging> Zdarzeń jest przydatne, gdy chcesz zatwierdzić zmiany w określonych kolumnach. Informacje o proponowanej zmiany jest przekazywany jako argument ze zdarzeniem. 
-   <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzenia są generowane podczas i po jednej zmiany w wierszu. <xref:System.Data.DataTable.RowChanging> Zdarzenie jest bardziej ogólne. Wskazuje on, że zmiany występuje gdzieś w wierszu, ale nie wiesz, która kolumna została zmieniona.  
  
Domyślnie każda zmiana kolumny w związku z tym zgłasza cztery zdarzenia. Pierwsza to <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzenia dla określonej kolumny, która jest zmieniane. Następnie są <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzenia. Jeśli jest wiele zmian do wiersza, zdarzenia zostanie wygenerowany dla każdej zmiany.  
  
> [!NOTE]
>  Wiersz danych <xref:System.Data.DataRow.BeginEdit%2A> metody wyłącza <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzeń po każdej zmianie poszczególnych kolumn. W takim przypadku zdarzenie nie jest wywoływane przed <xref:System.Data.DataRow.EndEdit%2A> metoda została wywołana, gdy <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzenia są generowane tylko raz. Aby uzyskać więcej informacji, zobacz [wyłączanie ograniczeń w czasie wypełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
Wybrane zdarzenie zależy od tego, jak szczegółowego ma sprawdzania poprawności należy. Jeśli jest to ważne, catch błąd, natychmiast, gdy kolumna zmieni tworzenia weryfikacji przy użyciu <xref:System.Data.DataTable.ColumnChanging> zdarzeń. W przeciwnym razie użyj <xref:System.Data.DataTable.RowChanging> zdarzeń, co może spowodować Przechwytywanie jednocześnie kilka błędów. Ponadto, jeśli dane mają strukturę tak, aby wartość jedną kolumnę sprawdzania poprawności na podstawie zawartości innej kolumny, następnie weryfikowania Twojej podczas <xref:System.Data.DataTable.RowChanging> zdarzeń.
  
Po zaktualizowaniu rekordów, <xref:System.Data.DataTable> obiektu informuje o zdarzeniach, które mogą odpowiadać na zmiany są wykonywane i po wprowadzeniu zmian.  
  
Jeśli aplikacja używa typizowanego zestaw danych, można utworzyć procedury obsługi zdarzeń jednoznacznie. Spowoduje to dodanie czterech dodatkowych typu zdarzenia, które można utworzyć procedury obsługi dla: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, i `dataTableNameRowDeleted`. Te programy obsługi zdarzeń typu przekazać argument, który zawiera nazwy kolumn tabeli, które czytelność kodu do zapisu i odczytu.  
  
## <a name="data-update-events"></a>Dane zdarzenia aktualizacji  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|Wartość w kolumnie został zmieniony. Zdarzenie przekazuje wiersz i kolumnę, wraz z proponowanych nową wartość.|  
|<xref:System.Data.DataTable.ColumnChanged>|Zmieniono wartość w kolumnie. Zdarzenie przekazuje wiersz i kolumnę, wraz z proponowaną wartość.|  
|<xref:System.Data.DataTable.RowChanging>|Zmiany dokonane w <xref:System.Data.DataRow> obiektów mają być przekazane do zestawu danych. Jeśli nie wywołano <xref:System.Data.DataRow.BeginEdit%2A> metody <xref:System.Data.DataTable.RowChanging> zdarzenie jest wywoływane dla każdej zmiany z kolumną natychmiast po <xref:System.Data.DataTable.ColumnChanging> zdarzeń został zgłoszony. Jeśli zostanie wywołany <xref:System.Data.DataRow.BeginEdit%2A> przed wprowadzeniem zmian, <xref:System.Data.DataTable.RowChanging> zdarzenie jest wywoływane tylko wtedy, gdy jest wywoływana <xref:System.Data.DataRow.EndEdit%2A> metody.<br /><br /> Zdarzenie przekazuje wiersz do Ciebie, oraz wartość wskazującą, jaki typ akcji (zmiana, Wstaw itd.) jest wykonywana.|  
|<xref:System.Data.DataTable.RowChanged>|Wiersz został zmieniony. Zdarzenie przekazuje wiersz do Ciebie, oraz wartość wskazującą, jaki typ akcji (zmiana, Wstaw itd.) jest wykonywana.|  
|<xref:System.Data.DataTable.RowDeleting>|Trwa usuwanie wiersza. Zdarzenie przekazuje wiersz do Ciebie, oraz wartość wskazującą, jaki typ akcji (Usuń) jest wykonywana.|  
|<xref:System.Data.DataTable.RowDeleted>|Wiersz został usunięty. Zdarzenie przekazuje wiersz do Ciebie, oraz wartość wskazującą, jaki typ akcji (Usuń) jest wykonywana.|  
  
<xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, I <xref:System.Data.DataTable.RowDeleting> zdarzenia są wywoływane podczas procesu aktualizacji. Można użyć tych zdarzeń do sprawdzania poprawności danych lub wykonywania innych typów przetwarzania. Ponieważ ta aktualizacja jest w toku podczas tych zdarzeń, możesz anulować jej zgłoszeniu wyjątku, który uniemożliwia aktualizację z zakończenia.  
  
<xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> i <xref:System.Data.DataTable.RowDeleted> zdarzenia są zdarzenia powiadomień, które są wywoływane, gdy aktualizacja została ukończona pomyślnie. Zdarzenia te są przydatne do podjęcia dalszych czynności w oparciu o pomyślnej aktualizacji.  
  
## <a name="validate-data-during-column-changes"></a>Sprawdzanie poprawności danych podczas zmiany kolumn  
  
> [!NOTE]
>  **Projektant obiektów Dataset** tworzy częściowej klasy, w których weryfikacji logiki można dodać do zestawu danych. Wygenerowany przez projektanta dataset nie usunąć lub zmienić kod w klasie częściowej.  
  
Można sprawdzić poprawności danych po zmianie wartości w kolumnie dane odpowiedzi na <xref:System.Data.DataTable.ColumnChanging> zdarzeń. Zgłoszony, to zdarzenie przekazuje argument zdarzenia (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) zawiera wartość, która jest proponowana dla bieżącej kolumny. Na podstawie zawartości z `e.ProposedValue`, można wykonywać następujące czynności:  
  
-   Zaakceptuj wartość proponowanych, wykonując nothing.  
  
-   Odrzuć proponowaną wartość ustawiając błąd kolumny (<xref:System.Data.DataRow.SetColumnError%2A>) z wewnątrz obsługi zdarzenia zmiany kolumny.  
  
-   Opcjonalnie użyj <xref:System.Windows.Forms.ErrorProvider> formantu, aby wyświetlić komunikat o błędzie dla użytkownika. Aby uzyskać więcej informacji, zobacz [ErrorProvider — składnik](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).  
  
Można również przeprowadzić weryfikacji podczas <xref:System.Data.DataTable.RowChanging> zdarzeń. 
  
## <a name="validate-data-during-row-changes"></a>Sprawdzanie poprawności danych podczas przeprowadzania zmian w wierszach  
Można napisać kod, aby zweryfikować, że każdy kolumnę, którą chcesz zweryfikować zawiera dane, które spełnia wymagania aplikacji. W tym celu ustawienia kolumny, aby wskazać, że zawiera błąd, jeśli proponowanej wartości jest nie do przyjęcia. W poniższych przykładach ustawiana błąd kolumny po `Quantity` kolumna jest mniejsze lub równe 0. Programy obsługi zdarzeń zmiany wiersza powinno przypominać następujące przykłady.  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Aby sprawdzić poprawność danych, gdy wiersz zmieni (Visual Basic)  
  
1.  Otwórz zestaw danych w **Projektant obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Kliknij dwukrotnie ikonę na pasku tytułu tabeli, którą chcesz zweryfikować. Ta akcja powoduje automatyczne utworzenie <xref:System.Data.DataTable.RowChanging> obsługi zdarzeń <xref:System.Data.DataTable> w pliku klasy częściowego zestawu danych.  
  
    > [!TIP]
    >  Kliknij dwukrotnie z lewej strony nazwy tabeli, aby utworzyć program obsługi zdarzeń zmiany wiersza. Dwukrotne kliknięcie nazwy tabeli, można go edytować.  
  
     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>Aby sprawdzić poprawność danych, gdy wiersz zmieni (C#)  
  
1.  Otwórz zestaw danych w **Projektant obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie zestawu danych w Projektancie obiektów dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Kliknij dwukrotnie ikonę na pasku tytułu tabeli, którą chcesz zweryfikować. Ta akcja tworzy plik klasy częściowe dla <xref:System.Data.DataTable>.  
  
    > [!NOTE]
    >  **Projektant obiektów Dataset** nie tworzy automatycznie programu obsługi zdarzeń dla <xref:System.Data.DataTable.RowChanging> zdarzeń. Należy utworzyć metody obsługi <xref:System.Data.DataTable.RowChanging> zdarzeń i wykonywania kodu podpinanie zdarzeń w metodzie inicjowania tabeli.  
  
3.  Skopiuj następujący kod do klasy częściowej:  
  
    ```csharp  
    public override void EndInit()  
    {  
        base.EndInit();  
        Order_DetailsRowChanging += TestRowChangeEvent;  
    }  
  
    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)  
    {  
        if ((short)e.Row.Quantity <= 0)  
        {  
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
        }  
        else  
        {  
            e.Row.SetColumnError("Quantity", "");  
        }  
    }  
    ```  
  
## <a name="to-retrieve-changed-rows"></a>Pobieranie zmienionych wierszy  
Każdy wiersz w tabeli danych ma <xref:System.Data.DataRow.RowState%2A> właściwość, która przechowuje informacje o bieżący stan tego wiersza przy użyciu wartości w <xref:System.Data.DataRowState> wyliczenia. Może zwracać zmienionych wierszy z tabeli zestawu danych lub danych, wywołując `GetChanges` metody <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>. Możesz sprawdzić, czy istnieją zmiany przed wywołaniem `GetChanges` przez wywołanie metody <xref:System.Data.DataSet.HasChanges%2A> metody zestawu danych. 
  
> [!NOTE]
>  Po zatwierdzeniu zmian do zestawu danych lub danych tabeli (wywołując <xref:System.Data.DataSet.AcceptChanges%2A> metodę), `GetChanges` metoda nie zwraca żadnych danych. Jeśli aplikacja wymaga do przetwarzania zmienionych wierszy, można przetwarzać zmiany przed wywołaniem `AcceptChanges` metody.  
  
Wywoływanie <xref:System.Data.DataSet.GetChanges%2A> metoda zestawu danych lub danych tabeli. zwraca nową tabelę dataset lub danych, która zawiera tylko rekordy, które zostały zmienione. Jeśli chcesz pobrać określone rekordy — na przykład tylko nowe rekordy, czy tylko zmodyfikowane — można przekazać wartość z zakresu od <xref:System.Data.DataRowState> wyliczenie jako parametr `GetChanges` metody.  
  
Użyj <xref:System.Data.DataRowVersion> wyliczeniu, aby uzyskać dostęp do różnych wersji wierszy (na przykład oryginalne wartości, które zostały w wierszu przed jego przetworzeniem).  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>Aby uzyskać wszystkie zmienionych rekordów z zestawu danych  
  
-   Wywołanie <xref:System.Data.DataSet.GetChanges%2A> metody zestawu danych.  
  
     Poniższy przykład tworzy nowy zestaw danych o nazwie `changedRecords` i wypełnia zmienionych rekordów z innego zestawu danych o nazwie `dataSet1`.  
  
     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>Aby uzyskać wszystkie zmienionych rekordów w tabeli danych  
  
-   Wywołanie <xref:System.Data.DataTable.GetChanges%2A> metody elementu DataTable.  
  
     Poniższy przykład tworzy nową tabelę danych o nazwie `changedRecordsTable` i wypełnia zmienionych rekordów z innej tabeli danych o nazwie `dataTable1`.  
  
     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Aby uzyskać wszystkie rekordy, które mają stan określonego wiersza  
  
-   Wywołanie `GetChanges` metody zestawu danych lub tabeli danych i przekazać <xref:System.Data.DataRowState> wartość wyliczenia jako argument.  
  
     Poniższy przykład pokazuje, jak utworzyć nowy zestaw danych o nazwie `addedRecords` i wypełnić ją tylko rekordy, które zostały dodane do `dataSet1` zestawu danych.  
  
     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]  
  
     Poniższy przykład przedstawia sposób zwrócenia wszystkich rekordów, które zostały ostatnio dodane do `Customers` tabeli:  
  
     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>Dostęp do oryginalnej wersji DataRow  
Podczas wprowadzania zmian do wierszy danych zestawu danych zachowuje zarówno oryginalne (<xref:System.Data.DataRowVersion.Original>) i nowe (<xref:System.Data.DataRowVersion.Current>) wersji wiersza. Na przykład przed wywołaniem `AcceptChanges` metody aplikacji można uzyskać dostęp do różnych wersji rekordu (zgodnie z definicją w <xref:System.Data.DataRowVersion> wyliczenie) i w związku z tym przetwarzania zmian.  
  
> [!NOTE]
>  Istnieją różne wersje wiersza tylko wtedy, gdy został zmodyfikowany i przed `AcceptChanges` została wywołana metoda. Po `AcceptChanges` została wywołana metoda, bieżących i oryginalnych wersje są takie same.  
  
Przekazywanie <xref:System.Data.DataRowVersion> wartość wraz z indeks kolumny (lub nazwy kolumny jako ciąg) zwraca wartość z tej kolumny wersji określonego wiersza. Zmienione kolumny jest określana w trakcie <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzenia. Jest to odpowiedni moment, aby sprawdzić wersje inny wiersz na potrzeby sprawdzania poprawności. Jednak jeśli zostały tymczasowo wstrzymane ograniczenia, te zdarzenia nie będą zgłaszane i konieczne będzie programowo zidentyfikować kolumny, które zostały zmienione. Aby to zrobić, iteracji <xref:System.Data.DataTable.Columns%2A> kolekcji i porównanie różnych <xref:System.Data.DataRowVersion> wartości.  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Aby uzyskać oryginalnej wersji rekordu  
  
-   Dostęp do wartości kolumny przez przekazywanie <xref:System.Data.DataRowVersion> wiersza, aby wrócić.  
  
     Poniższy przykład przedstawia użycie <xref:System.Data.DataRowVersion> wartości do pobrania oryginalnej wartości elementu `CompanyName` w <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>Dostęp do bieżącej wersji DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Aby uzyskać bieżącą wersję rekordu  
  
-   Dostęp do wartości kolumny, a następnie dodaj parametr do indeksu, który wskazuje, która wersja wiersz ma być zwrócona.  
  
     Poniższy przykład przedstawia użycie <xref:System.Data.DataRowVersion> wartość, aby uzyskać bieżącą wartość `CompanyName` w <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]  
  
## <a name="see-also"></a>Zobacz także
[Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
[Porady: Sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)   
[Porady: wyświetlanie ikon błędów dotyczących weryfikacji formularza z systemu Windows składnika ErrorProvider formularzy](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)