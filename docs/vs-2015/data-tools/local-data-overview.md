---
title: Dane lokalne — Przegląd | Dokumentacja firmy Microsoft
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
- SQL Server Express
- local data
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- SQL Server, local data
- SQL Express
- SQL Server Compact
- data access [Visual Studio], troubleshooting
- Access, .mdb files in Visual Studio
- data [Visual Studio], local
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b2bd594ba017a07ad3886a9aeb4b59d6f479a708
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680542"
---
# <a name="local-data-overview"></a>Dane lokalne — Przegląd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas tworzenia aplikacji do danych, jest zazwyczaj najlepiej jest używać lokalnej kopii bazy danych, tak, aby nie wprowadzają błędów w danych produkcyjnych. Nawet do udostępniania bazy danych testów z innymi deweloperami tworzy potencjalnych problemów, jeśli dwa deweloperów powodować błędy, wchodzących w interakcję względami twardych do wykrycia. Możesz uniknąć wszystkie te pułapek przy użyciu własnych danych testu na komputerze lokalnym. Większość, jeśli nie wszystkie systemy w bazie danych umożliwiają tworzenie lokalne pliki danych. Dla projektów .NET Visual Studio zapewnia obsługę specjalne lokalne pliki bazy danych programu SQL Server (mdf) i pliki bazy danych Microsoft Access (.mdb).  
  
 Program Visual Studio obsługuje następujące scenariusze:  
  
1.  
  
2.  
  
-  
  
-  
  
-   Utwórz projekt bazy danych programu SQL Server, klikając węzeł rozwiązania w Eksploratorze rozwiązań i wybierając pozycję **Dodaj &#124; nowy projekt**.  W okienku po lewej stronie wybierz **programu SQL Server &#124; bazy danych** projektu, a następnie kliknij przycisk OK. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu bazy danych, aby zaimportować plik lokalnej bazy danych, a następnie tworzenia aplikacji, który nawiązuje połączenie z bazą danych wytworzonych przez projekt. Dobre podczas ich tworzenia i modyfikowania schematu bazy danych w tym samym czasie, czy tworzysz aplikację.  
  
     ![Importowanie bazy danych do projektu bazy danych](../data-tools/media/raddata-import-database-into-database-project.png "raddata Importuj bazę danych do projektu bazy danych")  
  
