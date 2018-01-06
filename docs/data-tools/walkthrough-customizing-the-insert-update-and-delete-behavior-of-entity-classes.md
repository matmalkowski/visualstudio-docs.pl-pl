---
title: "Wskazówki: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: e4edcc21986ae0fd033228971697057932e63670
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Wskazówki: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek
[Składnika LINQ to SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) zapewnia visual powierzchnię tworzenia i edytowania [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy (klas jednostek), które są oparte na obiektach w bazie danych. Za pomocą [LINQ do SQL](/dotnet/framework/data/adonet/sql/linq/index), można użyć technologii LINQ do dostępu do bazy danych SQL. Aby uzyskać więcej informacji, zobacz [LINQ (zapytania język Language-Integrated)](/dotnet/csharp/linq/).  
  
Domyślnie logika przeprowadzania aktualizacji są dostarczane przez [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] środowiska wykonawczego. Środowisko uruchomieniowe tworzy domyślne instrukcje Insert, Update i Delete na podstawie schematu tabeli (definicje kolumn i informacje o kluczu podstawowym). Jeśli nie chcesz używać domyślnego zachowania, można skonfigurować zachowanie aktualizacji i wyznaczyć określonych procedur składowanych do wykonania niezbędnych operacji wstawienia, aktualizacje i usuwa wymagane do pracy z danymi w bazie danych. Ponadto można to zrobić, jeśli domyślne zachowanie nie jest generowany, na przykład po z klasami jednostki mapowania do widoków. Ponadto podczas bazy danych wymaga dostępu do tabeli za pomocą procedur składowanych można zastąpić domyślne zachowanie aktualizacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji przez przy użyciu procedur składowanych](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).  
  
> [!NOTE]
>  W tym przewodniku wymaga dostępności **InsertCustomer**, **UpdateCustomer**, i **DeleteCustomer** przechowywane procedury dla bazy danych Northwind.  
  
Ten przewodnik zawiera kroki, które należy wykonać, aby zastąpić domyślną LINQ do SQL zachowania w czasie wykonywania do zapisywania danych do bazy danych przy użyciu procedur składowanych.  
  
W tym przewodniku dowiesz się, jak wykonać następujące zadania:  
  
-   Tworzenie nowej aplikacji formularzy systemu Windows i Dodaj [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] pliku do niego.  
  
-   Utwórz klasę jednostki, który jest zamapowany na tabeli klientów Northwind.  
  
-   Utwórz źródło danych obiektu, który odwołuje się do składnika LINQ to SQL klienta klasy.  
  
-   Tworzenie formularza systemu Windows, który zawiera <xref:System.Windows.Forms.DataGridView> który jest powiązany z klasy klienta.  
  
-   Implementowanie zapisać funkcjonalności formularza.  
  
