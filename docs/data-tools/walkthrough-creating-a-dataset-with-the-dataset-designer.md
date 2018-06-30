---
title: 'Wskazówki: tworzenie zestawu danych za pomocą narzędzia Projektant obiektów Dataset'
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 32a093e59d918f34ddf5da9cbb5edb13c96b2777
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117930"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Wskazówki: Tworzenie zestawu danych w Projektancie obiektów Dataset

W tym przewodniku można utworzyć zestawu danych przy użyciu **Projektant obiektów Dataset**. Artykuł przeprowadza użytkownika przez proces tworzenia nowego projektu i dodawanie nowej **DataSet** element, aby go. Dowiesz się, jak utworzyć tabel na podstawie tabel w bazie danych bez użycia kreatora.

## <a name="prerequisites"></a>Wymagania wstępne

W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.

1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [strony pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **magazynu danych i przetwarzania** obciążenia, lub jako poszczególnych składników.

2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.

## <a name="create-a-new-windows-forms-application-project"></a>Utwórz nowy projekt aplikacji formularzy systemu Windows

1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy** > **projektu**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop**.

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.

4. Nazwij projekt **DatasetDesignerWalkthrough**, a następnie wybierz pozycję **OK**.

     Visual Studio dodaje projekt do **Eksploratora rozwiązań** i wyświetlić nowy formularz w projektancie.

## <a name="add-a-new-dataset-to-the-application"></a>Dodaj nowy zestaw danych do aplikacji

1.  Na **projektu** menu, wybierz opcję **Dodaj nowy element**.

     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.

2.  W okienku po lewej stronie wybierz **danych**, a następnie wybierz pozycję **DataSet** w środkowym okienku.

3.  Nazwa zestawu danych **NorthwindDataset**, a następnie wybierz pozycję **Dodaj**.

     Visual Studio dodaje plik o nazwie **NorthwindDataset.xsd** do projektu i otwarcie go w **Projektant obiektów Dataset**.

## <a name="create-a-data-connection-in-server-explorer"></a>Utwórz połączenie danych w Eksploratorze serwera

1.  Na **widoku** menu, kliknij przycisk **Eksploratora serwera**.

2.  W **Eksploratora serwera**, kliknij przycisk **Połącz z bazą danych** przycisku.

3.  Utwórz połączenie z przykładową bazą danych Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Tworzenie tabel w zestawie danych

W tej sekcji opisano sposób dodawania tabel do zestawu danych.

### <a name="to-create-the-customers-table"></a>Aby utworzyć tabelę Customers

1.  Rozwiń węzeł połączenia danych utworzonego w **Eksploratora serwera**, a następnie rozwiń węzeł **tabel** węzła.

2.  Przeciągnij **klientów** tabeli **Eksploratora serwera** na **Projektant obiektów Dataset**.

     A **klientów** tabeli danych i **CustomersTableAdapter** są dodawane do zestawu danych.

### <a name="to-create-the-orders-table"></a>Aby utworzyć tabelę Orders

-   Przeciągnij **zamówień** tabeli **Eksploratora serwera** na **Projektant obiektów Dataset**.

     **Zamówień** tabeli danych **OrdersTableAdapter**i danych relacji między **klientów** i **zamówień** tabele są dodawane do zestaw danych.

### <a name="to-create-the-orderdetails-table"></a>Aby utworzyć tabelę OrderDetails

-   Przeciągnij **szczegółów zamówienia** tabeli **Eksploratora serwera** na **Projektant obiektów Dataset**.

     **Szczegółów zamówienia** tabeli danych **OrderDetailsTableAdapter**i relację danych między **zamówień** i **SzczegółyZamówienia** tabel zostaną dodane do zestawu danych.

## <a name="next-steps"></a>Następne kroki

-   Zapisywanie zestawu danych.

-   Wybierz elementy w **źródeł danych** okna i przeciągnij je na formularzu. Aby uzyskać więcej informacji, zobacz [formanty formularzy systemu Windows powiązać z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

-   Dodaj więcej zapytań do elementów TableAdapter.

-   Dodaj logikę walidacji do zdarzeń <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> tabel danych w zestawie danych. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Zobacz także

- [Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Sprawdzanie poprawności danych](../data-tools/validate-data-in-datasets.md)