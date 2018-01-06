---
title: "Wskazówki: Tworzenie aplikacji warstwowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 7cc4d8420cd823964aeed790a412e462b14634c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Wskazówki: tworzenie aplikacji warstwowych
*N-warstwowa* dane aplikacji są aplikacjom dostęp do danych i są podzielone na kilka logicznych warstw, lub *warstw*. Rozdzielić składniki aplikacji odrębny warstw zwiększa łatwość konserwacji i skalowalność aplikacji. Robi to przez włączenie ułatwia przyjęcie nowych technologii, które można zastosować do pojedynczej warstwie bez konieczności ponownego zaprojektowania całego rozwiązania. Architektura N-warstwowa zawiera warstwę prezentacji warstwy środkowej i warstwy danych. Warstwy środkowej obejmują zazwyczaj Warstwa dostępu do danych, warstwy logiki biznesowej i udostępniane składniki, takie jak uwierzytelniania i weryfikacji. Warstwa danych zawiera relacyjnej bazy danych. Aplikacje warstwowe zwykle przechowuj poufnych informacji w warstwę dostępu do danych w warstwie środkowej do obsługi izolacji od użytkowników końcowych, którzy uzyskują dostęp do warstwy prezentacji. Aby uzyskać więcej informacji, zobacz [N-warstwowa danych aplikacji — omówienie](../data-tools/n-tier-data-applications-overview.md).  
  
Jest jednym ze sposobów oddzielnych różnych warstw w n poziomowej aplikacji do tworzenia projektów discrete dla każdej warstwy, które mają zostać uwzględnione w aplikacji. Typizowane zbiory danych zawierają `DataSet Project` właściwość określa, które projekty wygenerowanego zestawu danych i `TableAdapter` kod powinien przejść do.  
  
W tym przewodniku pokazano, jak rozdzielić zestawu danych i `TableAdapter` kodu w projektach biblioteki klas odrębny przy użyciu **Projektant obiektów Dataset**. Po oddzieleniu zestawu danych i kod TableAdapter, utworzysz [usług Windows Communication Foundation oraz usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) usługi do wywołania w warstwie dostępu do danych. Na koniec spowoduje utworzenie aplikacji Windows Forms jako warstwy prezentacji. Ta warstwa uzyskuje dostęp do danych z usługi danych.  
  
Podczas tego przewodnika wykonasz następujące czynności:  
  
-   Utwórz nowe rozwiązanie warstwowe, który będzie zawierać wiele projektów.  
  
-   Dodaj dwa projektów biblioteki klas do rozwiązania warstwowego.  
  
-   Tworzenie typizowanego zestaw danych za pomocą **Kreator konfiguracji źródła danych**.  
  
-   Oddziel wygenerowany [TableAdapters](create-and-configure-tableadapters.md) i kod zestawu danych w projektach dyskretnych.  
  
-   Tworzenie usługi Windows Communication Foundation (WCF) do wywołania w warstwie dostępu do danych.  
  
-   Tworzenie funkcji w usłudze do pobierania danych z warstwy dostępu do danych.  
  
-   Tworzenie aplikacji Windows Forms jako warstwy prezentacji.  
  
-   Tworzenie formantów formularzy systemu Windows, które są powiązane ze źródłem danych.  
  
-   Pisanie kodu do wypełniania danych w tabelach.  
  
