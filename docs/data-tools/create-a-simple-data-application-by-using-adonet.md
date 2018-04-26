---
title: Tworzenie prostej aplikacji danych przy użyciu pakietu ADO.NET w programie Visual Studio
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3d0b60bb4e7048e2dc49774ec69d3eea4fc0ce6c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Tworzenie prostej aplikacji danych przy użyciu pakietu ADO.NET

Podczas tworzenia aplikacji, która obsługuje dane w bazie danych można wykonywać podstawowe zadania, takie jak definiowanie parametry połączenia, wstawiania danych i uruchamianie procedur składowanych. Wykonując w tym temacie, można wykryć jak wchodzić w interakcję z bazą danych z wewnątrz prostą aplikację "formularzy nad danymi" formularzy systemu Windows za pomocą Visual C# lub Visual Basic i ADO.NET.  Wszystkie technologie danych .NET — łącznie z zestawów danych LINQ do SQL i programu Entity Framework — ostatecznie wykonaj kroki, które są bardzo podobne do tych przedstawionych w tym artykule.

 W tym artykule przedstawiono prosty sposób, aby pobrać dane z bazy danych w sposób bardzo szybko. Jeśli aplikacja wymaga do modyfikacji danych w sposób nieuproszczony i zaktualizować bazę danych, należy rozważyć przy użyciu programu Entity Framework i danych powiązanie formantów interfejsu użytkownika na zmiany w danych są synchronizowane automatycznie.

> [!IMPORTANT]
> Aby zachować prostego kodu, nie ma wśród nich obsługi wyjątków gotowe do produkcji.

## <a name="prerequisites"></a>Wymagania wstępne

Aby utworzyć aplikację, będą potrzebne:

-   Program Visual Studio.

-   SQL Server Express LocalDB. Jeśli nie masz programu SQL Server Express LocalDB, można zainstalować go z [strony pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express).

