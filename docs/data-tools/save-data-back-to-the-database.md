---
title: Zapisywanie danych w bazie danych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f5d50dff4b71402184e0c1127242c1ddb0b1827f
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="save-data-back-to-the-database"></a>Zapisywanie danych w bazie danych
Zestaw danych znajduje się w pamięci kopia danych. Jeśli zmodyfikujesz danych jest dobrym rozwiązaniem, aby zapisać te zmiany w bazie danych. Można to robić na jeden z trzech sposobów:  
  
-   Wywołując jedną z metod aktualizacji TableAdapter  
  
-   Wywołując jedną z metod TableAdapter DBDirect  
  
-   Przez wywołanie metody UpdateAll na TableAdapterManager Visual Studio generuje automatycznie, gdy zestaw danych zawiera tabele, które są związane z innych tabel w zestawie danych  
  
Gdy dane są związane tabel zestawu danych do formantów w formularzu systemu Windows lub XAML strony, architektura powiązanie danych wykonuje całą pracę.  
  
Jeśli znasz TableAdapters, można przejść bezpośrednio do jednej z poniższych tematów:  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Wstawianie nowych rekordów do bazy danych](../data-tools/insert-new-records-into-a-database.md)|Jak przeprowadzić aktualizacje i wstawia przy użyciu polecenia lub TableAdapters obiektów|  
|[Aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Jak przeprowadzić aktualizacji przy użyciu TableAdapters|  
|[Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md)|Jak przeprowadzić aktualizacje z zestawu danych z co najmniej dwie tabele powiązane|  
|[Obsługiwanie wyjątku współbieżności](../data-tools/handle-a-concurrency-exception.md)|Sposób obsługi wyjątków, gdy dwóch użytkowników próbują zmienić tych samych danych w bazie danych, w tym samym czasie|  
|[Porady: zapisywanie danych przy użyciu transakcji](../data-tools/save-data-by-using-a-transaction.md)|Jak zapisać danych w transakcji za pomocą przestrzeni nazw System.Transactions i obiektu TransactionScope|  
|[Przewodnik: Zapisywanie danych w transakcji](../data-tools/save-data-in-a-transaction.md)|Wskazówki, która tworzy aplikacji formularzy systemu Windows, aby zademonstrować zapisywania danych do bazy danych wewnątrz transakcji|  
|[Zapisywanie danych w bazie danych (wiele tabel)](../data-tools/save-data-to-a-database-multiple-tables.md)|Sposób edytowania rekordów i Zapisz zmiany w wielu tabel w bazie danych|  
|[Zapisywanie danych z obiektu w bazie danych](../data-tools/save-data-from-an-object-to-a-database.md)|Sposób przekazywania danych z obiektu, który nie znajduje się w zestawie danych do bazy danych przy użyciu metody TableAdapter DbDirect|  
|[Zapisywanie danych za pomocą metod DBDirect adaptera TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Jak używać TableAdapter do wysyłania zapytań SQL bezpośrednio do bazy danych|  
|[Zapisywanie zestawu danych jako kodu XML](../data-tools/save-a-dataset-as-xml.md)|Jak zapisać zestawu danych do dokumentu XML|  
  
## <a name="two-stage-updates"></a>Aktualizacje dwuetapowa  
 Aktualizowanie źródła danych jest procesem dwuetapowym. Pierwszym krokiem jest można zaktualizować zestawu danych o nowych rekordów, zmienionych rekordów lub usuniętych rekordów. Jeśli aplikacja nigdy nie wysyła te zmiany z powrotem do źródła danych, następnie zakończeniu z aktualizacją.  
  
 Jeśli wysłać zmiany w bazie danych, drugi krok jest wymagany. Jeśli nie korzystasz z formantów powiązanych z danymi, następnie należy ręcznie wywołać metody aktualizacji TableAdapter tego samego (lub adapter danych), używany do wypełniania zestawu danych. Jednak umożliwia także różne karty, na przykład, aby przenieść dane z jednego źródła danych do innego lub zaktualizować wiele źródeł danych. Jeśli nie są używanie powiązania danych i zapisywania zmian dla tabele powiązane, należy ręcznie utworzyć wystąpienia zmiennej automatycznie generowanej klasy TableAdapterManager, a następnie wywołaj jej metodę UdpateAll.  
  
 ![Aktualizacje zbiorów danych Visual Basic](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates")  
Aktualizacja dwuetapowego procesu i roli DataRowVersion w Pomyślna aktualizacja  
  
 Zestaw danych zawiera kolekcje tabel, które zawierają kolekcji wierszy. Jeśli zamierzasz później zaktualizować źródła danych, musi użyć metody, dla właściwości DataTable.DataRowCollection podczas dodawania i usuwania wierszy. Te metody wykonywania śledzenia zmian, które ma potrzebne do aktualizowania źródła danych. Jeśli wywołujesz kolekcji Element RemoveAt we właściwości wierszy usunięcia nie będą przekazywane w bazie danych.  
  
## <a name="merge-datasets"></a>Scal zbiory danych  
 Możesz zaktualizować zawartość zestawu danych przez *scalanie* go z innego elementu dataset. Ten proces obejmuje kopiowanie zawartości *źródła* zestawu danych do dataset wywołujący (nazywane *docelowej* zestawu danych). Przy scalaniu zestawów danych nowych rekordów w źródłowym zestawie danych są dodawane do zestawu danych docelowego. Ponadto dodatkowe kolumny w źródłowym zestawie danych są dodawane do zestawu danych docelowego. Scalanie zestawów danych jest przydatne, gdy masz lokalne zestawu danych i uzyskać drugi zestaw danych z innej aplikacji. Jest również przydatne, gdy drugi zestaw danych można uzyskać od składnika, takiego jak usługi XML sieci web lub w przypadku, gdy konieczne zintegrowanie danych z wielu zestawów danych.  
  
 Podczas scalania zestawów danych, można przekazać logiczną argumentu (`preserveChanges`), który zawiadamia <xref:System.Data.DataSet.Merge%2A> metody przechowywanie modyfikacji istniejącego w docelowym elemencie dataset. Ponieważ zestawów danych, obsługa wielu wersji rekordów, należy pamiętać o więcej niż jedną wersję rekordy są scalane. W poniższej tabeli przedstawiono, jak scaleniu rekordu w dwóch zestawach:  
  
|DataRowVersion|Docelowy zestaw danych|Zestaw źródła danych|  
|--------------------|--------------------|--------------------|  
|Oryginał|Wilson Kuba|Kuba Wilson C.|  
|Bieżący|Jim Wilson|Kuba Wilson C.|  
  
 Wywoływanie <xref:System.Data.DataSet.Merge%2A> metody w poprzedniej tabeli z `preserveChanges=false targetDataset.Merge(sourceDataset)` powoduje następujące:  
  
|DataRowVersion|Docelowy zestaw danych|Zestaw źródła danych|  
|--------------------|--------------------|--------------------|  
|Oryginał|Kuba Wilson C.|Kuba Wilson C.|  
|Bieżący|Kuba Wilson C.|Kuba Wilson C.|  
  
 Wywoływanie <xref:System.Data.DataSet.Merge%2A> metody z `preserveChanges = true targetDataset.Merge(sourceDataset, true)` powoduje następujące:  
  
|DataRowVersion|Docelowy zestaw danych|Zestaw źródła danych|  
|--------------------|--------------------|--------------------|  
|Oryginał|Kuba Wilson C.|Kuba Wilson C.|  
|Bieżący|Jim Wilson|Kuba Wilson C.|  
  
> [!CAUTION]
>  W `preserveChanges = true` scenariusza, jeśli <xref:System.Data.DataSet.RejectChanges%2A> metoda jest wywoływana rekord docelowego zestawu danych, a następnie przywraca pierwotne dane z *źródła* zestawu danych. Oznacza to, że próba aktualizacji oryginalnego źródła danych z zestawu danych docelowego może nie być może znaleźć oryginalnego wiersza do aktualizacji. Naruszenie współbieżności można zapobiec przez wypełnianie innego elementu dataset zaktualizowane rekordy ze źródła danych, a następnie wykonuje scalania, aby zapobiec Naruszenie współbieżności. (Naruszenie współbieżności występuje, gdy inny użytkownik modyfikuje rekordu w źródle danych, po zestawu danych zostały wypełnione.)  
  
## <a name="update-constraints"></a>Ograniczenia aktualizacji  
 Aby wprowadzić zmiany w istniejącym wierszu danych, należy dodać lub zaktualizować danych w poszczególnych kolumnach. Jeśli zestaw danych zawiera ograniczenia (takie jak klucze obce lub ograniczenia wartości null), jest to możliwe, że rekord tymczasowo może być w stanie błędu, aktualizując go. Oznacza to może być w stanie błędu po zakończeniu aktualizowania jedną kolumnę, ale przed Przechodzimy do następnego.  
  
 Aby uniknąć naruszenia ograniczeń przedwczesny można czasowo zawiesić ograniczenia aktualizacji. Dzięki temu dwóch celów:  
  
-   Błąd uniemożliwia zgłaszane po zakończeniu aktualizowania jedną kolumnę, ale jeszcze nie rozpoczęto innej aktualizacji.  
  
-   Zapobiega niektórych aktualizacji zdarzeń jest wywoływane (zdarzenia, które są często używane do sprawdzania poprawności).  
   
> [!NOTE]
>  W formularzach systemu Windows, architektury powiązania danych, która jest wbudowana w elemencie datagrid wstrzymuje ograniczenia sprawdzania, dopóki fokus zostanie przeniesiona poza wierszem i nie trzeba jawnie wywołać <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, lub <xref:System.Data.DataRow.CancelEdit%2A> metody.  
  
 Ograniczenia są automatycznie wyłączone podczas <xref:System.Data.DataSet.Merge%2A> metoda jest wywoływana w zestawie danych. Po ukończeniu scalania, jeśli istnieją żadnych ograniczeń dla zestawu danych, która nie może być włączone, <xref:System.Data.ConstraintException> jest generowany. W takiej sytuacji <xref:System.Data.DataSet.EnforceConstraints%2A> właściwość jest ustawiona na `false,` i wszystkie naruszenia ograniczenia muszą zostać rozwiązane przed zresetowaniem <xref:System.Data.DataSet.EnforceConstraints%2A> właściwości `true`.  
  
 Po ukończeniu aktualizacji, można ponownie włączyć ograniczenia sprawdzania, który również włączające zdarzeń aktualizacji i uruchamia je.  
  
 Aby uzyskać więcej informacji na temat wstrzymywania zdarzeń, zobacz [wyłączanie ograniczeń w czasie wypełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
## <a name="dataset-update-errors"></a>Błędy aktualizacji zbiorów danych  
 Podczas aktualizacji rekordu w zestawie danych, istnieje prawdopodobieństwo wystąpienia błędu. Na przykład przypadkowo może zapisać danych niewłaściwy typ dla kolumny, lub danych, które są za długie lub inny problem integralności danych. Mogą też sprawdzanie poprawności specyficzne dla aplikacji, które może wiązać się błędy niestandardowe z dowolnym etapie zdarzenia aktualizacji. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md).  
  
## <a name="maintaining-information-about-changes"></a>Obsługa informacji na temat zmian  
 Informacje o zmianach wprowadzonych w zestawie danych są obsługiwane na dwa sposoby: przez flagowanie wierszy, które wskazują, że zostały zmienione (<xref:System.Data.DataRow.RowState%2A>) i utrzymywania wielu kopii rekordu (<xref:System.Data.DataRowVersion>). Za pomocą tych informacji, procesów można ustalić, co się zmieniło w zestawie danych i wysyłać odpowiednie aktualizacje w źródle danych.  
  
### <a name="rowstate-property"></a>Właściwość RowState  
 <xref:System.Data.DataRow.RowState%2A> Właściwość <xref:System.Data.DataRow> obiektu to wartość, która zawiera informacje o stanie z określonego wiersza danych.  
  
 W poniższej tabeli przedstawiono możliwe wartości <xref:System.Data.DataRowState> wyliczenie:  
  
|Wartość właściwością DataRowState|Opis|  
|------------------------|-----------------|  
|<xref:System.Data.DataRowState.Added>|Wiersz został dodany jako element, aby <xref:System.Data.DataRowCollection>. (Wiersz w tym stanie nie ma odpowiedniej wersji oryginalnej, ponieważ nie istnieje podczas ostatniego <xref:System.Data.DataRow.AcceptChanges%2A> wywołano metodę).|  
|<xref:System.Data.DataRowState.Deleted>|Wiersz został usunięty przy użyciu <xref:System.Data.DataRow.Delete%2A> z <xref:System.Data.DataRow> obiektu.|  
|<xref:System.Data.DataRowState.Detached>|Wiersz został utworzony, ale nie jest częścią żadnego <xref:System.Data.DataRowCollection>. A <xref:System.Data.DataRow> obiekt jest w tym stanie, natychmiast po jej utworzeniu, przed zostało ono dodane do kolekcji, a po został on usunięty z kolekcji.|  
|<xref:System.Data.DataRowState.Modified>|Wartość kolumny w wierszu została zmieniona w inny sposób.|  
|<xref:System.Data.DataRowState.Unchanged>|Wiersz nie zmienił się od <xref:System.Data.DataRow.AcceptChanges%2A> ostatniego została wywołana.|  
  
### <a name="datarowversion-enumeration"></a>DataRowVersion — wyliczenie  
Zestawy danych, obsługa wielu wersji rekordów. <xref:System.Data.DataRowVersion> Pola mogą być używane podczas pobierania wartości znalezione w <xref:System.Data.DataRow> przy użyciu <xref:System.Data.DataRow.Item%2A> właściwości lub <xref:System.Data.DataRow.GetChildRows%2A> metody <xref:System.Data.DataRow> obiektu.  
  
W poniższej tabeli przedstawiono możliwe wartości <xref:System.Data.DataRowVersion> wyliczenie:  
  
|Wartość DataRowVersion|Opis|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|Bieżąca wersja rekord zawiera wszystkie zmiany, które mogły zostać wykonane w rekordzie od czasu ostatniego <xref:System.Data.DataRow.AcceptChanges%2A> została wywołana. Jeśli wiersz został usunięty, nie istnieje żadne bieżącej wersji.|  
|<xref:System.Data.DataRowVersion.Default>|Wartość domyślna rekordu, zgodnie z definicją w zestawie danych schematu lub źródła danych.|  
|<xref:System.Data.DataRowVersion.Original>|Oryginalnej wersji rekordu jest kopią rekordu, jakim znajdował się, że czas ostatniej zmiany zostały zatwierdzone w zestawie danych. W praktyce jest zwykle wersji rekordu jako odczytu źródła danych.|  
|<xref:System.Data.DataRowVersion.Proposed>|Proponowane wersji rekordu, który jest dostępny, tymczasowo, gdy trwa aktualizacja — to znaczy, między czasem wywołana <xref:System.Data.DataRow.BeginEdit%2A> — metoda i <xref:System.Data.DataRow.EndEdit%2A> — metoda. Zwykle dostęp proponowanych wersji rekordu w procedurze obsługi zdarzenia takich jak <xref:System.Data.DataTable.RowChanging>. Wywoływanie <xref:System.Data.DataRow.CancelEdit%2A> metoda odwraca zmiany i usuwa proponowanych wersję wiersza danych.|  
  
 Oryginalny i bieżące wersje są przydatne informacje dotyczące aktualizacji są przesyłane do źródła danych. Zazwyczaj gdy aktualizacja jest wysyłana do źródła danych, nowe informacje dla bazy danych jest w bieżącej wersji rekordu. Informacje z oryginalną wersją jest używana do lokalizowania rekordu do uaktualnienia.  
  
 Na przykład w przypadku, gdy zostanie zmieniona klucza podstawowego rekordu, należy zlokalizować właściwego rekordu w źródle danych, aby można było zaktualizować zmiany. Jeśli nie oryginalnej wersji istnieje, a następnie rekord najprawdopodobniej będzie dołączona do źródła danych, co nie tylko w rekordzie bardzo niepożądane, ale w jeden rekord, który jest niedokładna i nieaktualny. Dwie wersje są również używane w formancie współbieżności. Możesz porównać oryginalnej wersji przed rekordu w źródle danych, aby określić, czy rekord został zmieniony od ostatniego załadowania do zestawu danych.  
  
 Proponowane wersji jest przydatne, gdy trzeba wykonać weryfikacji przed faktycznie zatwierdzenie zmian do zestawu danych.  
  
 Nawet jeśli rekordy uległy zmianie, nie ma zawsze oryginalny lub bieżącej wersji tego wiersza. Po włożeniu nowy wiersz do tabeli nie ma wersji oryginalnej, bieżącej wersji. Podobnie jeśli usunięcia wiersza przez wywołanie w tabeli `Delete` metody, brak oryginalnej wersji, ale nie bieżącej wersji.  
  
 Możesz przetestować, czy określonej wersji rekordu istnieje badając wiersz danych <xref:System.Data.DataRow.HasVersion%2A> metody. Dostęp do danej wersji rekordu przez przekazanie <xref:System.Data.DataRowVersion> wartość wyliczenia jako opcjonalny argument w przypadku żądania wartość kolumny.  
  
## <a name="getting-changed-records"></a>Pobieranie zmienionych rekordów  
 Jest typowym rozwiązaniem z aktualizacji każdego rekordu w zestawie danych. Na przykład użytkownik może pracować z formularzy systemu Windows <xref:System.Windows.Forms.DataGridView> kontrolkę wyświetlającą wiele rekordów. Użytkownik może jednak zaktualizować tylko kilka rekordów, Usuń jedno i wstawić nową. Tabele zestawów danych i danych udostępnia metody (`GetChanges`) dla zwracania tylko wiersze, które zostały zmodyfikowane.  
  
 Możesz utworzyć podzbiór zmienionych rekordów przy użyciu `GetChanges` metody tabeli danych (<xref:System.Data.DataTable.GetChanges%2A>) lub zestawu danych (<xref:System.Data.DataSet.GetChanges%2A>) samej siebie. Jeśli należy wywołać metodę dla tabeli danych zwraca kopii tabeli z tylko zmienionych rekordów. Podobnie jeśli należy wywołać metodę dla zestawu danych, możesz uzyskać nowy zestaw danych z tylko zmienionych rekordów w nim.  
  
 `GetChanges`samodzielnie zwraca wszystkie zmienionych rekordów. Z kolei, przekazując żądaną <xref:System.Data.DataRowState> jako parametr `GetChanges` metody, można określić podzbiór zmienionych rekordów mają: nowo dodany rekordów i rekordów, które są oznaczone do usunięcia, odłączyć rekordów lub zmodyfikowanych rekordów.  
  
 Pobieranie podzbiór zmienionych rekordów jest przydatne, gdy chcesz wysyłać do innego składnika do przetwarzania rekordów. Zamiast przesyłania całego zestawu danych, można zmniejszyć koszty komunikowania się z innych składników, pobierając tylko te rekordy, które wymaga składnika.   
  
## <a name="committing-changes-in-the-dataset"></a>Zatwierdza zmiany w zestawie danych  
 Zmiany w zestawie danych, <xref:System.Data.DataRow.RowState%2A> ustawiono właściwość zmienionych wierszy. Oryginalny i bieżące wersje rekordów są ustalone, obsługiwane i udostępniane przez <xref:System.Data.DataRowView.RowVersion%2A> właściwości. Metadane są przechowywane we właściwościach tych zmienionych wierszy jest niezbędne do wysyłania właściwe aktualizacje w źródle danych.  
  
 Jeśli zmiany odzwierciedlają aktualny stan źródła danych, nie trzeba zachować te informacje. Zazwyczaj istnieją dwa razy podczas są zsynchronizowane zestawu danych i jego źródło:  
  
-   Natychmiast po informacje zostały załadowane do zestawu danych, np. podczas odczytu danych ze źródła.  
  
-   Po wysłaniu zmiany z zestawu danych do źródła danych (, ale nie przed, ponieważ spowoduje utratę informacje zmiany, które są wymagane, aby wysłać zmiany do bazy danych).  
  
Oczekujące zmiany zostaną zatwierdzone do zestawu danych, przez wywołanie metody <xref:System.Data.DataSet.AcceptChanges%2A> metody. Zazwyczaj <xref:System.Data.DataSet.AcceptChanges%2A> nazywa się o następujących godzinach:  
  
-   Po załadowaniu zestawu danych. Czy ładowanie zestawu danych przez wywołanie metody TableAdapter `Fill` metody, a następnie kartę automatycznie zatwierdza zmiany dla Ciebie. Jednak jeśli zestaw danych zostanie załadowana przez scalenie innego elementu dataset, następnie należy ręcznie zatwierdzić zmiany.  
  
    > [!NOTE]
    >  Karta uniemożliwia automatyczne zatwierdzenie zmian po wywołaniu `Fill` metody ustawiając `AcceptChangesDuringFill` właściwości karty do `false`. Jeśli wartość jest ustawiona na `false`, a następnie <xref:System.Data.DataRow.RowState%2A> każdego wiersza, który dodaje się podczas operacji fill jest ustawiony na wartość <xref:System.Data.DataRowState.Added>.  
  
-   Po wysłaniu zmiany zestawu danych do innego procesu, takie jak usługi XML sieci Web.  
  
    > [!CAUTION]
    >  Zatwierdzenie zmiany w ten sposób usuwa wszystkie informacje o zmianach. Nie zatwierdzić zmiany dopiero po zakończyć wykonywanie operacji, które wymagają aplikacji w taki sposób, aby dowiedzieć się, jakie zmiany wprowadzono w zestawie danych.  
  
Ta metoda wykonuje następujące czynności:  
  
-   Zapisuje <xref:System.Data.DataRowVersion.Current> wersji rekordu do jego <xref:System.Data.DataRowVersion.Original> wersji i zastępuje oryginalną wersją.  
  
-   Usuwa wszystkie wiersze gdzie <xref:System.Data.DataRow.RowState%2A> właściwość jest ustawiona na <xref:System.Data.DataRowState.Deleted>.  
  
-   Ustawia <xref:System.Data.DataRow.RowState%2A> właściwości rekordu do <xref:System.Data.DataRowState.Unchanged>.  
  
<xref:System.Data.DataSet.AcceptChanges%2A> Metoda jest dostępna na trzech poziomach. Można go wywołać w <xref:System.Data.DataRow> obiekt do zatwierdzenia zmian właśnie tego wiersza. Należy także wywołać ją na <xref:System.Data.DataTable> obiekt, aby zatwierdzić wszystkie wiersze w tabeli. Na koniec należy wywołać go na <xref:System.Data.DataSet> obiekt, aby zatwierdzić wszystkie oczekujące zmiany we wszystkich rekordach wszystkich tabel zestawu danych.  
  
W poniższej tabeli opisano, jakie zmiany są zatwierdzone na co obiekt ma zostać wywołana metoda na podstawie.  
  
|Metoda|Wynik|  
|------------|------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Zmiany zostały wprowadzone tylko dla określonego wiersza.|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Zmiany zostały wprowadzone na wszystkie wiersze w określonej tabeli.|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Zmiany zostały wprowadzone we wszystkich wierszach we wszystkich tabelach zestawu danych.|  
  
> [!NOTE]
>  Czy ładowanie zestawu danych przez wywołanie metody TableAdapter `Fill` metody, nie trzeba jawnie zaakceptować zmiany. Domyślnie `Fill` wywołania metody `AcceptChanges` metody po zakończeniu wypełnianie tabeli danych.  
  
 Powiązanej metody, <xref:System.Data.DataSet.RejectChanges%2A>, opcja zmiany przez skopiowanie <xref:System.Data.DataRowVersion.Original> wersji do <xref:System.Data.DataRowVersion.Current> wersji rekordów. Ustawia również <xref:System.Data.DataRow.RowState%2A> z każdego rekordu z powrotem <xref:System.Data.DataRowState.Unchanged>.  
  
## <a name="data-validation"></a>Sprawdzanie poprawności danych  
 Aby sprawdzić, czy danych w aplikacji użytkownika spełnia wymagania procesów, które są przekazywane do, często trzeba dodawać sprawdzania poprawności. Może to obejmować sprawdzanie, czy wpis użytkownika w postaci jest poprawny, sprawdzanie poprawności danych, które są wysyłane do aplikacji przez inną aplikację, lub nawet sprawdzanie, czy informacje, które jest obliczane w ramach składnika mieści się w ograniczenia źródła danych i wymagań aplikacji.  
  
 Można zweryfikować danych na kilka sposobów:  
  
-   W warstwie business, przez dodawanie kodu do aplikacji, aby sprawdzić poprawność danych. Zestaw danych znajduje się w jednym miejscu, można to zrobić. Zestaw danych zawiera niektóre zalety weryfikacji zaplecza — takie jak możliwość weryfikacji zmian, ponieważ zmieniasz wartości kolumn i wierszy. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md).  
  
-   W warstwie prezentacji, przez dodawanie walidacji do formularzy. Aby uzyskać więcej informacji, zobacz [sprawdzania poprawności danych wejściowych użytkownika w formularzach systemu Windows](/dotnet/framework/winforms/user-input-validation-in-windows-forms).  
  
-   W danych zaplecza, na wysyłanie danych do źródła danych — na przykład bazy danych —, dzięki czemu jego o zaakceptowanie lub odrzucenie danych. Podczas pracy z bazą danych, w którym dostępne są zaawansowane opcje urządzenia do sprawdzania poprawności danych i udostępnia informacje o błędzie, może to być praktyczne rozwiązania, ponieważ można sprawdzić poprawność danych niezależnie od tego, gdzie pochodzi on z. Jednak ta metoda nie może uwzględnić wymagania weryfikacji specyficzne dla aplikacji. Ponadto posiadanie źródła danych sprawdzania poprawności danych może spowodować wiele rund do źródła danych, w zależności od tego, jak aplikacji upraszcza rozpoznawanie błędów sprawdzania poprawności zgłaszany przez wewnętrzny.  
  
    > [!IMPORTANT]
    >  Za pomocą poleceń danych z <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> właściwość, która ma ustawioną wartość <xref:System.Data.CommandType.Text>, należy dokładnie sprawdzić informacje wysyłane przez klienta przed przekazaniem go do bazy danych. Złośliwi użytkownicy mogą stanowić próbę wysyłania (Wstaw) zmodyfikowany lub dodatkowe instrukcje SQL w celu uzyskania nieautoryzowanego dostępu lub uszkodzenia bazy danych. Przed przeniesieniem danych wejściowych użytkownika do bazy danych zawsze Sprawdź, czy informacje są prawidłowe. Jest najlepszym rozwiązaniem, aby zawsze używała zapytań sparametryzowanych lub procedur składowanych, gdy jest to możliwe.  
  
## <a name="transmitting-updates-to-the-data-source"></a>Przesyłania aktualizacji do źródła danych  
Po dokonaniu zmian w zestawie danych, może przesyłać zmiany ze źródłem danych. Najczęściej, możesz to zrobić przez wywołanie metody `Update` metodę TableAdapter (lub adapter danych). Metoda pętlę każdego rekordu w tabeli danych określa, jaki typ aktualizacji jest wymagany (aktualizowania, wstawiania lub usuwania), jeśli istnieje, a następnie uruchamia odpowiednie polecenie.  

 Ilustracją jak zaktualizowane Załóżmy, że aplikacja korzysta z zestawu danych, który zawiera jednej tabeli danych. Aplikacja pobiera dwa wiersze z bazy danych. Po ich pobraniu tabeli w pamięci danych wygląda następująco:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 Aplikacja zmieni Irena Nowak "Preferowane". W wyniku tej zmiany wartości <xref:System.Data.DataRow.RowState%2A> właściwości dla danego wiersza zmieni się z <xref:System.Data.DataRowState.Unchanged> do <xref:System.Data.DataRowState.Modified>. Wartość <xref:System.Data.DataRow.RowState%2A> właściwości dla pierwszego wiersza pozostaje <xref:System.Data.DataRowState.Unchanged>. Tabela danych teraz wygląda następująco:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 Wywołania teraz aplikacji `Update` metodę transmisji zestawu danych w bazie danych. Metoda sprawdza kolejno każdy wiersz. Pierwszy wiersz metoda nieprzesyłania nie instrukcji SQL w bazie danych, ponieważ ten wiersz nie został zmieniony, ponieważ pierwotnie została pobrana z bazy danych.  
  
 Dla drugiego wiersza, jednak `Update` metoda automatycznie wywołuje polecenie prawidłowe dane i przesyła ją do bazy danych. Dialekt programu SQL Server, która jest obsługiwana przez Magazyn danych zależy od określonej składni instrukcji SQL. Ale są warte wymienienia następujące cechy ogólne przesyłane instrukcji SQL:  
  
-   Przesłano instrukcja SQL jest instrukcji UPDATE. Karta zna użyć instrukcji aktualizacji, ponieważ wartość <xref:System.Data.DataRow.RowState%2A> jest właściwość <xref:System.Data.DataRowState.Modified>.  
  
-   Przesyłane instrukcji SQL zawiera klauzulę WHERE, co oznacza, że obiekt docelowy instrukcji UPDATE wiersz gdzie `CustomerID = 'c400'`. Ta część instrukcji SELECT odróżnia wiersz docelowy od innych, ponieważ `CustomerID` jest to klucz podstawowy tabeli docelowej. Informacje dotyczące klauzuli WHERE pochodzi od wersji oryginalnej rekordu (`DataRowVersion.Original`), w przypadku wartości, które są wymagane do identyfikowania wiersza zostały zmienione.  
  
-   Przesłano instrukcja SQL zawiera klauzuli SET, aby ustawić nowe wartości zmodyfikowanej kolumny.  
  
    > [!NOTE]
    >  Jeśli element TableAdapter `UpdateCommand` właściwość została ustawiona na nazwę procedury składowanej, karta nie tworzenia instrukcji SQL. Zamiast tego wywołuje procedurę składowaną z odpowiednimi parametrami przekazany.  
  
## <a name="passing-parameters"></a>Przekazywanie parametrów  
 Zwykle używasz parametry do przekazania te rekordy, które mają zostać zaktualizowane w bazie danych.  Gdy element TableAdapter `Update` metoda jest uruchamiana w instrukcji UPDATE, należy podać wartości parametrów. Pobiera wartości te `Parameters` kolekcję dla polecenia odpowiednie dane — w takim przypadku `UpdateCommand` Obiekt TableAdapter.  
  
 Jeśli używano narzędzia programu Visual Studio do generowania adaptera danych `UpdateCommand` obiekt zawiera kolekcję parametrów, które odpowiadają symbol zastępczy każdego parametru w instrukcji.  
  
 <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> Właściwości każdego parametru wskazuje kolumnę w tabeli danych. Na przykład `SourceColumn` właściwość `au_id` i `Original_au_id` parametry ustawiono niezależnie od kolumny w tabeli danych zawiera identyfikator autora. Gdy karty `Update` uruchamia — metoda odczytuje identyfikator kolumny autora z rekordu, który jest aktualizowana i wpisuje wartości w instrukcji.  
  
 W instrukcji UPDATE należy określić zarówno nowe wartości (takie, które będą zapisywane dla tego rekordu) również stare wartości (tak, aby rekordu może znajdować się w bazie danych). Istnieją dwa parametry dla każdej wartości: jeden dla klauzuli SET, a druga w klauzuli WHERE. Oba parametry odczytać danych z rekordu, który jest aktualizowana, ale otrzymują różne wersje wartości kolumn na podstawie parametru <xref:System.Data.SqlClient.SqlParameter.SourceVersion> właściwości. Parametr dla klauzuli SET pobiera bieżącą wersję, a parametr dla klauzuli WHERE pobiera wersji oryginalnej.  
  
> [!NOTE]
>  Można też ustawić wartości w `Parameters` kolekcji samodzielnie w kodzie, które zwykle należy w obsłudze zdarzeń dla adaptera danych <xref:System.Data.DataTable.RowChanging> zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
[Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
[Tworzenie i konfigurowanie TableAdapters](create-and-configure-tableadapters.md)  
[Aktualizowanie danych za pomocą TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
[Powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[Sprawdzanie poprawności danych](validate-data-in-datasets.md)   
[Zapisywanie danych](../data-tools/saving-data.md)