![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo") wersję wideo tego tematu, zobacz [wideo sposobu: tworzenie aplikacji warstwowych dane](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.  
  
1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania wersjach programu SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **tworzenia klasycznych aplikacji .NET** obciążenia, lub jako poszczególnych składników.  
  
2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:  

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowej kwerendy...** .  

       Zostanie otwarte okno edytora zapytań.  

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.  

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.  

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.  
  
## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Tworzenie rozwiązania N-warstwowa i biblioteki klas do przechowywania obiektów Dataset (DataEntityTier)  
 Pierwszym krokiem tego przewodnika jest tworzenie rozwiązania i dwóch projektów biblioteki klas. Biblioteka pierwszym klasy będą przechowywane dataset (wygenerowany wpisanych klasy DataSet i DataTables, w którym będą przechowywane dane aplikacji). Ten projekt jest używany jako warstwa jednostki danych aplikacji i zwykle znajduje się w warstwy środkowej. Datasetis, używany do tworzenia początkowego zestawu danych i automatycznie oddzielenie kodu do bibliotek klas dwa.  
  
> [!NOTE]
>  Pamiętaj poprawnie nazwę projektu i rozwiązania, przed kliknięciem przycisku **OK**. W ten sposób ułatwi Ci w tym przewodniku.  
  
#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Aby utworzyć rozwiązanie warstwowe i DataEntityTier biblioteki klas  

1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .  
  
2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.  

3. W środkowym okienku wybierz **biblioteki klas** typu projektu.  
  
4. Nazwij projekt **DataEntityTier**.  
  
5. Nazwa rozwiązania **NTierWalkthrough**, a następnie wybierz pozycję **OK**.  
  
     To rozwiązanie NTierWalkthrough, które zawiera projekt DataEntityTier jest tworzony i dodawany do **Eksploratora rozwiązań**.  
  
## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Tworzenia biblioteki klas, aby pomieścić TableAdapters (DataAccessTier)  
 Następnym krokiem po utworzeniu projektu DataEntityTier jest utworzyć innego projektu biblioteki klas. Ten projekt będzie przechowywać wygenerowany `TableAdapter`s i nosi nazwę *warstwy dostępu do danych* aplikacji. Warstwa dostępu do danych zawiera informacje, które jest wymagany do połączenia z bazą danych i zwykle znajduje się w warstwy środkowej.  
  
#### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Do tworzenia biblioteki klas osobne dla TableAdapters  
  
1.  Kliknij prawym przyciskiem myszy w ramach rozwiązania w Eksploratorze rozwiązań i wybierz polecenie **Dodaj**, **nowy projekt...** .  
  
2.  W **nowy projekt** okno dialogowe, w środkowym okienku, wybierz opcję **biblioteki klas**.  
  
3.  Nazwij projekt **DataAccessTier** i wybierz polecenie **OK**.  
  
     Projekt DataAccessTier jest tworzony i dodawany do rozwiązania NTierWalkthrough.  
  
## <a name="creating-the-dataset"></a>Tworzenie zestawu danych  
 Następnym krokiem jest tworzenie typizowanego zestaw danych. Typizowane zbiory danych są tworzone za pomocą obu klasy dataset (w tym klasy DataTables) i `TableAdapter` klas w jednym projekcie. (Wszystkie klasy są generowane w jednym pliku). Po oddzieleniu zestawu danych i `TableAdapter`s do różnych projektów, jest klasa zestawu danych, która została przeniesiona do innych projektów, pozostawiając `TableAdapter` klasy do oryginalnego projektu. W związku z tym utworzyć zestawu danych w projekcie, który będzie zawierać ostatecznie `TableAdapter`s (projekt DataAccessTier). Spowoduje utworzenie zestawu danych za pomocą **Kreator konfiguracji źródła danych**.  
  
> [!NOTE]
>  Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje dotyczące sposobu konfigurowania przykładowej bazy danych Northwind, zobacz [porady: Instalowanie przykładowe bazy danych](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych  
  
1.  Wybierz DataAccessTier w **Eksploratora rozwiązań**.  
  
2.  Na **danych** menu, wybierz opcję **Pokaż źródeł danych**.  
  
3.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
4.  Na **wybierz typ źródła danych** wybierz pozycję **bazy danych** , a następnie wybierz **dalej**.  
  
5.  Na **wybierz połączenie danych** wykonaj jedną z następujących czynności:  
  
     Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
     —lub—  
  
     Wybierz **nowe połączenie** otworzyć **Dodawanie połączenia** okno dialogowe.  
  
6.  Jeśli baza danych wymaga hasła, wybierz opcję, aby obejmować dane poufne, a następnie wybierz **dalej**.  
  
    > [!NOTE]
    >  W przypadku wybrania pliku lokalnej bazy danych (zamiast połączenia z programem SQL Server) może zostać poproszony, jeśli chcesz dodać plik do projektu. Wybierz **tak** można dodać pliku bazy danych do projektu.  
  
7.  Wybierz **dalej** na **zapisać parametry połączenia do pliku konfiguracji aplikacji** strony.  
  
8.  Rozwiń węzeł **tabel** węzła na **wybierz obiekty bazy danych użytkownika** strony.  
  
9.  Zaznacz pola wyboru dla **klientów** i **zamówień** tabel, a następnie wybierz pozycję **Zakończ**.  
  
     NorthwindDataSet zostanie dodany do projektu DataAccessTier i pojawia się w **źródeł danych** okna.  
  
## <a name="separating-the-tableadapters-from-the-dataset"></a>Oddzielanie TableAdapters z zestawu danych  
 Po utworzeniu zestawu danych z TableAdapters należy oddzielić wygenerowaną klasę zestawu danych. Możesz to zrobić przez ustawienie **projektu DataSet** właściwości do nazwy projektu do przechowywania rozdzielonych limit klasy dataset.  
  
#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Do rozdzielania TableAdapters z zestawu danych  
  
1.  Kliknij dwukrotnie **NorthwindDataSet.xsd** w **Eksploratora rozwiązań** można otworzyć zestawu danych w **Projektant obiektów Dataset**.  
  
2.  Wybierz pusty obszar na projektanta.  
  
3.  Zlokalizuj **projektu DataSet** w węźle **właściwości** okna.  
  
4.  W **projektu DataSet** listy, wybierz **DataEntityTier**.  
  
5.  Na **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.  
  
 Zestaw danych i TableAdapters są podzielone na dwie klasy projektów bibliotek. Projekt, który pierwotnie teraz zawarty całego zestawu danych (DataAccessTier) zawiera tylko TableAdapters. Projekt wymienionych na liście **projektu DataSet** właściwość (DataEntityTier) zawiera typizowanego obiektu dataset: NorthwindDataSet.Dataset.Designer.vb (lub NorthwindDataSet.Dataset.Designer.cs).  
  
> [!NOTE]
>  Po oddzieleniu zestawów danych i TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące klasy częściowe dataset w projekcie nie zostaną automatycznie przeniesione. Istniejące klasy częściowy zestaw danych należy ręcznie przenieść do projektu dataset.  
  
## <a name="creating-a-new-service-application"></a>Tworzenie nowej aplikacji usługi  
W tym przewodniku pokazano, jak dostęp do warstwy dostępu do danych za pomocą usługi WCF, więc warto utworzyć nową aplikację usługi WCF.  
  
#### <a name="to-create-a-new-wcf-service-application"></a>Aby utworzyć nową aplikację usługi WCF  
  
1.  Kliknij prawym przyciskiem myszy w ramach rozwiązania w Eksploratorze rozwiązań i wybierz polecenie **Dodaj**, **nowy projekt...** .  
  
2.  W **nowy projekt** okno dialogowe, w okienku po lewej stronie wybierz **WCF**.  W środkowym okienku wybierz **biblioteki usługi WCF**.  
  
3.  Nazwij projekt **DataService** i wybierz **OK**.  
  
     Usługi danych projektu jest tworzony i dodawany do rozwiązania NTierWalkthrough.  
  
## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Tworzenie metod w warstwie dostępu do danych do zwrócenia z klientami oraz zamówienia danych  
 Usługi danych ma wywołać dwie metody w warstwie dostępu do danych: GetCustomers i GetOrders. Te metody zwróci tabeli klientów Northwind i zleceń. Tworzenie metody GetCustomers i GetOrders w projekcie DataAccessTier.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Można utworzyć metody w warstwie dostępu do danych, która zwraca tabelę klientów  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie NorthwindDataset.xsd można otworzyć zestawu danych.
  
2.  Kliknij prawym przyciskiem myszy CustomersTableAdapter, a następnie kliknij przycisk **Dodaj zapytanie**.  
  
3.  Na **wybierz typ polecenia** pozostaw wartość domyślną **instrukcji SQL użyj** i kliknij przycisk **dalej**.  
  
4.  Na **wybierz typ zapytania** pozostaw wartość domyślną **SELECT, która zwraca wiersze** i kliknij przycisk **dalej**.  
  
5.  Na **Określ instrukcję SQL SELECT** , pozostaw domyślne zapytanie i kliknij przycisk **dalej**.  
  
6.  Na **Wybierz metody do generowania** wpisz **GetCustomers** dla **nazwę metody** w **zwraca DataTable** sekcji.  
  
7.  Kliknij przycisk **Zakończ**.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Można utworzyć metody w warstwie dostępu do danych, która zwraca tabelę zleceń  
  
1.  Kliknij prawym przyciskiem myszy OrdersTableAdapter, a następnie kliknij przycisk **Dodaj zapytanie**.  
  
2.  Na **wybierz typ polecenia** pozostaw wartość domyślną **instrukcji SQL użyj** i kliknij przycisk **dalej**.  
  
3.  Na **wybierz typ zapytania** pozostaw wartość domyślną **SELECT, która zwraca wiersze** i kliknij przycisk **dalej**.  
  
4.  Na **Określ instrukcję SQL SELECT** , pozostaw domyślne zapytanie i kliknij przycisk **dalej**.  
  
5.  Na **Wybierz metody do generowania** wpisz **GetOrders** dla **nazwę metody** w **zwraca DataTable** sekcji.  
  
6.  Kliknij przycisk **Zakończ**.  
  
7.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Dodawanie warstwy dostępu do danych i odwołanie do jednostki danych do usługi danych  
 Usługi danych wymaga informacji z zestawu danych i TableAdapters, dlatego należy dodać odwołań do projektów DataEntityTier i DataAccessTier.  
  
#### <a name="to-add-references-to-the-data-service"></a>Aby dodać odwołania do usługi danych  
  
1.  Kliknij prawym przyciskiem myszy DataService w **Eksploratora rozwiązań** i kliknij przycisk **Dodaj odwołanie**.  
  
2.  Kliknij przycisk **projekty** karcie **Dodaj odwołanie** okno dialogowe.  
  
3.  Wybierz oba **DataAccessTier** i **DataEntityTier** projektów.  
  
4.  Kliknij przycisk **OK**.  
  
## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Dodawanie funkcji do usługi w celu wywołania GetCustomers i metod GetOrders danych dostępu do warstwy  
 Teraz, warstwie dostępu do danych zawiera metody służące do zwracanych danych, należy utworzyć metody w usłudze danych do wywołania metody w warstwie dostępu do danych.  
  
> [!NOTE]
>  Dla projektów C#, należy dodać odwołanie do `System.Data.DataSetExtensions` zestawu dla następującego kodu do kompilacji.  
  
#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Aby utworzyć funkcje GetCustomers i GetOrders usługi danych  
  
1.  W **DataService** projektu, kliknij dwukrotnie IService1.vb lub IService1.cs.  
  
2.  Dodaj następujący kod pod **Dodaj tutaj operacje usługi** komentarza:  
  
    ```vb  
    <OperationContract()> _  
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable  
  
    <OperationContract()> _  
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable  
    ```  
  
    ```csharp  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();  
  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();  
    ```  
  
3.  W projekcie usługi danych kliknij dwukrotnie Service1.vb (lub Service1.cs).  
  
4.  Dodaj następujący kod do klasy Service1:  
  
    ```vb  
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers  
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
        Return CustomersTableAdapter1.GetCustomers()  
    End Function  
  
    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders  
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
        Return OrdersTableAdapter1.GetOrders()  
    End Function  
    ```  
  
    ```csharp  
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
             CustomersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();  
        return CustomersTableAdapter1.GetCustomers();  
    }  
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
             OrdersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();  
        return OrdersTableAdapter1.GetOrders();  
    }  
    ```  
  
5.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Tworzenie warstwy prezentacji, aby wyświetlić dane z usługi danych  
 Teraz, gdy rozwiązanie zawiera usługę danych, która ma metody, które wywołują warstwie dostępu do danych, należy utworzyć inny projekt, które wywołują usługi danych i przedstawiają dane użytkowników. W ramach tego przewodnika tworzenia aplikacji formularzy systemu Windows; jest to warstwa prezentacji aplikacji wielowarstwowych.  
  
#### <a name="to-create-the-presentation-tier-project"></a>Aby utworzyć projekt warstwy prezentacji  
  
1.  Kliknij prawym przyciskiem myszy w ramach rozwiązania w Eksploratorze rozwiązań i wybierz polecenie **Dodaj**, **nowy projekt...** .  
  
2.  W **nowy projekt** okno dialogowe, w okienku po lewej stronie wybierz **Windows Desktop klasycznego**. W środkowym okienku wybierz **aplikacji formularzy systemu Windows**.  
  
3.  Nazwij projekt **PresentationTier** i kliknij przycisk **OK**.  
  
    Projekt PresentationTier jest tworzony i dodawany do rozwiązania NTierWalkthrough.  
  
## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Ustawienia projektu PresentationTier jako projekt startowy  
Zaplanujemy PresentationTier projekt jako projekt startowy do rozwiązania, ponieważ jest on aplikacji klienckiej rzeczywista, która służy do przedstawienia i interakcję z danymi.  
  
#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Aby ustawić nowy projekt warstwy prezentacji jako projekt startowy  
  
-   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **PresentationTier** i kliknij przycisk **Ustaw jako projekt startowy**.  
  
## <a name="adding-references-to-the-presentation-tier"></a>Dodawanie odwołań do warstwy prezentacji  
 Aplikacja kliencka PresentationTier wymaga odwołania do usługi z usługą danych, aby uzyskać dostęp do metod w usłudze. Ponadto odwołanie do zestawu danych są wymagane do włączenia typ udostępniania przez usługę WCF. Przed włączeniem typ udostępniania za pośrednictwem usługi danych kodu dodawana do klasy częściowej zestawu danych nie będą dostępne do warstwy prezentacji. Ponieważ zazwyczaj kodu, takich jak sprawdzanie poprawności są dodawane do wiersz i kolumnę, zmiana zdarzenia tabelę danych, prawdopodobne jest, że można uzyskać dostęp do tego kodu z klienta.  
  
#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Aby dodać odwołanie do warstwy prezentacji  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy PresentationTier i wybierz **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, wybierz opcję **projekty** kartę.  
  
3.  Wybierz **DataEntityTier** i wybierz polecenie **OK**.  
  
#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Aby dodać odwołania do usługi do warstwy prezentacji  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy PresentationTier i wybierz **Dodaj odwołanie do usługi**.  
  
2.  W **Dodaj odwołanie do usługi** okno dialogowe, wybierz opcję **odnajdowania**.  
  
3.  Wybierz **Service1** i wybierz polecenie **OK**.  
  
    > [!NOTE]
    >  Jeśli masz wiele usług na komputerze bieżącym, wybierz usługę utworzonego wcześniej w tym przewodniku (usługa zawiera metody GetCustomers i GetOrders).  
  
## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Dodawanie DataGridViews do formularza w celu wyświetlania danych zwróconych przez usługi danych  
 Po dodaniu odwołania do usługi z usługą danych **źródeł danych** okna jest automatycznie wypełniane przy użyciu danych zwracanych przez usługę.  
  
#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Aby dodać dane dwa powiązany DataGridViews do formularza  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt PresentationTier.  
  
2.  W **źródeł danych** okna, rozwiń węzeł **NorthwindDataSet** i Znajdź **klientów** węzła.  
  
3.  Przeciągnij **klientów** węzła na Form1.  
  
4.  W **źródeł danych** okna, rozwiń węzeł **klientów** węzła i Znajdź pokrewny **zamówień** węzła ( **zamówień** węzła zagnieżdżona w  **Klienci** węzła).  
  
5.  Przeciągnij pokrewny **zamówień** węzła na Form1.  
  
6.  Utwórz `Form1_Load` obsługi zdarzeń, klikając dwukrotnie pusty obszar formularza.  
  
7.  Dodaj następujący kod do `Form1_Load` obsługi zdarzeń.  
  
    ```vb  
    Dim DataSvc As New ServiceReference1.Service1Client  
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)  
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)  
    ```  
  
    ```csharp  
    ServiceReference1.Service1Client DataSvc =   
        new ServiceReference1.Service1Client();  
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());  
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());  
    ```  
  
## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Zwiększyć maksymalny rozmiar komunikatu dozwolony przez usługę  
Wartość domyślna właściwości MaxReceivedMessageSize nie jest wystarczająco duży, aby pomieścić dane pobrane z tabel Klienci i zamówienia. W poniższych krokach powoduje zwiększenie wartości 6553600. Zmieni wartość na komputerze klienckim, automatycznie aktualizuje odwołania do usługi.  
  
> [!NOTE]
>  Niższe domyślny rozmiar ma na celu ograniczenia narażenia na ataki (DoS). Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Aby zwiększyć wartości maxReceivedMessageSize  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie plik app.config w projekcie PresentationTier.  
  
2.  Zlokalizuj **maxReceivedMessage** rozmiaru atrybutu i zmień wartość na `6553600`.  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
Uruchom aplikację, naciskając klawisz **F5**. Dane z tabel Klienci i zamówienia jest pobierane z usługi danych i wyświetlane w formularzu.  
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po zapisaniu powiązanych danych w aplikacji systemu Windows. Można na przykład należy następujące ulepszenia w tej aplikacji:  
  
-   Dodawanie walidacji do zestawu danych. 
  
-   Dodaj dodatkowe metody do usługi do aktualizowania danych w bazie danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z zestawami danych w aplikacjach warstwowych](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md)   
 [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)