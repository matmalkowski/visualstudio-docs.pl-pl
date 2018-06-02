---
title: Przekazywanie danych między formularzami
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: db1d993d745ea4dd1861dd086cea73cb16a08c81
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691215"
---
# <a name="pass-data-between-forms"></a>Przekazywanie danych między formularzami
Ten przewodnik zawiera instrukcje krok po kroku przekazywania danych z jednego formularza do innego. Przy użyciu klientów i tabele zamówień z Northwind, jeden formularz umożliwia użytkownikowi wybranie klienta, a drugi formularz zawiera wybranego klienta. W tym przewodniku przedstawiono sposób tworzenia metody na drugi formularz, który odbiera dane z pierwszego formularza.

> [!NOTE]
>  W tym przewodniku pokazano tylko jeden ze sposobów do przekazywania danych między formularzami. Istnieją inne opcje przekazywania danych do postaci, w tym tworzenie drugi Konstruktor na odbieranie danych, lub Tworzenie publicznej właściwości, które można ustawić za pomocą danych z pierwszego formularza.

 Zadania przedstawione w tym przewodniku obejmują:

-   Tworzenie nowego **aplikacji Windows Forms** projektu.

-   Tworzenie i konfigurowanie zestaw danych o [Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).

-   Wybieranie formantu ma zostać utworzony w formularzu, gdy przeciąganie elementów z **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Tworzenie formantu powiązanego z danymi przez przeciąganie elementów z **źródeł danych** okna w formularzu.

-   Tworzenie drugiej formy siatki, aby wyświetlić dane.

-   Tworzenie zapytań TableAdapter, można pobrać zleceń dla określonego klienta.

-   Przekazywanie danych pomiędzy formularzami.

## <a name="prerequisites"></a>Wymagania wstępne
W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.

1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [strony pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **magazynu danych i przetwarzania** obciążenia, lub jako poszczególnych składników.

2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowej kwerendy...** .

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.

## <a name="create-the-windows-forms-application"></a>Tworzenie aplikacji formularzy systemu Windows

#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt dla systemu Windows

1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.

4. Nazwij projekt **PassingDataBetweenForms**, a następnie wybierz pozycję **OK**.

     **PassingDataBetweenForms** projektu jest tworzony i dodane do **Eksploratora rozwiązań**.

## <a name="create-the-data-source"></a>Utwórz źródło danych

#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.

2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** uruchomić **konfiguracji źródła danych** kreatora.

3.  Wybierz **bazy danych** na **wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

4.  Na **wybierz model bazy danych** Sprawdź, czy **Dataset** jest określona, a następnie kliknij przycisk **dalej**.

5.  Na **wybierz połączenie danych** wykonaj jedną z następujących czynności:

    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    -   Wybierz **nowe połączenie** można uruchomić **połączenia Dodawanie i modyfikowanie** okno dialogowe.

6.  Jeśli baza danych wymaga hasła i włączono opcję, aby obejmować dane poufne, wybierz opcję, a następnie kliknij przycisk **dalej**.

7.  Na **zapisać parametry połączenia w pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

8.  Na **wybierz obiekty bazy danych** rozwiń pozycję **tabel** węzła.

9. Wybierz **klientów** i **zamówień** tabel, a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu i **klientów** i **zamówień** tabele są wyświetlane w **źródeł danych** okna.

## <a name="create-the-first-form-form1"></a>Tworzenie pierwszego formularza (Form1)
 Możesz utworzyć siatki powiązanych z danymi ( <xref:System.Windows.Forms.DataGridView> kontroli), przeciągając **klientów** węzła z **źródeł danych** okna na formularzu.

#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Aby utworzyć siatki powiązane z danymi w formularzu

-   Przeciągnij głównym **klientów** węzła z **źródeł danych** okna na **Form1**.

     A <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania rekordy są wyświetlane na **Form1**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane na pasku składnika.

## <a name="create-the-second-form-form2"></a>Tworzenie drugiej formy (formularz2)

#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Aby utworzyć drugi formularz do przekazywania danych do

1.  Z **projektu** menu, wybierz **dodać formularza systemu Windows**.

2.  Pozostaw nazwę domyślną **formularz2**i kliknij przycisk **Dodaj**.

3.  Przeciągnij głównym **zamówień** węzła z **źródeł danych** okna na **formularz2**.

     A <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania rekordy są wyświetlane na **formularz2**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane na pasku składnika.

4.  Usuń **OrdersBindingNavigator** zasobnika składnika.

     **OrdersBindingNavigator** zniknie z **formularz2**.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Dodaj zapytanie TableAdapter do formularz2 załadować zamówień wybranego klienta na Form1

#### <a name="to-create-a-tableadapter-query"></a>Aby utworzyć zapytanie TableAdapter

1.  Kliknij dwukrotnie **NorthwindDataSet.xsd** w pliku **Eksploratora rozwiązań**.

2.  Kliknij prawym przyciskiem myszy **OrdersTableAdapter**i wybierz **Dodaj zapytanie**.

3.  Pozostaw opcję domyślną **instrukcji SQL użyj**, a następnie kliknij przycisk **dalej**.

4.  Pozostaw opcję domyślną **SELECT, która zwraca wiersze**, a następnie kliknij przycisk **dalej**.

5.  Dodaj klauzulę WHERE zapytania, aby powrócić `Orders` na podstawie `CustomerID`. Zapytanie powinny być podobne do następujących:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    >  Sprawdź składnię odpowiedni parametr bazy danych. Na przykład w programie Microsoft Access w klauzuli WHERE będzie wyglądać: `WHERE CustomerID = ?`.

6.  Kliknij przycisk **Dalej**.

7.  Aby uzyskać **wpisać nazwę DataTableMethod**, typ `FillByCustomerID`.

8.  Wyczyść **zwraca DataTable** , a następnie kliknij przycisk **dalej**.

9. Kliknij przycisk **Zakończ**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Tworzenie metody na formularz2 do przekazywania danych do

#### <a name="to-create-a-method-to-pass-data-to"></a>Aby utworzyć metodę do przekazywania danych do

1.  Kliknij prawym przyciskiem myszy **formularz2**i wybierz **kod widoku** otworzyć **formularz2** w **edytora kodu**.

2.  Dodaj następujący kod do **formularz2** po `Form2_Load` metody:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Tworzenie metody na Form1 przekazywania danych do wyświetlenia formularz2

#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Aby utworzyć metodę do przekazywania danych do formularz2

1.  W **Form1**, kliknij prawym przyciskiem myszy siatka danych klienta, a następnie kliknij przycisk **właściwości**.

2.  W **właściwości** okna, kliknij przycisk **zdarzenia**.

3.  Kliknij dwukrotnie **CellDoubleClick** zdarzeń.

     Edytor kodu zostanie wyświetlony.

4.  Należy zaktualizować definicję metody do dopasowania w poniższym przykładzie:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

#### <a name="to-run-the-application"></a>Aby uruchomić aplikację

-   Naciśnij klawisz F5, aby uruchomić aplikację.

-   Kliknij dwukrotnie rekord klienta w **Form1** otworzyć **formularz2** z klienta.

## <a name="next-steps"></a>Następne kroki

Istnieje kilka kroków, które można wykonać po przekazywanie danych pomiędzy formularzami, w zależności od wymagań aplikacji. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

-   Edytowanie zestawu danych, aby dodać lub usunąć obiekty bazy danych. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Dodawanie funkcji, aby zapisać danych w bazie danych. Aby uzyskać więcej informacji, zobacz [zapisać danych w bazie danych](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Zobacz także

- [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)