---
title: 'Porady: łączenie z bazą danych Northwind | Dokumentacja firmy Microsoft'
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
- connections [Visual Studio], Northwind database
- Northwind sample database
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 45e8e1bcab3af0c55a541b589574eca37fc7f2ec
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681731"
---
# <a name="how-to-connect-to-the-northwind-database"></a>Porady: połączenie z bazą danych Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jak dowiesz się, jak tworzyć aplikacje bazy danych przy użyciu programu Visual Studio, należy połączyć z bazą danych Northwind, aby wykonać wiele przykładów w dokumentacji produktu. W zależności od przykładu, które wykonujesz uzyskasz połączenie z bazą danych programu SQL Server lub pliku bazy danych, np. jedno dla programu Microsoft Access lub programu SQL Server.  
  
## <a name="creating-data-connections-to-the-northwind-database"></a>Tworzenie połączenia danych z bazy danych Northwind  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-data-connection-to-the-northwind-database-sql-server"></a>Aby utworzyć połączenie danych z bazy danych Northwind (SQL Server)  
  
1.  Na **widoku** menu, wybierz **Eksploratora serwera**/**Eksplorator bazy danych**.  
  
2.  W **Eksploratora serwera**/**Eksplorator bazy danych**, otwórz menu skrótów dla **połączeń danych** i wybierz polecenie **Dodaj połączenie**.  
  
     Po wybraniu **Dodaj połączenie**, albo **wybierz źródło danych** okno dialogowe lub **Dodaj połączenie** zostanie wyświetlone okno dialogowe.  
  
3.  Jeśli **wybierz źródło danych** pojawi się okno dialogowe, wybierz **programu Microsoft SQL Server**, a następnie wybierz **OK**.  
  
     Jeśli **Dodaj połączenie** pojawi się okno dialogowe i **źródła danych** nie **programu Microsoft SQL Server (SqlClient)**, wybierz **zmiany** przycisk, aby otworzyć **Zmień źródło danych** okno dialogowe, wybierz opcję **programu Microsoft SQL Server**, a następnie wybierz **OK** przycisku.  
  
4.  W **nazwy serwera** Określ nazwę serwera, na którym znajduje się baza danych Northwind.  
  
5.  W zależności od wymagań używanej wersji programu SQL Server i bazy danych Northwind, wybierz opcję **uwierzytelnianie Windows** lub wybierz **Użyj uwierzytelniania programu SQL Server** i wprowadź nazwę użytkownika i hasło do logowania się do komputera z programem SQL Server.  
  
6.  Wybierz bazę danych Northwind w **wybierz lub wprowadź nazwę bazy danych** listy.  
  
7.  Wybierz **Testuj połączenie** do weryfikowania łączności z bazą danych Northwind.  
  
8.  Wybierz **OK**.  
  
     Połączenie danych z bazy danych Northwind jest dodawany do **Eksploratora serwera**/**Eksplorator bazy danych**.  
  
 Oprócz nawiązywania połączenia ze zdalnym wystąpieniem bazy danych programu SQL Server, można też połączyć bezpośrednio z rzeczywistymi plikami, które zawierają bazy danych. Dzięki temu można dodać pliki bazy danych bezpośrednio do projektu, gdzie one wdrażane jako część aplikacji. Obecnie obsługiwane są następujące pliki z lokalnej bazy danych: pliki bazy danych programu SQL Server Compact (.sdf) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] i pliki bazy danych programu SQL Server Express (.mdf) i pliki bazy danych Microsoft Access (.mdb lub accdb).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databasesql-server-database-file-mdf"></a>Aby utworzyć połączenie danych z bazy danych Northwind — plik bazy danych programu SQL Server (mdf)  
  
1.  Na **widoku** menu, wybierz **Eksploratora serwera**/**Eksplorator bazy danych**.  
  
2.  W **Eksploratora serwera**/**Eksplorator bazy danych**, otwórz menu skrótów dla **połączeń danych** i wybierz polecenie **Dodaj połączenie**.  
  
     Po wybraniu **Dodaj połączenie**, albo **Dodaj połączenie** okno dialogowe lub **wybierz źródło danych** zostanie wyświetlone okno dialogowe.  
  
3.  Jeśli **wybierz źródło danych** pojawi się okno dialogowe, wybierz **plik bazy danych programu Microsoft SQL Server**, a następnie wybierz **OK**.  
  
4.  Jeśli **Dodaj połączenie** pojawi się okno dialogowe, upewnij się, że **źródła danych** ustawiono **plik bazy danych Microsoft SQL Server (SqlClient)**. Jeśli nie jest ustawiony na **plik bazy danych Microsoft SQL Server (SqlClient)**, wybierz **zmiany** otworzyć **Zmień źródło danych** okna dialogowego wybierz **programu Microsoft SQL Plik bazy danych serwera**, a następnie wybierz **OK** przycisku.  
  
5.  Wybierz **Przeglądaj** można zlokalizować pliku mdf, który zawiera bazę danych Northwind.  
  
6.  W zależności od wymagań Twojej wersji bazy danych Northwind, wybierz opcję **uwierzytelnianie Windows** lub wybierz **uwierzytelniania programu SQL Server** i wprowadź nazwę użytkownika i hasło, aby zalogować się do komputer z uruchomionym programem SQL Server.  
  
7.  Wybierz **OK** przycisku.  
  
     Połączenie danych z bazy danych Northwind jest dodawany do **Eksploratora serwera**/**Eksplorator bazy danych**.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] zawiera zmiany, które są stosowane do pliku bazy danych Northwind (.mdf). Aby uzyskać informacje, zobacz [porady: Instalowanie przykładowych baz danych](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databaseaccess-database-file-mdb-or-accdb"></a>Aby utworzyć połączenie danych z bazy danych Northwind — plik bazy danych programu Access (.mdb lub accdb)  
  
1.  Na **widoku** menu, wybierz **Eksploratora serwera**/**Eksplorator bazy danych**.  
  
2.  W **Eksploratora serwera**/**Eksplorator bazy danych**, otwórz menu skrótów dla **połączeń danych** i wybierz polecenie **Dodaj połączenie**.  
  
     Po wybraniu **Dodaj połączenie**, albo **Dodaj połączenie** okno dialogowe lub **wybierz źródło danych** zostanie wyświetlone okno dialogowe.  
  
3.  Jeśli **wybierz źródło danych** pojawi się okno dialogowe, wybierz **plik bazy danych programu Microsoft Access**, a następnie wybierz **OK**.  
  
4.  Jeśli **Dodaj połączenie** pojawi się okno dialogowe, upewnij się, że **źródła danych** ustawiono **plik bazy danych programu Microsoft Access**. Jeśli nie jest ustawiony na **plik bazy danych programu Microsoft Access**, wybierz **zmiany** otworzyć **Zmień źródło danych** okna dialogowego wybierz **bazy danych programu Microsoft Access Plik**, a następnie wybierz **OK** przycisku.  
  
5.  Wybierz **Przeglądaj** aby zlokalizować plik .mdb lub accdb, który zawiera bazę danych Northwind.  
  
6.  Wprowadź nazwę użytkownika i hasło, jeśli jest to wymagane przez Twoją wersję bazy danych Northwind.  
  
7.  Wybierz **OK**.  
  
     Połączenie danych z bazy danych Northwind jest dodawany do **Eksploratora serwera**/**Eksplorator bazy danych**.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Instalowanie przykładowych baz danych](../data-tools/how-to-install-sample-databases.md)   
 [Programowanie danych przy użyciu programu Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)