---
title: "Wskazówki: Tworzenie zestawu danych w Projektancie obiektów Dataset | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 44139e06a09fc2883c7a42202129bfd3c82343d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Wskazówki: tworzenie zestawu danych za pomocą narzędzia Projektant obiektów Dataset

W tym przewodniku spowoduje utworzenie zestawu danych za pomocą **Projektant obiektów Dataset**. Nastąpi przekierowanie przez proces tworzenia nowego projektu i dodawanie nowej **DataSet** element, aby go. Nauczysz się, w jaki sposób tworzyć tabele na podstawie tabel w bazie danych bez używania kreatora.  

Zadania przedstawione w tym przewodniku obejmują:  

-   Tworzenie nowego **aplikacji Windows Forms** projektu.  

-   Dodawanie pustą **DataSet** elementu do projektu.  

-   Tworzenie i konfigurowanie źródła danych w aplikacji przez utworzenie zestawu danych z **Projektant obiektów Dataset**.  
 
-   Tworzenie połączenia z bazą danych Northwind w **Eksploratora serwera**.  

-   Tworzenie tabel z elementami TableAdapter w zestawie danych na podstawie tabel istniejących w bazie danych.  

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.  
  
1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania wersjach programu SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **magazynu danych i przetwarzania** obciążenia, lub jako poszczególnych składników.  
  
2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:  

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowej kwerendy...** .  

       Zostanie otwarte okno edytora zapytań.  

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.  

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.  

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.  
  
## <a name="creating-a-new-windows-forms-application-project"></a>Tworzenie nowego projektu aplikacji Windows Forms  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>Aby utworzyć nowy projekt aplikacji Windows Forms  
  
1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .  
  
2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.  

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.  

4. Nazwij projekt **DatasetDesignerWalkthrough**, a następnie wybierz pozycję **OK**.  
  
     Visual Studio dodaje projekt do **Eksploratora rozwiązań** i wyświetlić nowy formularz w projektancie.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Dodawanie nowego zestawu danych do aplikacji  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Aby dodać nowy zestaw danych do projektu  
  
1.  Na **projektu** menu, wybierz opcję **Dodaj nowy element...** .  
  
     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
2.  W okienku po lewej stronie wybierz **danych**, a następnie wybierz pozycję **DataSet** w środkowym okienku.  
  
3.  Nazwa zestawu danych **NorthwindDataset**, a następnie wybierz pozycję **Dodaj**.  
  
     Visual Studio dodaje plik o nazwie **NorthwindDataset.xsd** do projektu i otwarcie go w **Projektant obiektów Dataset**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Tworzenie połączenia danych w Eksploratorze serwera  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Aby utworzyć połączenie z bazą danych Northwind  
  
1.  Na **widoku** menu, kliknij przycisk **Eksploratora serwera**.  
  
2.  W **Eksploratora serwera**, kliknij przycisk **Połącz z bazą danych** przycisku.  
  
3.  Utwórz połączenie z przykładową bazą danych Northwind.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Tworzenie tabel w zestawie danych  
W tej sekcji opisano sposób dodawania tabel do zestawu danych.  
  
#### <a name="to-create-the-customers-table"></a>Aby utworzyć tabelę Customers  
  
1.  Rozwiń węzeł połączenia danych utworzonego w **Eksploratora serwera**, a następnie rozwiń węzeł **tabel** węzła.  
  
2.  Przeciągnij **klientów** tabeli **Eksploratora serwera** na **Projektant obiektów Dataset**.  
  
     A **klientów** tabeli danych i **CustomersTableAdapter** są dodawane do zestawu danych.  
  
#### <a name="to-create-the-orders-table"></a>Aby utworzyć tabelę Orders  
  
-   Przeciągnij **zamówień** tabeli **Eksploratora serwera** na **Projektant obiektów Dataset**.  
  
     **Zamówień** tabeli danych **OrdersTableAdapter**i danych relacji między **klientów** i **zamówień** tabele są dodawane do zestaw danych.  
  
#### <a name="to-create-the-orderdetails-table"></a>Aby utworzyć tabelę OrderDetails  
  
-   Przeciągnij **szczegółów zamówienia** tabeli **Eksploratora serwera** na **Projektant obiektów Dataset**.  
  
     **Szczegółów zamówienia** tabeli danych **OrderDetailsTableAdapter**i relację danych między **zamówień** i **SzczegółyZamówienia** tabel zostaną dodane do zestawu danych.  
  
## <a name="next-steps"></a>Następne kroki  
  
### <a name="to-add-functionality-to-your-application"></a>Dodawanie funkcji do aplikacji  
  
-   Zapisywanie zestawu danych.  
  
-   Wybierz elementy w **źródeł danych** okna i przeciągnij je na formularzu. Aby uzyskać więcej informacji, zobacz [formanty formularzy systemu Windows powiązać z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Dodaj więcej zapytań do elementów TableAdapter. 
  
-   Dodaj logikę walidacji do zdarzeń <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> tabel danych w zestawie danych. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Zobacz także
[Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
[Powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[Sprawdzanie poprawności danych](../data-tools/validate-data-in-datasets.md)   
[Zapisywanie danych](../data-tools/saving-data.md)