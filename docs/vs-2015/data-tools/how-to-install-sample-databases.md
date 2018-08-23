---
title: 'Porady: Instalowanie przykładowych baz danych | Dokumentacja firmy Microsoft'
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
- sample databases, Adventure Works
- data [Visual Studio], sample databases
- sample databases, Northwind
- Northwind sample database
- Adventure Works sample database
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 86dd1914b69dc047c6f8fd9b5d531976141b5ded
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633529"
---
# <a name="how-to-install-sample-databases"></a>Porady: instalacja przykładowych baz danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wiele przykładów danych wymaga możliwości podłączenia do Northwind, Pubs i AdventureWorks przykładowych baz danych. Można zainstalować i połączyć z tych baz danych przy użyciu poniższych procedur.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="installing-databases"></a>Instalowanie baz danych  
 Wiele przykładów danych wymaga dostępności przykładowych baz danych, które można pobrać z witryny sieci web. Przykładowe bazy danych obejmują bazy danych AdventureWorks, Northwind i Pubs.  
  
#### <a name="to-install-the-northwind-and-pubs-sample-databases-for-sql-server"></a>Aby zainstalować Northwind i Pubs przykładowe bazy danych programu SQL Server  
  
1.  Przejdź do [Northwind i Pubs Sample Databases](http://go.microsoft.com/fwlink?linkid=64296) witryny sieci web.  
  
2.  Pobierz i uruchom Instalatora.  
  
     Instalator dodaje folder **programu SQL Server 2000 Sample Databases** do folderu głównego na komputerze. (Na przykład: **C:\SQL Server 2000 Sample Databases**).  
  
3.  Odszukaj skrypt SQL dla bazy danych, którą chcesz, Northwind lub Pubs.  
  
    > [!WARNING]
    >  . Plik bazy danych MDF łatwo nie można przekonwertować do formatu, którego można użyć w bieżących wersjach programu SQL Server, dlatego najlepiej użyć skryptu, aby utworzyć bazę danych.  
  
4.  W **Eksploratora serwera**, utworzyć połączenie z wystąpieniem programu SQL Server, na którym chcesz zainstalować bazę danych. Jeśli nie masz określonego serwera SQL, którego chcesz używać, można użyć bazy danych, która jest automatycznie instalowany z programem Visual Studio. Aby to zrobić, należy określić `(localdb)\v11.0` jako nazwy serwera.  
  
     Aby utworzyć połączenie, wykonaj następujące kroki.  
  
    ###### <a name="to-create-a-connection-to-an-instance-of-sql-server"></a>Aby utworzyć połączenie z wystąpieniem programu SQL Server  
  
    1.  W **Eksploratora serwera**, otwórz menu skrótów dla **połączeń danych** węzeł i wybierz polecenie **Dodaj połączenie**.  
  
         **Dodaj połączenie** pojawi się okno dialogowe.  
  
    2.  Nazwa serwera SQL, w którym chcesz utworzyć bazę danych Northwind lub Pubs, lub wpisz (localdb) \v11.0.  
  
    3.  W obszarze **wybierz lub wprowadź nazwę bazy danych**, wybierz dowolną bazę danych z listy, na przykład bazy danych tempdb.  
  
    4.  Wybierz **Testuj połączenie** przycisk, aby sprawdzić, czy wszystko działa, a następnie wybierz **OK** przycisku.  
  
         Nowy węzeł połączenia pojawia się w **Eksploratora serwera**.  
  
5.  W menu skrótów dla węzła połączenia dla serwera a następnie wybierz **nowe zapytanie** przycisku.  
  
     Okno edytora otwiera się i pokazuje pusty plik skryptu .sql.  
  
6.  Wklej zawartość instnwnd.sql lub instpubs.sql w oknie edytora.  
  
7.  Wybierz przycisk wykonywanie zapytań (ikonę Otwórz zielony trójkąt u góry po prawej krawędzi okna zapytania).  
  
     Jeśli zapytanie powiedzie się, komunikat **polecenia została ukończona pomyślnie** pojawia się. Oznacza to, że utworzono bazę danych Northwind lub pubs.  
  
     Nadal musisz dodać połączenie z przykładową bazą danych. W **Eksploratora serwera**, otwórz menu skrótów dla **połączeń danych** węzeł i wybierz polecenie **Dodaj połączenie**.  
  
8.  Tej samej bazy danych serwera, która została wybrana wcześniej, ale tym razem z menu wybierz lub wprowadź nazwę bazy danych, wybierz bazę danych Northwind lub pubs lub wybrać **OK** przycisku.  
  
     Nowy węzeł zostanie wyświetlony w obszarze połączenia danych przykładowej bazy danych.  
  
9. Zamknij okno edytora i upewnij się, że nie chcesz zapisać plik zapytania. Nie jest to konieczne zapisać skrypt tworzenia bazy danych, po utworzeniu bazy danych.  
  
#### <a name="to-install-the-adventureworks-sample-databases"></a>Aby zainstalować przykładowe bazy danych AdventureWorks  
  
-   Pobierz przykładowe bazy danych AdventureWorks z [witryny sieci CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### <a name="to-install-the-northwind-sample-database-for-microsoft-access"></a>Aby zainstalować przykładową bazę danych Northwind dla programu Microsoft Access  
  
1.  W programie Microsoft Access 2010 lub nowszej, wyszukiwanie szablonów online Northwind i wybierz polecenie **Desktop Northwind 2007 przykładowej bazy danych**.  
  
2.  W programie Microsoft Access należy zapisać plik bazy danych jako Northwind.accdb.  
  
 Nowe rozszerzenie dla baz danych programu Access to accdb. Zobacz [programowanie danych przy użyciu programu Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx). Aby połączyć z bazą danych Northwind za pomocą programu Access, zobacz [jak: łączenie z bazą danych Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Przykładowe bazy danych są wyłącznie do celów informacyjnych i nie muszą pokazywać najlepszych rozwiązań zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak określić wersję i wydanie programu SQL Server i jego składników](http://support.microsoft.com/kb/321185)   
 [Tworzenie bazy danych SQL za pomocą projektanta](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Porady: łączenie z bazą danych Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)