-   Jeśli tworzysz nową bazę danych, najpierw dodać **usługową bazę danych pliku** do projektu (**projektu &#124; Dodaj nowy element)**. Spowoduje to utworzenie nowego pliku mdf, który jest dołączony do domyślnego wystąpienia programu SQL Server na maszynie lokalnej, która domyślnie jest \MSSQLocalDB (localdb). Baza danych powinna zostać wyświetlona w oknie Eksploratora serwera. Rozwiń węzeł, a następnie kliknij prawym przyciskiem myszy na węzłach, aby dodać nowe obiekty bazy danych, takich jak tabele, widoki, funkcje i tak dalej.  
  
 Aby uzyskać więcej informacji na temat programu SQL Server Express LocalDB, zobacz [wprowadzenie do LocalDB, ulepszonej wersji SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375) i [LocalDB: gdzie jest Moja bazy danych?](http://go.microsoft.com/fwlink/?LinkId=234376) w witrynie internetowej firmy Microsoft.  
  
 Poniższa tabela zawiera łącza do tematów opisujących sposób łączenia aplikacji z danymi lokalnymi:  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Tworzenie bazy danych SQL za pomocą projektanta](../data-tools/create-a-sql-database-by-using-a-designer.md)|Instrukcje krok po kroku do tworzenia pliku lokalnej bazy danych, który służy do testowania funkcji danych i tworzenia aplikacji.|  
|[Wskazówki: Łączenie z danymi w pliku lokalnej bazy danych (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|Instrukcje krok po kroku dotyczące łączenia z bazą danych SQL Server Express LocalDB podczas tworzenia prostej aplikacji Windows.|  
|[Łączenie z danymi w bazie danych programu Access (formularze Windows)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Instrukcje krok po kroku dotyczące łączenia z bazą danych programu Microsoft Access.|  
|[Porady: łączenie z bazą danych Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)|Zawiera instrukcje dotyczące łączenia z przykładową bazą danych Northwind w [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], SQL Server Compact, SQL Server Express i Access.|  
  
## <a name="use-the-connection-string"></a>Użyj parametrów połączenia  
 To najprostsza metoda i jest dobrym wyborem podczas aplikacji odczytuje jedynie z bazy danych i korzystanie z baz danych innych firm. Plik bazy danych może być umieszczony w dowolnym miejscu na maszynie lokalnej, która aplikacja ma uprawnienia dostępu i obsługuje system bazy danych.  
  
1.  (Opcjonalnie) Tworzenie nowego połączenia, zgodnie z opisem w [dodać nowe połączenia](../data-tools/add-new-connections.md). Do innej bazy danych i plików mdf, dla których już znać parametry połączenia i będzie nie być podczas wiązania z danymi lub korzystanie ze źródła danych, takich jak klasy Entity Framework lub zestawów danych ten krok nie jest konieczne. Wystarczy użyć parametrów połączenia, aby połączyć się z plikiem lokalnym. Dla plików .mdf [uaktualnianie plików MDF](../data-tools/upgrade-dot-mdf-files.md) i [ustanawiania połączenia](https://msdn.microsoft.com/en-us/library/ms254507.aspx).  
  
2.  (Opcjonalnie) Jeśli używane są zestawy danych platformy Entity Framework x lub LINQ to SQL, Utwórz źródło danych za pomocą Kreatora konfiguracji źródła danych. Aby uzyskać więcej informacji, zobacz [dodasz nowe źródła danych](../data-tools/add-new-data-sources.md).  
  
## <a name="add-an-existing-mdf-to-your-project"></a>Dodaj istniejące .mdf do projektu  
 Jeśli aplikacji będzie Wstawianie, usuwanie lub aktualizowanie danych i chcesz przechowywać kopię oryginalnego pliku dostępna, Rozważ dodanie pliku do projektu. Po wykonaniu tej czynności, można ustawić właściwość elementu na niej w celu **Kopiuj do katalogu wyjściowego** do **zawsze Kopiuj** lub **Kopiuj Jeśli nowszy**oraz opracowywania aplikacji. Każdorazowo, gdy tworzysz aplikację, oryginalna baza danych jest kopiowany do folderu wyjściowego i wprowadzania zmian w Twojej aplikacji są wykonywane na kopię. W ten sposób zawsze mieć czystą kopię oryginalnych danych.  
  
1.  Użyj **Eksploratora plików Windows** ich przeciąganie i upuszczanie plików MDF z jego bieżącej lokalizacji na węzeł projektu w Eksploratorze rozwiązań w programie Visual Studio.  Jeśli plik jest już dołączony do wystąpienia localDB, należy ją najpierw odłączyć. Po upuszczeniu go do projektu programu Visual Studio będzie automatycznie dołączyć go do domyślnego wystąpienia localDB.  
  
2.  Kliknij prawym przyciskiem myszy w nowym węźle bazy danych, a następnie wybierz polecenie Właściwości. Wybierz zachowanie kopiowania: **zawsze Kopiuj** lub **Kopiuj Jeśli nowszy**.  
  
## <a name="create-a-sql-server-database-project-and-import-your-database"></a>Utwórz projekt bazy danych programu SQL Server i zaimportować bazę danych  
 Jest to dobry wybór, gdy użytkownik będzie rozwijać, sama baza danych może być dodanie kolumn lub tabel lub zmienianie typów danych.  
  
## <a name="each-project-contains-two-copies-of-the-database"></a>Każdy projekt zawiera dwie kopie bazy danych  
 Podczas tworzenia projektu plik bazy danych może zostać skopiowany z głównego folderu projektu do danych wyjściowych, **bin**, folder. To zachowanie zależy **Kopiuj do katalogu wyjściowego** właściwości pliku, a wartość domyślna tej właściwości zależy od typu pliku bazy danych, którego używasz.  
  
 Aby wyświetlić **bin** folderu w **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** przycisk na pasku narzędzi.  
  
> [!NOTE]
>  **Kopiuj do katalogu wyjściowego** właściwość nie ma zastosowania do projektów C++ lub sieci web.  
  
 Plik bazy danych w folderze głównym projektu zostanie zmieniony tylko wtedy, gdy edytujesz schemat bazy danych lub dane za pomocą **Eksploratora serwera**/**Eksplorator bazy danych** lub innych [Visual Narzędzia bazy danych](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 W przypadku zmiany danych podczas tworzenia aplikacji zmieniasz też bazę danych w **bin** folderu. Na przykład wybierając klawisz F5, aby debugować aplikację, masz połączenia z bazą danych w tym folderze.  
  
|Wartość atrybutu **Kopiuj do katalogu wyjściowego** właściwości|Zachowanie|  
|----------------------------------------------------|--------------|  
|**Kopiuj Jeśli nowszy** (wartość domyślna dla plików .sdf)|Plik bazy danych jest kopiowany z katalogu projektu do **bin** katalogu, skompiluj projekt po raz pierwszy. **Data modyfikacji** własności plików jest porównywana z każdym razem, gdy kompilujesz projekt. Jeśli plik w folderze projektu jest nowszy, jest kopiowany do **bin** folderu, zastępując poprzedni plik. W przeciwnym razie żadne pliki nie są kopiowane. **Uwaga:** nie zalecamy użycia tej wartości dla plików .mdb lub .mdf. Plik bazy danych można zmienić nawet wtedy, gdy dane nie ulegają zmianom. Plik może być oznaczony jako nowszy, jeśli po prostu otwierasz połączenie (na przykład rozwiń folder **tabel** w węźle **Eksploratora serwera**).|  
|**Zawsze Kopiuj** (wartość domyślna dla plików .mdf i .mdb)|Plik bazy danych jest kopiowany z katalogu projektu do **bin** katalogu w każdym razem, gdy kompilujesz aplikację. Wszelkie zmiany wprowadzone w pliku danych w folderze wyjściowym są zastępowane przy następnym uruchomieniu aplikacji.|  
|**Nie Kopiuj**|System nigdy nie zastępuje pliku w **bin** katalogu. Aplikacja tworzy ciąg połączenia dynamicznego, który wskazuje plik bazy danych w katalogu wyjściowym. W związku z tym należy ręcznie skopiować plik do katalogu wyjściowego Jeśli chcesz, aby dane w katalogu wyjściowym pasowały do danych w katalogu projektu.|  
  
## <a name="common-issues-with-local-data"></a>Typowe problemy z danymi lokalnymi  
 W poniższej tabeli opisano typowe problemy, które można napotkać podczas pracy z plikami danych lokalnych.  
  
|Problem|Wyjaśnienie|  
|-----------|-----------------|  
|Za każdym razem, gdy mam testuję moją aplikację i modyfikuję dane, Moje zmiany są usuwane przy następnym uruchomieniu mojej aplikacji.|Wartość **Kopiuj do katalogu wyjściowego** właściwość **Kopiuj Jeśli nowszy** lub **zawsze Kopiuj**. Bazy danych w folderze danych wyjściowych (bazy danych, która jest modyfikowana podczas testowania aplikacji) jest zastępowany podczas każdego kompilowania projektu. Aby uzyskać więcej informacji, zobacz [jak: Manage Local Data Files in Your Project](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Pojawi się komunikat informujący o tym, że plik danych jest zablokowany.|Access (pliki .mdb): Sprawdź, czy plik nie jest otwarty w innym programie, takich jak dostęp.<br /><br /> SQL Server Express (pliki .mdf): SQL Express blokuje plik danych, jeśli użytkownik próbuje skopiować, przenieść lub zmienić jego nazwę na zewnątrz środowiska IDE programu Visual Studio.|  
|Odmowa dostępu, gdy więcej niż jeden użytkownik podejmuje próbę dostępu do tej samej bazy danych w tym samym czasie.|Program Visual Studio korzysta z *wystąpień użytkownika*, które są funkcją programu SQL Server Express, która tworzy osobne wystąpienia programu SQL Server dla każdego użytkownika. Po wielu użytkowników uzyskuje dostęp do pliku, nie można połączyć kolejni użytkownicy. Ten problem może wystąpić, jeśli na przykład zostanie podjęta próba uruchomienia aplikacji sieci web w ASP.NET Development Server i usług Internet Information Services (IIS) w tym samym czasie, ponieważ program IIS jest zazwyczaj uruchamiany przy użyciu innego konta.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Łączenie z danymi w pliku lokalnej bazy danych (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Łączenie z danymi w bazie danych programu Access (formularze Windows)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)