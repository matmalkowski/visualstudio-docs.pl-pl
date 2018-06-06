---
title: Hierarchiczna aktualizacja
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 442d6cd60597219c25b41f26ad8c2dc2151248ee
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747472"
---
# <a name="hierarchical-update"></a>Hierarchiczna aktualizacja
*Hierarchiczna aktualizacja* proces zapisywanie zaktualizowanych danych (z zestawu danych z dwóch lub więcej powiązanych tabel) do bazy danych przy zachowaniu zasady integralności referencyjnej. *Integralność referencyjna* odwołuje się do reguły spójności udostępniane przez ograniczenia w bazie danych, które kontrolują zachowanie wstawiania, aktualizowania i usuwania rekordów powiązanych. Na przykład jest integralności referencyjnej, wymusza tworzenie rekordu klienta przed zezwoleniem zamówień ma zostać utworzony dla tego klienta.  Aby uzyskać więcej informacji na temat relacje w zestawach danych, zobacz [relacje w zestawach danych](../data-tools/relationships-in-datasets.md)

 Używa funkcji hierarchicznej aktualizacji `TableAdapterManager` do zarządzania `TableAdapter`s w typizowanego obiektu dataset. `TableAdapterManager` Składnik jest [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-wygenerowane klasy, więc nie jest częścią [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Podczas przeciągania tabelę z okna źródeł danych do formularzy systemu Windows lub programu WPF strony Visual Studio dodaje zmienną typu TableAdapterManager do formularza lub strony, a następnie zostanie wyświetlony w Projektancie na pasku składnika. Aby uzyskać szczegółowe informacje o `TableAdapterManager` klasy, zobacz sekcję odwołanie TableAdapterManager [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

 Domyślnie zestawu danych traktuje powiązane tabele jako "tylko relacje" oznacza, że nie wymuszania ograniczeń klucza obcego. To ustawienie w czasie projektowania można modyfikować za pomocą Projektanta obiektów Dataset. Wybierz wiersz relacji między dwiema tabelami, aby wyświetlić **relacji** okno dialogowe. Zmiany wprowadzone w tym miejscu będą określają sposób TableAdapterManager zachowania, gdy wysłać zmiany w tabelach pokrewnych w bazie danych.

## <a name="enable-hierarchical-update-in-a-dataset"></a>Włącz hierarchicznej aktualizacji w zestawie danych
 Hierarchiczna aktualizacja domyślnie dla wszystkich nowych baz danych, które zostały dodane lub utworzony w projekcie. Włączanie lub wyłączanie hierarchicznej aktualizacji przez ustawienie **hierarchicznej aktualizacji** właściwości typizowanego zestaw danych w zestawie danych do **True** lub **False**:

 ![Ustawienie hierarchiczna aktualizacja](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>Tworzenie nowej relacji między tabelami
 Aby utworzyć nową relację między dwiema tabelami, w Projektancie obiektów Dataset, wybierz pasek tytułu każdej tabeli, następnie kliknij prawym przyciskiem myszy i wybierz **Dodawanie relacji**.

 ![Hierarchiczna aktualizacja Dodaj menu relacji](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Ograniczenia klucza obcego, kaskadowych aktualizacji i usuwania
 Ważne jest, aby zrozumieć, jak ograniczenia klucza obcego i kaskadowych zachowanie w bazie danych są tworzone w kodzie wygenerowanym zestawie danych.

 Domyślnie tabel danych w zestawie danych są generowane z relacji (<xref:System.Data.DataRelation>) spełniających relacje w bazie danych. Relacja w zestawie danych nie jest generowana jako ograniczenie klucza obcego. <xref:System.Data.DataRelation> Jest skonfigurowany jako **tylko relacja** bez <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> lub <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> obowiązywać.

 Domyślnie aktualizacje kaskadowe i usuwanie kaskadowe są wyłączone nawet wtedy, gdy relacja bazy danych ustawiono aktualizacji kaskadowych i/lub usuwanie kaskadowe włączona. Na przykład tworzenie nowego klienta i zamówienie nowe, a następnie spróbuj zapisać danych może powodować konflikt z ograniczenia klucza obcego, które są zdefiniowane w bazie danych. Aby uzyskać więcej informacji, zobacz [wyłączanie ograniczeń w czasie wypełniania zestawu danych](turn-off-constraints-while-filling-a-dataset.md).

## <a name="set-the-order-to-perform-updates"></a>Ustaw kolejność przeprowadzania aktualizacji
 Ustawienie kolejności przeprowadzania aktualizacji ustawia kolejność poszczególne wstawia, aktualizowanie i usuwanie które są wymagane do Zapisz wszystkie zmodyfikowane dane we wszystkich tabelach zestawu danych. Hierarchiczna aktualizacja jest włączona, wstawia odbywa się najpierw, a następnie aktualizuje i usuwa. `TableAdapterManager` Zapewnia `UpdateOrder` właściwości, która może być zestaw przeprowadzania aktualizacji najpierw, a następnie wstawienia i usunięcia.

> [!NOTE]
>  Jest ważne dowiedzieć się, że kolejność aktualizacji całkowitą. Oznacza to kiedy aktualizacje są wykonywane, wstawiania i usuwania są wykonywane dla wszystkich tabel w zestawie danych.

 Aby ustawić `UpdateOrder` właściwości po przeciąganie elementów z [Data Sources — okno](add-new-data-sources.md) na formularz, wybierz `TableAdapterManager` w składnika na pasku zadań, a następnie ustawić `UpdateOrder` właściwości w **właściwości** okna.

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Utwórz kopię zapasową zestawu danych przed wykonaniem hierarchiczna aktualizacja
 Podczas zapisywania danych (wywołując `TableAdapterManager.UpdateAll()` metodę), `TableAdapterManager` próby aktualizacji danych dla każdej tabeli w ramach jednej transakcji. W przypadku niepowodzenia żadnej części aktualizacji dla dowolnej tabeli cała transakcja zostanie wycofana. W większości przypadków wycofywanie zwraca aplikacji do stanu pierwotnego.

 Jednak czasami może chcesz przywrócić zestawu danych z kopii zapasowej. Przykładem mogą wystąpić podczas korzystania z automatycznego przyrostu wartości. Na przykład, jeśli zapisywania operacji kończy się niepowodzeniem, automatycznego przyrostu wartości nie są resetowane w zestawie danych i kontynuuje zestawu danych do tworzenia wartości, zwiększając automatycznie. Spowoduje to pozostawienie przerwa w numeracji, które nie mogą być akceptowane w aplikacji. W sytuacjach, w przypadku, gdy jest to problem `TableAdapterManager` zapewnia `BackupDataSetBeforeUpdate` właściwość, która zastępuje istniejący zestaw danych z kopii zapasowej, jeśli transakcja nie powiedzie się.

> [!NOTE]
>  Kopia zapasowa znajduje się tylko w pamięci podczas `TableAdapterManager.UpdateAll` metody jest uruchomiona. Dlatego nie jest brak programowy dostęp do tego zestawu kopii zapasowych danych, ponieważ jego zastępuje oryginalnego zestawu danych lub wykracza poza zakres natychmiast `TableAdapterManager.UpdateAll` zakończeniu metody.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modyfikowanie wygenerowany Zapisz kod, aby wykonać hierarchiczna aktualizacja
 Zapisz zmiany z tabel powiązanych danych w zestawie danych do bazy danych przez wywołanie metody `TableAdapterManager.UpdateAll` — metoda i przekazywanie nazwy zestawu danych, który zawiera powiązane tabele. Na przykład uruchom `TableAdapterManager.UpdateAll(NorthwindDataset)` metody do wysyłania aktualizacji ze wszystkich tabel NorthwindDataset do wewnętrznej bazy danych.

 Po upuszczeniu elementy z **źródeł danych** okna, kod jest automatycznie dodawany do `Form_Load` zdarzeń, aby wypełnić każdej tabeli ( `TableAdapter.Fill` metody). Kod jest także dodawane do **zapisać** zdarzenia kliknij przycisk <xref:System.Windows.Forms.BindingNavigator> można zapisać danych z zestawu danych w bazie danych ( `TableAdapterManager.UpdateAll` metody).

 Zapisz wygenerowany kod zawiera również wiersza kodu, który wywołuje `CustomersBindingSource.EndEdit` metody. W szczególności, wywołuje <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody pierwszego <xref:System.Windows.Forms.BindingSource>dodana do formularza. Innymi słowy, ten kod jest generowany tylko w pierwszej tabeli, która zostanie przeciągnięty z **źródeł danych** okna na formularzu. <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Wywołania zatwierdza zmiany, które są w toku w formantów powiązanych z danymi, które są aktualnie edytowany. W związku z tym, jeśli formant powiązany z danymi nadal ma fokus i użytkownik kliknie **Zapisz** przycisk wszystkie oczekujące zmiany, w tym kontroli są zaangażowane przed rzeczywiste Zapisz ( `TableAdapterManager.UpdateAll` metody).

> [!NOTE]
>  Projektant obiektów Dataset tylko dodaje `BindingSource.EndEdit` kodu do pierwszej tabeli, które są przenoszone do formularza. W związku z tym należy dodać wiersza kodu w celu wywołania `BindingSource.EndEdit` metody dla każdej tabeli powiązanego na formularzu. W ramach tego przewodnika, oznacza to, należy dodać wywołanie `OrdersBindingSource.EndEdit` metody.

#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Aby zaktualizować kodu w celu zatwierdzenia zmian w tabelach pokrewnych przed zapisaniem

1.  Kliknij dwukrotnie **zapisać** znajdującego się na <xref:System.Windows.Forms.BindingNavigator> otworzyć **Form1** w edytorze kodu.

2.  Dodaj wiersz kodu w celu wywołania `OrdersBindingSource.EndEdit` metody po wierszu, który wywołuje `CustomersBindingSource.EndEdit` metody. Kod w **zapisać** kliknij przycisk zdarzeń powinien przypominać następujący:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

Oprócz zatwierdzania zmian w tabeli podrzędnych przed zapisaniem danych do bazy danych, również może być konieczne zatwierdzanie nowo utworzone rekordy główne przed dodaniem nowych rekordów podrzędnych do zestawu danych. Innymi słowy, może być konieczne dodanie nowego rekordu nadrzędnego (klienta) do zestawu danych przed ograniczeń klucza obcego włączyć nowe podrzędne rekordy (zamówienia), który ma zostać dodany do zestawu danych. W tym celu można użyć elementu podrzędnego `BindingSource.AddingNew` zdarzeń.

> [!NOTE]
> Czy należy zatwierdzić nowych rekordów nadrzędnego zależy od typu formantu, który jest używany do powiązania ze źródłem danych. W tym przewodniku pojedynczych formantów służy do powiązania tabeli nadrzędnej. Wymaga to dodatkowego kodu można przekazać nowy rekord nadrzędny. Jeśli rekordy główne zamiast były wyświetlane w formancie złożone powiązanie, takich jak <xref:System.Windows.Forms.DataGridView>, dodatkowego <xref:System.Windows.Forms.BindingSource.EndEdit%2A> wywołania dla rekordu nadrzędnego nie jest konieczne. Jest to spowodowane funkcjonalność wiązania danych formantu obsługuje zatwierdzania nowych rekordów.

#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Aby dodać kod, aby zatwierdzić rekordy główne w zestawie danych przed dodaniem nowych rekordów podrzędnych

1.  Tworzenie procedury obsługi zdarzeń dla `OrdersBindingSource.AddingNew` zdarzeń.

    -   Otwórz **Form1** w widoku Projekt, wybierz **OrdersBindingSource** na pasku składnika wybierz **zdarzenia** w **właściwości** okna, i następnie kliknij dwukrotnie ikonę **AddingNew** zdarzeń.

2.  Dodaj wiersz kodu do obsługi zdarzeń, który wywołuje `CustomersBindingSource.EndEdit` metody. Kod w `OrdersBindingSource_AddingNew` obsługi zdarzeń powinny przypominać następujący:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>Odwołanie TableAdapterManager
 Domyślnie `TableAdapterManager` klasy jest generowany po utworzeniu zestawu danych, który zawiera powiązane tabele. Aby zapobiec klasy generowane, zmień wartość `Hierarchical Update` właściwości zestawu danych na wartość false. Podczas przeciągania tabeli, która ma relację na powierzchnię projektu formularza systemu Windows lub programu WPF strony Visual Studio deklaruje zmienną członkowską klasy. Nie używaj wiązania z danymi, trzeba ręcznie zadeklarować zmienną.

 `TableAdapterManager` Klasa nie jest częścią [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. W związku z tym nie można go wyszukać w dokumentacji. Jest on tworzony w czasie projektowania, jako część procesu tworzenia zestawu danych.

 Poniżej przedstawiono często używanych metod i właściwości `TableAdapterManager` klasy:

|Element członkowski|Opis|
|------------|-----------------|
|`UpdateAll` — Metoda|Zapisuje wszystkie dane ze wszystkich tabel danych.|
|`BackUpDataSetBeforeUpdate` Właściwość|Określa, czy należy utworzyć kopię zapasową zestawu danych, przed wykonaniem `TableAdapterManager.UpdateAll` metody. Wartość logiczna.|
|*tableName* `TableAdapter` właściwości|Reprezentuje `TableAdapter`. Wygenerowany `TableAdapterManager` zawiera właściwość dla każdego `TableAdapter` zarządza. Na przykład zestaw danych z tabeli Klienci i zamówienia jest generowana za pomocą `TableAdapterManager` zawierający `CustomersTableAdapter` i `OrdersTableAdapter` właściwości.|
|`UpdateOrder` Właściwość|Określa kolejność poszczególnych insert, update i polecenia usuwania. Ustaw tę wartość na jedną z wartości w `TableAdapterManager.UpdateOrderOption` wyliczenia.<br /><br /> Domyślnie `UpdateOrder` ustawiono **InsertUpdateDelete**. Oznacza to, które wstawia, a następnie aktualizuje i usuwa są wykonywane dla wszystkich tabel w zestawie danych.|

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)