W tym temacie założono, że znasz podstawowych funkcji programu Visual Studio IDE i można utworzyć aplikacji formularzy systemu Windows, dodać formularzy do projektu, przycisków i innych formantów na formularzach, ustaw właściwości formantów i zdarzenia prostego kodu. Jeśli nie masz doświadczenia z tych zadań, zaleca się wykonanie [wprowadzenie do języka Visual C# i Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) tematu przed skorzystaniem z tego przewodnika.

## <a name="set-up-the-sample-database"></a>Konfigurowanie przykładowej bazy danych

Tworzenie przykładowej bazy danych, wykonaj następujące czynności:

1. W programie Visual Studio Otwórz **Eksploratora serwera** okna.

2. Kliknij prawym przyciskiem myszy **połączenia danych** i wybierz polecenie ** Tworzenie nowej bazy danych serwera SQL... ".

3. W **nazwy serwera** tekst wprowadź **(localdb) \mssqllocaldb**.

4. W **nowej nazwy bazy danych** tekst wprowadź **sprzedaży**, a następnie wybierz **OK**.

     Pustych **sprzedaży** bazy danych jest tworzony i dodawany do węzła połączenia danych w Eksploratorze serwera.

5. Kliknij prawym przyciskiem myszy **sprzedaży** połączenie danych i wybierz **nowe zapytanie**.

     Zostanie otwarte okno edytora zapytań.

6. Kopiuj [skryptu sprzedaży języka Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) do Schowka.

7. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.

     Po pewnym czasie zapytanie kończy wykonywanie i są tworzone obiekty bazy danych. Baza danych zawiera dwie tabele: klienta oraz zleceń. Te tabele nie zawierają danych początkowo, ale możesz dodać dane po uruchomieniu aplikacji, które zostaną utworzone. Baza danych zawiera również czterech prostych procedur składowanych.

## <a name="create-the-forms-and-add-controls"></a>Utwórz formularze i Dodaj formanty

1.  Utwórz projekt aplikacji formularzy systemu Windows, a następnie nadaj mu nazwę SimpleDataApp.

     Program Visual Studio tworzy projekt i kilka plików, w tym pusty formularz systemu Windows o nazwie Form1.

2.  Dodaj dwa formularze systemu Windows do projektu, aby miała trzy formularzy, a następnie nadaj im następujące nazwy:

    -   Nawigacji

    -   NewCustomer

    -   FillOrCancel

3.  Dla każdego formularza Dodaj pola tekstowe, przycisków i innych kontrolek, które pojawiają się na poniższych ilustracjach. Dla każdego formantu można ustawić właściwości, które w tabelach opisano.

    > [!NOTE]
    >  Pole grupy i formantów etykiet, Dodaj przejrzystości, ale nie są używane w kodzie.

 **Formularz nawigacji**

 ![Okno dialogowe nawigacji](../data-tools/media/simpleappnav.png "SimpleAppNav")

|Formanty formularza nawigacji|Właściwości|
|--------------------------------------|----------------|
|Przycisk|Nazwa = btnGoToAdd|
|Przycisk|Name = btnGoToFillOrCancel|
|Przycisk|Nazwa = btnExit|

 **Formularz NewCustomer**

 ![Dodawanie nowego klienta i złóż zamówienie](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")

|Formanty formularza NewCustomer|Właściwości|
|---------------------------------------|----------------|
|TextBox|Nazwa = txtCustomerName|
|TextBox|Nazwa = txtCustomerID<br /><br /> ReadOnly = True|
|Przycisk|Nazwa = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maksymalna = 5000<br /><br /> Nazwa = numOrderAmount|
|Element DateTimePicker|Format = krótki<br /><br /> Nazwa = dtpOrderDate|
|Przycisk|Nazwa = btnPlaceOrder|
|Przycisk|Nazwa = btnAddAnotherAccount|
|Przycisk|Nazwa = btnAddFinish|

 **Formularz FillOrCancel**

 ![Wypełnij lub anulowania zamówienia](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")

|Formanty formularza FillOrCancel|Właściwości|
|----------------------------------------|----------------|
|TextBox|Nazwa = txtOrderID|
|Przycisk|Nazwa = btnFindByOrderID|
|Element DateTimePicker|Format = krótki<br /><br /> Nazwa = dtpFillDate|
|Formant DataGridView|Nazwa = dgvCustomerOrders<br /><br /> ReadOnly = True<br /><br /> RowHeadersVisible = False|
|Przycisk|Nazwa = btnCancelOrder|
|Przycisk|Nazwa = btnFillOrder|
|Przycisk|Nazwa = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Przechowywanie parametrów połączenia
 Gdy aplikacja próbuje otworzyć połączenia z bazą danych, aplikacja musi mieć dostęp do ciągu połączenia. Aby uniknąć wprowadzenia ciąg ręcznie na każdym formularzu, umieść ciąg w pliku App.config w projekcie, a tworzenie metody, która zwraca ciąg, gdy metoda jest wywoływana z dowolnego formularza w aplikacji.

 Parametry połączenia można znaleźć, klikając prawym przyciskiem myszy **sprzedaży** połączenia danych w **Eksploratora serwera** i wybierając polecenie **właściwości**. Zlokalizuj **ConnectionString** właściwości, a następnie użyj klawiszy Ctrl + A klawisze Ctrl + C, zaznacz i skopiuj ciąg do Schowka.

1.  Jeśli używasz C# w **Eksploratora rozwiązań**, rozwiń węzeł **właściwości** węzła w ramach projektu, a następnie otwórz **Settings.settings** pliku.
    Jeśli używasz języka Visual Basic w **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**, rozwiń węzeł **mój projekt** węzeł, a następnie otwórz **Settings.settings** pliku.

2.  W **nazwa** kolumny, wprowadź `connString`.

3.  W **typu** listy, wybierz **(parametry połączenia)**.

4.  W **zakres** listy, wybierz **aplikacji**.

5.  W **wartość** kolumny, wprowadź ciąg połączenia (bez żadnych poza cudzysłowów), a następnie zapisz zmiany.

> [!NOTE]
> W rzeczywistej aplikacji, należy przechowywać parametry połączenia bezpiecznego, zgodnie z opisem w [parametry połączenia i pliki konfiguracyjne](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

##  <a name="write-the-code-for-the-forms"></a>Pisanie kodu dla formularzy

Ta sekcja zawiera krótkie omówienia działania każdego formularza. Umożliwia także kod, który definiuje podstawowej logiki, gdy kliknięto przycisk w formularzu.

### <a name="navigation-form"></a>Formularz nawigacji

Formularz nawigacji zostanie otwarte po uruchomieniu aplikacji. **Dodaj konto** przycisk otwiera NewCustomer formularza. **Wypełnienia lub anulowania zamówienia** przycisk otwiera FillOrCancel formularza. **Zakończenia** kliknięcie przycisku powoduje zamknięcie aplikacji.

#### <a name="make-the-navigation-form-the-startup-form"></a>Umożliwiają tworzą formularz startowy

Jeśli używasz C# w **Eksploratora rozwiązań**, otwórz plik Program.cs, a następnie zmień `Application.Run` wiersza do tego: `Application.Run(new Navigation());`

Jeśli używasz języka Visual Basic w **Eksploratora rozwiązań**, otwórz **właściwości** wybierz **aplikacji** , a następnie wybierz  **SimpleDataApp.Navigation** w **formularz startowy** listy.

#### <a name="create-auto-generated-event-handlers"></a>Tworzenie obsługi zdarzeń generowanych automatycznie

Kliknij dwukrotnie trzy przyciski nawigacji formularza można utworzyć metody obsługi zdarzeń pusta. Dwukrotne kliknięcie przycisków dodaje również automatycznie wygenerowany kod w pliku kodu projektanta, który umożliwia kliknij przycisk wywołać zdarzenie.

#### <a name="add-code-for-the-navigation-form-logic"></a>Dodaj kod logiki formularza nawigacji

Na stronie kodu formularza nawigacji pełną treść metody dla trzech przycisku kliknięcie uchwytów zdarzeń jak pokazano w poniższym kodzie.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>Formularz NewCustomer

Gdy wprowadź nazwę klienta, a następnie wybierz **Utwórz konto** przycisk, formularz NewCustomer tworzy konto klienta, a program SQL Server zwraca wartość tożsamości jako nowego identyfikatora klienta. Można zdefiniować kolejność dla nowego konta przez określenie kwotę i dat zamówienia i wybierając **złóż zamówienie** przycisku.

#### <a name="create-auto-generated-event-handlers"></a>Tworzenie obsługi zdarzeń generowanych automatycznie

Utwórz pusty kliknij program obsługi zdarzeń dla każdego przycisku w formularzu NewCustomer przez dwukrotne kliknięcie na każdej z czterech przycisków. Dwukrotne kliknięcie przycisków dodaje również automatycznie wygenerowany kod w pliku kodu projektanta, który umożliwia kliknij przycisk wywołać zdarzenie.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Dodaj kod NewCustomer logiki formularza

Aby ukończyć logiki formularza NewCustomer, wykonaj następujące kroki.

1. Przełącz `System.Data.SqlClient` przestrzeni nazw w zakresie, dzięki czemu nie trzeba pełni kwalifikuje się nazwy jej elementów członkowskich.

     ```csharp
     using System.Data.SqlClient;
     ```
     ```vb
     Imports System.Data.SqlClient
     ```

2. Dodaj niektóre zmienne i metody pomocnicze do klasy, jak pokazano w poniższym kodzie.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Pełna treść metody dla przycisku cztery kliknięcie uchwytów zdarzeń jak pokazano w poniższym kodzie.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>Formularz FillOrCancel

Formularz FillOrCancel przeprowadza kwerendę zwracane kolejności w przypadku wprowadź identyfikator zamówienia, a następnie kliknij przycisk **znaleźć kolejności** przycisku. Wiersz zwrócony zostanie wyświetlony w siatce danych tylko do odczytu. Możesz oznaczyć kolejności jak anulowane (X) w przypadku wybrania **anulowania zamówienia** przycisku, lub można określić kolejność wypełniony (F) w przypadku wybrania **wypełnienia kolejności** przycisku. W przypadku wybrania **znaleźć kolejności** przycisk ponownie, pojawi się zaktualizowany wiersz.

#### <a name="create-auto-generated-event-handlers"></a>Tworzenie obsługi zdarzeń generowanych automatycznie

Utwórz pusty kliknięcie uchwytów zdarzeń czterech przycisków w formularzu FillOrCancel przez dwukrotne kliknięcie przycisków. Dwukrotne kliknięcie przycisków dodaje również automatycznie wygenerowany kod w pliku kodu projektanta, który umożliwia kliknij przycisk wywołać zdarzenie.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Dodaj kod FillOrCancel logiki formularza

Aby ukończyć logiki formularza FillOrCancel, wykonaj następujące kroki.

1. Przełącz następujące dwie przestrzenie nazw w zakresie, dzięki czemu nie trzeba do pełnej kwalifikacji nazwy ich elementy członkowskie.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```
     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Dodaj metodę zmienną i pomocnika do klasy, jak pokazano w poniższym kodzie.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Pełna treść metody dla przycisku cztery kliknięcie uchwytów zdarzeń jak pokazano w poniższym kodzie.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Testowanie aplikacji

Wybierz **F5** klucz do tworzenia i testowania aplikacji po kodu każdego kliknij program obsługi zdarzeń, a następnie po Zakończ kodowania.

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
