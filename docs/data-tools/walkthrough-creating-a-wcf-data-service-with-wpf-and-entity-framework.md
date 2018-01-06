---
title: "Wskazówki: Tworzenie usługi danych WCF z WPF i strukturą Entity Framework | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 5c1d86d634579370565f2def7af233b4edffae53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Wskazówki: Tworzenie usługi danych WCF z WPF i strukturą Entity Framework
W tym przewodniku pokazano, jak utworzyć prostą [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] jest hostowana w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, a następnie do niego dostęp z aplikacji formularzy systemu Windows.  
  
W instruktażu wykonasz następujące czynności:  
  
-   Tworzenie aplikacji sieci Web do hosta [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Utwórz [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] reprezentujący tabeli klientów w bazie danych Northwind.  
  
-   Utwórz [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Tworzenie aplikacji klienckich i Dodaj odwołanie do [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Utworzenie powiązania danych z usługą i wygenerowanie interfejsu użytkownika.  
  
-   Opcjonalnie dodanie funkcji filtrowania do aplikacji.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.  
  
1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania wersjach programu SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **magazynu danych i przetwarzania** obciążenia, lub jako poszczególnych składników.  
  
2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:  

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowej kwerendy...** .  

       Zostanie otwarte okno edytora zapytań.  

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.  

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.  

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.  
  
## <a name="creating-the-service"></a>Tworzenie usługi  
Aby utworzyć [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], będzie dodać projekt sieci Web, Utwórz [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], a następnie Utwórz usługę z modelu.  
  
W pierwszym kroku dodasz projekt internetowy, który będzie hostował usługę.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-the-web-project"></a>Aby utworzyć projekt internetowy  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual Basic** lub **Visual C#** i **sieci Web** węzłów, a następnie wybierz pozycję **ASP. Aplikacja sieci Web NET** szablonu.  
  
3.  W **nazwa** tekst wprowadź **NorthwindWeb**, a następnie wybierz pozycję **OK** przycisku.  
  
4.  W **nowy projekt ASP.NET** okna dialogowego, **wybierz szablon** wybierz **pusty**, a następnie wybierz pozycję **OK** przycisku.  
  
W następnym kroku zostanie utworzony [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] reprezentujący tabeli klientów w bazie danych Northwind.  
  
#### <a name="to-create-the-entity-data-model"></a>Aby utworzyć model Entity Data Model  
  
1.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe Wybierz **danych** węzeł, a następnie wybierz pozycję **modelu danych jednostki ADO.NET** elementu.  
  
3.  W **nazwa** tekst wprowadź `NorthwindModel`, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Zostanie wyświetlony Kreator modelu Entity Data Model.  
  
4.  W kreatorze modelu danych jednostki na **wybierz zawartość modelu** wybierz pozycję **EF Designer z bazy danych** elementu, a następnie wybierz pozycję **dalej** przycisku.  
  
5.  Na **wybierz połączenie danych** wykonaj jedną z następujących czynności:  
  
    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
         —lub—  
  
    -   Wybierz **nowe połączenie** przycisk, aby skonfigurować nowe połączenie danych. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
6.  Jeśli baza danych wymaga hasła, wybierz **tak, Dołącz danych poufnych w parametrach połączenia** przycisk opcji, a następnie wybierz pozycję **dalej** przycisku.  
  
    > [!NOTE]
    >  Jeśli zostanie wyświetlone okno dialogowe, wybierz **tak** można zapisać pliku do projektu.  
  
7.  Na **wybierz wersję** wybierz pozycję **Entity Framework w wersji 5.0** przycisk opcji, a następnie wybierz pozycję **dalej** przycisku.  
  
    > [!NOTE]
    >  Aby korzystać z najnowszej wersji programu Entity Framework 6 w usługi WCF, należy zainstalować pakiet NuGet dostawcy Framework jednostki usługi danych WCF. Zobacz [przy użyciu programu WCF Data Services 5.6.0 Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8.  Na **wybierz obiekty bazy danych użytkownika** rozwiń pozycję **tabel** węzła, wybierz opcję **klientów** pole wyboru, a następnie wybierz pozycję **Zakończ** przycisk.  
  
     Zostanie wyświetlony diagram modelu jednostek, a do projektu zostanie dodany plik NorthwindModel.edmx.  
  
W następnym kroku utworzysz i przetestować usługę danych.  
  
#### <a name="to-create-the-data-service"></a>Aby utworzyć usługę danych  
  
1.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe Wybierz **sieci Web** węzeł, a następnie wybierz pozycję **5.6 usługi danych WCF** elementu.  
  
3.  W **nazwa** tekst wprowadź `NorthwindCustomers`, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Plik NorthwindCustomers.svc pojawia się w **edytora kodu**.  
  
4.  W **edytora kodu**, zlokalizuj pierwszy `TODO:` komentarzy i Zastąp kod następującym kodem:  
  
     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]  
  
5.  Zastąp komentarzy w `InitializeService` obsługi zdarzeń z następującym kodem:  
  
     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]  
  
6.  Na pasku menu wybierz **debugowania**, **uruchomić bez debugowania** do uruchamiania usługi. Zostanie otwarte okno przeglądarki i pojawi się w nim schemat XML usługi.  
  
7.  W **adres** pasek, wprowadź `Customers` na końcu adresu URL NorthwindCustomers.svc, a następnie wybierz pozycję **ENTER** klucza.  
  
     Zostanie wyświetlona reprezentacja XML danych znajdujących się w tabeli Klienci.  
  
    > [!NOTE]
    >  Czasami przeglądarka Internet Explorer błędnie interpretuje dane jako źródło danych RSS. Należy się upewnić, że opcja wyświetlania źródeł danych RSS jest wyłączona. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami usługi](../data-tools/troubleshooting-service-references.md).  
  
8.  Zamknij okno przeglądarki.  
  
W następnych krokach utworzysz aplikację kliencką opartą na interfejsie Windows Forms, która będzie korzystała z usługi.  
  
## <a name="creating-the-client-application"></a>Tworzenie aplikacji klienckiej  
 W celu utworzenia aplikacji klienckiej dodasz drugi projekt, dodasz odwołanie z projektu do usługi, skonfigurujesz źródło danych oraz utworzysz interfejs użytkownika, w którym będą wyświetlane dane z usługi.  
  
 W pierwszym kroku dodasz projekt Windows Forms do rozwiązania oraz nadasz mu status projektu startowego.  
  
#### <a name="to-create-the-client-application"></a>Aby utworzyć aplikację kliencką  
  
1.  Na pasku menu, wybierz plik, **Dodaj**, **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual Basic** lub **Visual C#** węzła i wybierz polecenie **systemu Windows** węzła, a następnie wybierz pozycję  **Aplikacji formularzy systemu Windows**.  
  
3.  W **nazwa** tekst wprowadź `NorthwindClient`, a następnie wybierz pozycję **OK** przycisku.  
  
4.  W **Eksploratora rozwiązań**, wybierz **NorthwindClient** węzła projektu.  
  
5.  Na pasku menu wybierz **projektu**, **Ustaw jako projekt startowy**.  
  
W następnym kroku spowoduje dodanie odwołania do usługi do [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] w projekcie sieci Web.  
  
#### <a name="to-add-a-service-reference"></a>Aby dodać odwołanie do usługi  
  
1.  Na pasku menu wybierz **projektu**, **Dodaj odwołanie do usługi**.  
  
2.  W **Dodaj odwołanie do usługi** oknie dialogowym wybierz **odnajdowania** przycisku.  
  
     Adres URL usługi NorthwindCustomers pojawia się w **adres** pola.  
  
3.  Wybierz **OK** przycisk, aby dodać odwołania do usługi.  
  
W następnym kroku skonfigurujesz źródła danych, aby umożliwić wiązanie danych do usługi.  
  
#### <a name="to-enable-data-binding-to-the-service"></a>Aby utworzyć powiązanie danych z usługą  
  
1.  Na pasku menu wybierz **widoku**, **inne okna**, **źródeł danych**.  
  
2.  W **źródeł danych** okna, wybierz **Dodaj nowe źródło danych** przycisku.  
  
3.  Na **wybierz typ źródła danych** strony **Kreator konfiguracji źródła danych**, wybierz **obiektu**, a następnie wybierz pozycję **dalej** przycisku .  
  
4.  Na **wybierz obiekty danych** rozwiń pozycję **NorthwindClient** węzeł, a następnie rozwiń węzeł **NorthwindClient.ServiceReference1** węzła.  
  
5.  Wybierz **klienta** pole wyboru, a następnie wybierz pozycję **Zakończ** przycisku.  
  
W następnym kroku utworzysz interfejsu użytkownika, które będą wyświetlane dane z usługi.  
  
#### <a name="to-create-the-user-interface"></a>Aby utworzyć interfejs użytkownika  
  
1.  W **źródeł danych** okna, otwórz menu skrótów **klientów** węzeł i wybierz polecenie **kopiowania**.  
  
2.  W **Form1.vb** lub **pliku Form1.cs** tworzą projektanta, otwórz menu skrótów i wybierz polecenie **Wklej**.  
  
     A <xref:System.Windows.Forms.DataGridView> kontroli, <xref:System.Windows.Forms.BindingSource> składnik, a <xref:System.Windows.Forms.BindingNavigator> składnika są dodawane do formularza.  
  
3.  Wybierz **CustomersDataGridView** kontroli, a następnie w **właściwości** zestaw okna **dokowania** właściwości **wypełnienia**.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **Form1** węzeł i wybierz polecenie **kod widoku** aby otworzyć edytora kodu i dodaj następujące instrukcje importu lub przy użyciu instrukcji w w górnej części pliku:  
  
    ```vb  
    Imports NorthwindClient.ServiceReference1  
    ```  
  
    ```csharp  
    using NorthwindClient.ServiceReference1;  
    ```  
  
5.  Dodaj następujący kod do `Form1_Load` obsługi zdarzeń:  
  
    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
            Dim proxy As New NorthwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))  
            Me.CustomersBindingSource.DataSource = proxy.Customers  
        End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(object sender, EventArgs e)  
    {  
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
    this.CustomersBindingSource.DataSource = proxy.Customers;  
    }  
  
    ```  
  
6.  W **Eksploratora rozwiązań**, otwórz plik NorthwindCustomers.svc menu skrótów i wybierz polecenie **Wyświetl w przeglądarce**. Zostanie otwarte okno przeglądarki Internet Explorer i pojawi się w nim schemat XML usługi.  
  
7.  Skopiuj adres URL z paska adresu przeglądarki Internet Explorer.  
  
8.  W kodzie dodanego w kroku 4, wybierz `http://localhost:53161/NorthwindCustomers.svc/` i zamień ją na adres URL, który został skopiowany.  
  
9. Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** do uruchomienia aplikacji. Zostaną wyświetlone informacje o kliencie.  
  
 Masz teraz działającą aplikację, która wyświetla listę klientów z usługi NorthwindCustomers. Jeśli chcesz udostępnić dodatkowe dane za pośrednictwem usługi, można zmodyfikować [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] uwzględnienie dodatkowych tabel z bazy danych Northwind.  
  
W następnym opcjonalnym kroku dowiesz się, jak filtrować dane zwracane przez usługę.  
  
## <a name="adding-filtering-capabilities"></a>Dodawanie funkcji filtrowania  
 W tym kroku dostosujesz aplikację w taki sposób, aby filtrowała dane według miejscowości zamieszkania klienta.  
  
#### <a name="to-add-filtering-by-city"></a>Aby dodać filtrowanie według miejscowości  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **Form1.vb** lub **pliku Form1.cs** węzeł i wybierz polecenie **Otwórz**.  
  
2.  Dodaj <xref:System.Windows.Forms.TextBox> kontroli i <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do formularza.  
  
3.  Otwórz menu skrótów <xref:System.Windows.Forms.Button> kontroli, a następnie wybierz pozycję **kod widoku**, a następnie dodaj następujący kod w `Button1_Click` obsługi zdarzeń:  
  
    ```vb  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
            Dim proxy As New northwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))  
            Dim city As String = TextBox1.Text  
  
            If city <> "" Then  
                Me.CustomersBindingSource.DataSource = From c In _  
             proxy.Customers Where c.City = city  
            End If  
  
        End Sub  
    ```  
  
    ```csharp  
    private void Button1_Click(object sender, EventArgs e)  
    {  
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));  
    string city = TextBox1.Text;  
  
    if (!string.IsNullOrEmpty(city)) {  
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;  
    }  
  
    }  
    ```  
  
4.  W poprzednim kodzie Zamień `http://localhost:53161/NorthwindCustomers.svc` z adresem URL z `Form1_Load` obsługi zdarzeń.  
  
5.  Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** do uruchomienia aplikacji.  
  
6.  W polu tekstowym wprowadź **Londynie**, a następnie wybierz przycisk. Zostaną wyświetleni tylko klienci z Londynu.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi Windows Communication Foundation oraz usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Porady: Dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)