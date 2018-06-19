---
title: Uaktualnij plików .mdf
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fa7fac39e8f198c473bf79a68a48feb136eccda3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924436"
---
# <a name="upgrade-mdf-files"></a>Uaktualnij plików .mdf

W tym temacie opisano opcje uaktualniania pliku bazy danych (mdf), po zainstalowaniu nowszej wersji programu Visual Studio. Zawiera instrukcje dotyczące następujących zadań:

- Uaktualnić plik bazy danych do nowszej wersji programu SQL Server Express LocalDB

- Uaktualnić plik bazy danych do nowszej wersji programu SQL Server Express

- Praca z plikiem bazy danych w programie Visual Studio, ale zachować zgodność ze starszymi wersjami programu SQL Server Express lub LocalDB

- Wprowadź programu SQL Server Express domyślny aparat bazy danych

Aby otworzyć projekt, który zawiera plik bazy danych (mdf), który został utworzony przy użyciu starszej wersji programu SQL Server Express lub LocalDB, można użyć programu Visual Studio. Aby kontynuować tworzenie projektu w programie Visual Studio, musi mieć danej wersji programu SQL Server Express lub LocalDB zainstalowany na tym samym komputerze co program Visual Studio lub należy uaktualnić plik bazy danych. Jeżeli uaktualnisz plik bazy danych nie można do niego dostęp przy użyciu starszej wersji programu SQL Server Express lub LocalDB.

Może też pojawić się prośba uaktualnić plik bazy danych, który został utworzony za pomocą starszej wersji programu SQL Server Express lub LocalDB, jeśli wersja pliku nie jest zgodna z wystąpienia programu SQL Server Express lub LocalDB, które jest obecnie zainstalowane. Aby rozwiązać ten problem, Visual Studio spowoduje wyświetlenie monitu do uaktualnienia pliku.

> [!IMPORTANT]
> Firma Microsoft zaleca, Utwórz kopię zapasową pliku bazy danych przed rozpoczęciem uaktualniania.

> [!WARNING]
> Po uaktualnieniu plik mdf, który został utworzony w LocalDB 2014 r. (wersja 12) 32-bitowych do LocalDB 2016 (V13) lub nowszym, nie można ponownie otworzyć plik w 32-bitowej wersji bazy danych LocalDB.

Przed rozpoczęciem uaktualniania bazy danych, należy wziąć pod uwagę następujące kryteria:

-   Nie uaktualniaj, jeśli chcesz pracować nad projektem w starszej wersji i nowszej wersji programu Visual Studio.

-   Nie uaktualniaj, jeśli aplikacja będzie używany w środowiskach korzystających z programu SQL Server Express zamiast LocalDB.

-   Nie uaktualniaj Jeśli aplikacja korzysta z połączenia zdalne, ponieważ LocalDB nie akceptuje tych postanowień.

-   Nie uaktualniaj, jeśli aplikacja opiera się na Internet Information Services (IIS).

-   Rozważ uaktualnienie, jeśli chcesz testować aplikacje baz danych w środowisku piaskownicy, ale nie chcesz administrować bazy danych.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Aby uaktualnić plik bazy danych, aby użyć wersji bazy danych LocalDB

1.  W **Eksploratora serwera**, wybierz pozycję **Połącz z bazą danych** przycisku.

2.  W **Dodawanie połączenia** okna dialogowego wprowadź następujące informacje:

    -   **Źródło danych**: `Microsoft SQL Server (SqlClient)`

    -   **Nazwa serwera**:

        -   Aby użyć domyślnej wersji: `(localdb)\MSSQLLocalDB`.  Ta wartość umożliwi określenie ProjectV12 lub ProjectV13, w zależności od wersji programu Visual Studio jest zainstalowany i utworzenia pierwszego wystąpienia bazy danych LocalDB. **MSSQLLocalDB** w węźle **Eksplorator obiektów SQL Server** pokazuje wersji wskazuje.

        -   Do korzystania z określonej wersji: `(localdb)\ProjectsV12` lub `(localdb)\ProjectsV13`, gdzie V12 jest LocalDB 2014, a V13 LocalDB 2016.

    -   **Dołącz plik bazy danych**: ścieżka fizyczna głównego pliku *.mdf.

    -   **Nazwa logiczna**: nazwa, która ma być używany z plikiem.

3.  Wybierz **OK** przycisku.

4.  Po wyświetleniu monitu wybierz **tak** przycisk, aby uaktualnić pliku.

    Bazy danych jest uaktualniany, jest dołączony do aparatu bazy danych LocalDB i nie jest zgodny ze starszą wersją programu LocalDB.

Można również zmodyfikować połączenie programu SQL Server Express do użycia LocalDB Otwieranie menu skrótów dla połączenia, a następnie wybierając **zmodyfikować połączenie**. W **zmodyfikować połączenie** okno dialogowe Zmień nazwę serwera, aby `(LocalDB)\MSSQLLocalDB`. W **właściwości zaawansowane** okna dialogowego upewnij się, że **wystąpienia użytkownika** ustawiono **False**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Aby uaktualnić plik bazy danych, aby użyć wersji programu SQL Server Express

1.  Menu skrótów dla połączenia z bazą danych, wybierz **zmodyfikować połączenie**.

2.  W **zmodyfikować połączenie** okno dialogowe, wybierz opcję **zaawansowane** przycisku.

3.  W **właściwości zaawansowane** okno dialogowe, wybierz opcję **OK** przycisk bez zmiany nazwy serwera.

    Plik bazy danych jest uaktualniona w celu dopasowania bieżącej wersji programu SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Do pracy z bazy danych w programie Visual Studio, ale zachować zgodność z programu SQL Server Express

-   W programie Visual Studio Otwórz projekt bez jego uaktualnieniem.

    -   Aby uruchomić projekt, zaznacz **F5** klucza.

    -   Aby edytować bazy danych, otwórz plik .mdf w **Eksploratora rozwiązań**, rozwiń węzeł w **Eksploratora serwera** do pracy z bazą danych.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Aby program SQL Server Express domyślny aparat bazy danych

1.  Na pasku menu wybierz **narzędzia**, **opcje**.

2.  W **opcje** okna dialogowego rozwiń **narzędzi bazy danych** opcje, a następnie wybierz **połączenia danych**.

3.  W **nazwa wystąpienia serwera SQL** tekst pola, określ nazwę wystąpienia programu SQL Server Express lub LocalDB, którego chcesz używać. Jeśli nie jest nazwane wystąpienie, określ `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.

4.  Wybierz **OK** przycisku.

    SQL Server Express będzie domyślny aparat bazy danych dla aplikacji.

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych w programie Visual Studio](accessing-data-in-visual-studio.md)