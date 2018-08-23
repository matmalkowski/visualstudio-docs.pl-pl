---
title: 'Wskazówki: Tworzenie procedur składowanych aktualizacji dla tabeli klientów Northwind | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Northwind sample database
- stored procedures [Visual Studio]
- O/R Designer, stored procedures
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: bbcd68b7604f7a80546168406146f326e1bac224
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633413"
---
# <a name="walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table"></a>Wskazówki: tworzenie procedur składowanych aktualizacji dla tabeli klientów Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niektóre tematy pomocy w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] dokumentacji wymagają dodatkowych procedur składowanych w bazie danych Northwind do operacji aktualizacji (operacje wstawiania, aktualizacji i usunięć) danych w tabeli Customers.  
  
 Ten przewodnik zawiera wskazówki dla tworzenia tych dodatkowych procedur składowanych w przykładowych baz danych Northwind dla [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 W sekcji kolejne kroki w dalszej części tego tematu zawiera łącza do tematów, które pokazują, jak pracować z tych dodatkowych procedur składowanych.  
  
 Z tego instruktażu dowiesz się, jak wykonywać następujące zadania:  
  
-   Utwórz połączenie danych z przykładowej bazy danych Northwind.  
  
-   Tworzenie procedur składowanych.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
-   Dostęp do wersji programu SQL Server w bazie danych Northwind. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie przykładowych baz danych](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="connecting-to-the-northwind-database"></a>Łączenie z bazą danych Northwind  
 Ten poradnik wymaga połączenia z SQL Server w wersji bazy danych Northwind. Poniższa procedura zawiera instrukcje tworzenia połączenia danych.  
  
> [!NOTE]
>  Jeśli masz już połączenie danych z bazy danych Northwind, możesz przejść do następnej sekcji Tworzenie procedur składowanych.  
  
#### <a name="to-create-a-data-connection-to-the-northwind-sql-server-database"></a>Aby utworzyć połączenie danych w bazie danych Northwind programu SQL Server  
  
1.  Na **widoku** menu, kliknij przycisk **Eksploratora serwera**/**Eksplorator bazy danych**.  
  
2.  Kliknij prawym przyciskiem myszy **połączeń danych** i kliknij przycisk **Dodaj połączenie**.  
  
3.  W **wybierz źródło danych** okno dialogowe, kliknij przycisk **programu Microsoft SQL Server**, a następnie kliknij przycisk **OK**.  
  
     Jeśli **Dodaj połączenie** zostanie otwarte okno dialogowe i **źródła danych** nie jest **programu Microsoft SQL Server (SqlClient)**, kliknij przycisk **zmiany** do otwarcia **Wybierz/Zmień źródło danych** okno dialogowe, kliknij przycisk **programu Microsoft SQL Server**, a następnie kliknij przycisk **OK**.  
  
4.  Kliknij przycisk **nazwy serwera** listy rozwijanej listy lub wpisz nazwę serwera, na którym znajduje się baza danych Northwind.  
  
5.  Na podstawie wymagań bazy danych lub aplikacji, kliknij przycisk **Użyj uwierzytelniania Windows** lub zaloguj się do komputera z programem SQL Server za pomocą określonej nazwy użytkownika i hasło (**uwierzytelnianiaprogramuSQLServer**).  
  
6.  Kliknij w bazie danych Northwind **wybierz lub wprowadź nazwę bazy danych** listy.  
  
7.  Kliknij przycisk **OK**.  
  
     Połączenie danych jest dodawany do **Eksploratora serwera**/**Eksplorator bazy danych**.  
  
## <a name="creating-the-stored-procedures"></a>Tworzenie procedur składowanych  
 Utwórz procedury składowane, uruchamiając dostarczonego skryptu SQL w bazie danych Northwind za pomocą [narzędzia graficzne bazy danych](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) dostępne w **Eksploratora serwera** /  **Database Explorer**.  
  
#### <a name="to-create-the-stored-procedures-by-using-a-sql-script"></a>Aby utworzyć procedur składowanych przy użyciu skryptu SQL  
  
1.  Rozwiń węzeł bazy danych Northwind w **Eksploratora serwera**/**Eksplorator bazy danych**.  
  
2.  Kliknij prawym przyciskiem myszy **procedur składowanych** węzła i kliknij przycisk **Dodaj nową procedurę przechowywaną**.  
  
3.  Wklej następujący kod do edytora kodu, zastępując `CREATE PROCEDURE` szablonu:  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  Zaznacz cały tekst w edytorze kodu, kliknij prawym przyciskiem myszy zaznaczony tekst, a następnie kliknij przycisk **Uruchom zaznaczone**.  
  
     SelectCustomers, InsertCustomers, UpdateCustomers i DeleteCustomers procedury składowane są tworzone dla bazy danych Northwind.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, po utworzeniu procedur składowanych, wypróbuj poniższe instruktaże, które pokazują, jak pracować z nimi:  
  
 [Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Wskazówki: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)  
  
 [Wskazówki: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ do SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)