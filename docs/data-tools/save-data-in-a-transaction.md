---
title: 'Wskazówki: Zapisywanie danych w transakcji'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ec2ff00c4d355b2683c888fcdb6a333bf15e1b99
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Wskazówki: Zapisywanie danych w transakcji
W tym przewodniku pokazano, jak można zapisać danych w transakcji za pomocą <xref:System.Transactions> przestrzeni nazw. W tym przewodniku utworzysz aplikacji formularzy systemu Windows. Użyjesz Kreator konfiguracji źródła danych można utworzyć zestawu danych dla dwóch tabel w bazie danych Northwind. Zostanie dodana dane powiązane kontrolki formularza systemu Windows i będzie zmodyfikować kod używany w parametrze BindingNavigator na przycisk zapisywania do aktualizacji bazy danych wewnątrz elementu TransactionScope.

## <a name="prerequisites"></a>Wymagania wstępne
W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.

1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [strony pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **tworzenia klasycznych aplikacji .NET** obciążenia, lub jako poszczególnych składników.

2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowej kwerendy...** .

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.

## <a name="create-a-windows-forms-application"></a>Tworzenie aplikacji formularzy systemu Windows
 Pierwszym krokiem jest utworzenie **aplikacji Windows Forms**.

#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt dla systemu Windows

1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.

4. Nazwij projekt **SavingDataInATransactionWalkthrough**, a następnie wybierz pozycję **OK**.

     **SavingDataInATransactionWalkthrough** projektu jest tworzony i dodawany do **Eksploratora rozwiązań**.

## <a name="create-a-database-data-source"></a>Utwórz źródło danych bazy danych
 Ten krok używa **Kreator konfiguracji źródła danych** tworzenia źródła danych na podstawie `Customers` i `Orders` tabele w bazie danych Northwind.

#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1.  Na **danych** menu, wybierz opcję **Pokaż źródeł danych**.

2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.

3.  Na **wybierz typ źródła danych** ekranu wybierz **bazy danych**, a następnie wybierz **dalej**.

4.  Na **wybierz połączenie danych** wykonaj ekranu, jedną z następujących czynności:

    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         —lub—

    -   Wybierz **nowe połączenie** można uruchomić **połączenia Dodawanie i modyfikowanie** okno dialogowe i utworzyć połączenie z bazą danych Northwind.

5.  Jeśli baza danych wymaga hasła, wybierz opcję, aby obejmować dane poufne, a następnie wybierz **dalej**.

6.  Na **zapisać parametry połączenia w pliku konfiguracji aplikacji** ekranu wybierz **dalej**.

7.  Na **wybierz obiekty bazy danych** ekranu, a następnie rozwiń **tabel** węzła.

8.  Wybierz `Customers` i `Orders` tabel, a następnie wybierz **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu i `Customers` i `Orders` tabele są wyświetlane w **źródeł danych** okna.

## <a name="add-controls-to-the-form"></a>Dodawanie formantów do formularza
 Formanty powiązane z danymi można utworzyć, przeciągając elementy z **źródeł danych** okna na formularzu.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Aby utworzyć dane powiązane formantów w formularzu systemu Windows

-   W **źródeł danych** okna, rozwiń węzeł **klientów** węzła.

-   Przeciągnij głównym **klientów** węzła z **źródeł danych** okna na **Form1**.

     A <xref:System.Windows.Forms.DataGridView> kontroli i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania rekordy są wyświetlane w formularzu. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane na pasku składnika.

-   Przeciągnij pokrewny **zamówień** węzła (nie głównym **zamówień** węzła, ale poniżej węzła powiązanej tabeli podrzędnej **faksów** kolumny) na poniższy formularz  **CustomersDataGridView**.

     A <xref:System.Windows.Forms.DataGridView> w formularzu. `OrdersTableAdapter` i <xref:System.Windows.Forms.BindingSource> są wyświetlane na pasku składnika.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Dodaj odwołanie do zestawu System.Transactions
 Użyj transakcji <xref:System.Transactions> przestrzeni nazw. Odwołanie projektu do zestawu system.transactions nie została dodana domyślnie, więc musisz ręcznie dodać ją.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Aby dodać odwołanie do pliku System.Transactions DLL

1.  Na **projektu** menu, wybierz opcję **Dodaj odwołanie**.

2.  Wybierz **System.Transactions** (na **.NET** kartę), a następnie wybierz **OK**.

     Odwołanie do **System.Transactions** zostanie dodany do projektu.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Zmodyfikuj kod w parametrze BindingNavigator SaveItem przycisku
 Do pierwszej tabeli na formularzu kodu jest dodawana domyślnie `click` zdarzeń Zapisz znajdującego się na <xref:System.Windows.Forms.BindingNavigator>. Należy ręcznie dodać kod, aby zaktualizować wszystkie dodatkowe tabele. W ramach tego przewodnika, firma Microsoft Refaktoryzuj istniejących Zapisz kod poza zapisywania przycisku kliknij program obsługi zdarzeń. Możemy również utworzyć kilka metod więcej umożliwiają korzystanie z funkcji określoną aktualizację oparte na Określa, czy wiersz musi być dodany lub usunięty.

#### <a name="to-modify-the-auto-generated-save-code"></a>Aby zmodyfikować automatycznie generowanej Zapisz kod

1.  Wybierz **zapisać** znajdującego się na **CustomersBindingNavigator** (przycisk z ikoną dyskietka).

2.  Zastąp `CustomersBindingNavigatorSaveItem_Click` metodę z następującym kodem:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

Aby uzgadnianie zmiany do powiązanych danych przebiega następująco:

-   Usuwanie rekordów podrzędnych. (W takim przypadku należy usunąć rekordy `Orders` tabeli.)

-   Usuwanie rekordów nadrzędnych. (W takim przypadku należy usunąć rekordy `Customers` tabeli.)

-   Wstawianie rekordów nadrzędnych. (W tym przypadku wstawiania rekordów w `Customers` tabeli.)

-   Wstawianie rekordów podrzędnych. (W tym przypadku wstawiania rekordów w `Orders` tabeli.)

#### <a name="to-delete-existing-orders"></a>Aby usunąć istniejące zlecenia

-   Dodaj następujące `DeleteOrders` metodę **Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

#### <a name="to-delete-existing-customers"></a>Aby usunąć istniejących klientów usługi

-   Dodaj następujące `DeleteCustomers` metodę **Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

#### <a name="to-add-new-customers"></a>Aby dodać nowych klientów

-   Dodaj następujące `AddNewCustomers` metodę **Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

#### <a name="to-add-new-orders"></a>Aby dodać nowe zlecenia

-   Dodaj następujące `AddNewOrders` metodę **Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

#### <a name="to-run-the-application"></a>Aby uruchomić aplikację

-   Wybierz **F5** do uruchomienia aplikacji.

## <a name="see-also"></a>Zobacz także

- [Porady: zapisywanie danych przy użyciu transakcji](../data-tools/save-data-by-using-a-transaction.md)
- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)