-   Utwórz <xref:System.Data.Linq.DataContext> metod przez dodanie przechowywane procedury [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
-   Konfigurowanie klasy klienta używają procedur składowanych do wykonywania operacji wstawiania, aktualizacji i usunięć.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.  
  
1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania wersjach programu SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **magazynu danych i przetwarzania** obciążenia, lub jako poszczególnych składników.  
  
2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:  

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowej kwerendy...** .  

       Zostanie otwarte okno edytora zapytań.  

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.  

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.  

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Tworzenie aplikacji i dodawanie LINQ w klasach SQL  
Ponieważ będzie działać z [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy i wyświetlanie danych w formularzu systemu Windows, tworzenie nowej aplikacji formularzy systemu Windows i Dodaj LINQ do pliku klasy SQL.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Aby utworzyć nowy projekt aplikacji formularzy systemu Windows, który zawiera LINQ w klasach SQL  
  
1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .  
  
2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.  

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.  

4. Nazwij projekt **UpdatingWithSProcsWalkthrough**, a następnie wybierz pozycję **OK**. 
  
     **UpdatingWithSProcsWalkthrough** projektu jest tworzony i dodane do **Eksploratora rozwiązań**.  
  
4.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
5.  Kliknij przycisk **klasy LINQ do SQL** szablon i typ **Northwind.dbml** w **nazwa** pole.  
  
6.  Kliknij przycisk **Dodaj**.  
  
     Pusty LINQ w klasach SQL pliku (Northwind.dbml) zostanie dodany do projektu i [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] otwiera.  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Tworzenie klasy jednostka klienta i źródło danych obiektu  
 Utwórz [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy, które są mapowane w tabelach bazy danych, przeciągając tabel z **Eksploratora serwera**/**Eksploratora bazy danych** na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Wynik jest LINQ w klasach SQL jednostki, które mapują do tabel w bazie danych. Po utworzeniu klas jednostek one może służyć jako obiekt źródła danych, podobnie jak inne klasy, których właściwości publicznej.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Aby utworzyć klasę jednostki klienta i skonfigurować źródła danych z nią  
  
1.  W **Eksploratora serwera**/**Eksploratora bazy danych**, Znajdź w tabeli klienta w wersji programu SQL Server w bazie danych Northwind. 
  
2.  Przeciągnij **klientów** węzła z **Eksploratora serwera**/**Eksploratora bazy danych** na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] powierzchni.  
  
     Klasa jednostki o nazwie **klienta** jest tworzony. Ma właściwości, które odnoszą się do kolumn w tabeli Klienci. Nosi nazwę klasy jednostka **klienta** (nie **klientów**), ponieważ reprezentuje on jednego odbiorcy z tabeli Klienci.  
  
    > [!NOTE]
    >  Zmiana nazwy jest to *pluralizacja*. Można ją włączyć lub wyłączyć [opcje — Okno dialogowe](../ide/reference/options-dialog-box-visual-studio.md). Aby uzyskać więcej informacji, zobacz [porady: Włączanie określania liczby mnogiej i wyłączanie (Projektanta obiektów relacyjnych)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  Na **kompilacji** menu, kliknij przycisk **kompilacji UpdatingwithSProcsWalkthrough** Aby skompilować projekt.  
  
4.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.  
  
5.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.  
  
6.  Kliknij przycisk **obiektu** na **wybierz typ źródła danych** a następnie kliknij przycisk **dalej**.  
  
7.  Rozwiń węzeł **UpdatingwithSProcsWalkthrough** węzła i Znajdź i zaznacz **klienta** klasy.  
  
    > [!NOTE]
    >  Jeśli **klienta** klasa nie jest dostępna, Anuluj wychodząc kreatora skompilować projekt i ponownie uruchom kreatora.  
8.  Kliknij przycisk **Zakończ** utworzyć źródło danych i dodać **klienta** klasy jednostki **źródeł danych** okna.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Tworzenie formantu DataGridView w celu wyświetlania danych klientów na formularzu systemu Windows  
 Tworzenie formantów, które są powiązane z klasami jednostki przeciągając [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] elementów ze źródła danych **źródeł danych** okna na formularzu systemu Windows.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Do dodawania formantów, które są powiązane z klasami jednostki  
  
1.  Otwórz Form1 w widoku Projekt.  
  
2.  Z **źródeł danych** okna, przeciągnij **klienta** węzła na Form1.  
  
    > [!NOTE]
    >  Aby wyświetlić **źródeł danych** okna, kliknij przycisk **Pokaż źródeł danych** na **danych** menu.  
  
3.  Otwórz Form1 w edytorze kodu.  
  
4.  Dodaj następujący kod do formularza, globalne do formularza, poza określonej metody, ale wewnątrz klasy Form1:  
  
    ```vb  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```csharp  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();    
    ```  
  
5.  Tworzenie procedury obsługi zdarzeń dla `Form_Load` zdarzeń i Dodaj następujący kod do programu obsługi:  
  
    ```vb  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```csharp  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;    
    ```  
  
## <a name="implementing-save-functionality"></a>Implementowanie funkcja zapisywania  
 Domyślnie ten przycisk nie jest włączone i nie jest zaimplementowana funkcja zapisywania. Ponadto kodu nie jest automatycznie dodawany do zapisania zmienione dane do bazy danych podczas tworzenia formantów powiązanych z danymi dla obiekt źródła danych. W tej sekcji wyjaśniono, jak włączyć zapisywania przycisk i implementować Zapisz funkcji [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] obiektów.  
  
#### <a name="to-implement-save-functionality"></a>Aby zaimplementować funkcja zapisywania  
  
1.  Otwórz Form1 w widoku Projekt.  
  
2.  Wybierz opcję Zapisz znajdującego się na **CustomerBindingNavigator** (przycisk z ikoną dyskietka).  
  
3.  W **właściwości** ustaw **włączone** właściwości **True**.  
  
4.  Kliknij dwukrotnie przycisk Zapisz, aby utworzyć program obsługi zdarzeń i przełącznika do edytora kodu.  
  
5.  Dodaj następujący kod do zapisywania przycisk obsługi zdarzeń:  
  
    ```vb  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```csharp  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Zastępowanie domyślnego zachowania umożliwiające wykonywanie aktualizacji (wstawienia, aktualizacje i usunięcia)  
  
#### <a name="to-override-the-default-update-behavior"></a>Aby zastąpić domyślne zachowanie aktualizacji  
  
1.  Otwórz LINQ do SQL pliku w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Kliknij dwukrotnie **Northwind.dbml** w pliku **Eksploratora rozwiązań**.)  
  
2.  W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń gałąź bazy danych Northwind **procedur składowanych** węzła i Znajdź  **InsertCustomers**, **UpdateCustomers**, i **DeleteCustomers** procedur składowanych.  
  
3.  Przeciągnij wszystkich trzech procedur składowanych na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Procedury składowane są dodawane do okienka metod jako <xref:System.Data.Linq.DataContext> metody. Aby uzyskać więcej informacji, zobacz [metodę DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Wybierz **klienta** klasy jednostki w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
5.  W **właściwości** wybierz **Wstaw** właściwości.  
  
6.  Kliknij przycisk wielokropka (...) obok pozycji **Użyj środowiska wykonawczego** otworzyć **Konfigurowanie zachowania** okno dialogowe.  
  
7.  Wybierz **dostosować**.  
  
8.  Wybierz **InsertCustomers** metody w **Dostosuj** listy.  
  
9. Kliknij przycisk **Zastosuj** Aby zapisać konfigurację dla wybranej klasy lub zachowania.  
  
    > [!NOTE]
    >  Możesz skonfigurować działanie dla każdej kombinacji klasy/zachowanie, pod warunkiem, możesz kliknąć przycisk **Zastosuj** po każdej zmianie. Jeśli zmienisz klasy lub zachowania przed kliknięciem przycisku **Zastosuj**, zapewniając możliwość zastosować zmiany będą wyświetlane okno dialogowe.  
  
10. Wybierz **aktualizacji** w **zachowanie** listy.  
  
11. Wybierz **dostosować**.  
  
12. Wybierz **UpdateCustomers** metody w **Dostosuj** listy.  
  
     Listę **argumenty metody** i **właściwości klasy** i zwróć uwagę, że istnieją dwa **argumenty metody** i dwa **właściwości klasy**dla niektórych kolumn w tabeli. Ułatwia to śledzenie zmian i utworzyć instrukcje sprawdzających naruszenia współbieżności.  
  
13. Mapa **Original_CustomerID** argument metody dla **CustomerID (oryginalny)** właściwość klasy.  
  
    > [!NOTE]
    >  Domyślnie argumenty metody przypisze do właściwości klasy, gdy nazwy są zgodne. Jeśli nazwy właściwości są zmieniane i nie jest już zgodne w tabeli, a klasa jednostki, może być konieczne wybierz właściwość klasy równoważne do mapowania Jeśli Projektanta obiektów relacyjnych nie może określić poprawne mapowania. Ponadto, jeśli argumenty metody nie ma właściwości prawidłową klasę do mapowania, możesz ustawić **właściwości klasy** do wartości **(Brak)**.  
  
14. Kliknij przycisk **Zastosuj** Aby zapisać konfigurację dla wybranej klasy lub zachowania.  
  
15. Wybierz **usunąć** w **zachowanie** listy.  
  
16. Wybierz **dostosować**.  
  
17. Wybierz **DeleteCustomers** metody w **Dostosuj** listy.  
  
18. Mapa **Original_CustomerID** argument metody dla **CustomerID (oryginalny)** właściwość klasy.  
  
19. Kliknij przycisk **OK**.  
  
> [!NOTE]
>  Chociaż nie jest problemem w przypadku tego przewodnika w szczególności, warto zauważyć, że [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] obsługi baza danych wygenerowała wartości automatycznie dla tożsamości (automatycznego przyrostu), rowguidcol (identyfikator GUID generowany przez bazę danych) i kolumn znaczników czasu podczas operacji wstawiania i aktualizacje. Wartości generowanych przez bazę danych w innych typów kolumn spowoduje nieoczekiwane wartości null. Aby zwrócić wartości generowanych przez bazę danych, należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> do `true` i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> do jednej z następujących czynności: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync>, lub <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Uruchom aplikację ponownie, aby sprawdzić, czy **UpdateCustomers** procedury składowanej poprawnie aktualizacji rekordu klienta w bazie danych.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Naciśnij F5.  
  
2.  Zmodyfikuj rekord w siatce, aby przetestować zachowania aktualizacji.  
  
3.  Dodaj nowy rekord do testowania zachowanie Insert.  
  
4.  Kliknij przycisk Zapisz, aby zapisać zmiany w bazie danych.  
  
5.  Zamknij formularz.  
  
6.  Naciśnij klawisz F5 i sprawdź, utrwalone zaktualizowany rekord i nowo wstawionego rekordu.  
  
7.  Usuń nowy rekord utworzonego w kroku 3 do testowania zachowanie Delete.  
  
8.  Kliknij ten przycisk, aby przesłać zmian i usunięcie usuniętego rekordu z bazy danych  
  
9. Zamknij formularz.  
  
10. Naciśnij klawisz F5 i sprawdź, czy usunięto rekord został usunięty z bazy danych.  
  
    > [!NOTE]
    >  Jeśli aplikacja używa programu SQL Server Express Edition, w zależności od wartości **Kopiuj do katalogu wyjściowego** właściwości pliku bazy danych, zmiany nie może występować, kiedy naciśniesz klawisz F5 w kroku 10. 
  
## <a name="next-steps"></a>Następne kroki  
W zależności od wymagań aplikacji istnieje kilka czynności, które można wykonać po utworzeniu [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klas jednostek. Oto niektóre ulepszenia, jakie można wprowadzać tej aplikacji:  
  
-   Implementuje współbieżności sprawdzanie w trakcie aktualizacji. Aby uzyskać informacje, zobacz [optymistycznej współbieżności: omówienie](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).  
  
-   Dodawanie zapytań LINQ można filtrować dane. Aby uzyskać informacje, zobacz [wprowadzenie do kwerend LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## <a name="see-also"></a>Zobacz także
[LINQ do SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)     
[Metody DataContext](../data-tools/datacontext-methods-o-r-designer.md)   
[Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)  
[LINQ do SQL zapytań](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)  
 