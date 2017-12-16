---
title: "Zgodność bazy danych programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/06/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 2b3a551f19e3410b5f56ebe994676666cdc3d4e1
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="compatible-database-systems-for-visual-studio"></a>Systemy zgodne bazy danych dla programu Visual Studio

Aby opracować połączone dane aplikacji w programie Visual Studio, zwykle Zainstaluj system bazy danych na komputerze deweloperskim lokalne, a następnie wdrażanie aplikacji i baz danych w środowisku produkcyjnym, gdy są one gotowe. Visual Studio instaluje na komputerze programu SQL Server Express LocalDB w ramach **magazynu danych i przetwarzania** obciążenia. To wystąpienie bazy danych LocalDB jest przydatne w przypadku tworzenia połączenia danych aplikacji, szybkie i łatwe.

System bazy danych mają być dostępne z aplikacji .NET i które będą widoczne w Visual Studio danych narzędzi systemu windows musi on mieć dostawcy danych ADO.NET. Dostawcy specjalnie musi obsługiwać Entity Framework, jeśli planujesz używanie modeli danych jednostki w aplikacji .NET. Wielu dostawców są dostępne za pośrednictwem Menedżera pakietów NuGet lub za pomocą programu Visual Studio Marketplace.

Jeśli używane są interfejsy API usługi Azure Storage, aby uniknąć naliczania opłat, aż wszystko będzie gotowe do wdrożenia w środowisku produkcyjnym należy zainstalować te emulatory magazynu Azure na komputerze lokalnym podczas programowania. Aby uzyskać więcej informacji, zobacz [użyć emulatora magazynu Azure do programowania i testowania](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/).

Poniższa lista zawiera niektóre z najpopularniejszych systemów bazy danych, które mogą być używane w projektach Visual Studio. Lista nie jest kompletną. Aby uzyskać listę dostawców innych firm, które oferują dostawcy danych ADO.NET, umożliwiających głęboką integrację z narzędziami Visual Studio, zobacz [dostawcy danych ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

Program SQL Server jest bazą danych programu Microsoft najważniejszych oferty. SQL Server 2016 zapewnia wydajność przełomowe, zabezpieczeniami zaawansowanymi i rozbudowane, zintegrowane raportowania i analiz. Ten składnik jest dostarczany w różnych wersjach, które są przeznaczone do różnych celów: z analizy biznesowe wysoce skalowalną, wysokiej wydajności, do użycia na pojedynczym komputerze. SQL Server Express to oferujący wszystkie funkcje wersja programu SQL Server, które są dopasowane do rozpowszechniania i osadzania.  LocalDB to Uproszczona wersja programu SQL Server Express, która nie wymaga konfigurowania i działa w procesie aplikacji. Możesz pobrać jedną lub obie te produkty z [strony pobierania programu SQL Server Express](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx). Większość przykładów SQL w tej sekcji służy bazy danych LocalDB programu SQL Server. SQL Server Management Studio (SSMS) jest aplikacją zarządzania autonomicznej bazy danych, która ma więcej funkcji niż jaka jest dostępna w Eksploratorze obiektów serwera SQL programu Visual Studio. Możesz pobrać ze strony poprzedniej konsolidacji SSMS.

## <a name="oracle"></a>Oracle

Możesz pobrać płatną lub bezpłatnej wersji bazy danych programu Oracle [Oracle technologii sieci](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) strony. Obsługę projektowania dla programu Entity Framework i TableAdapters należy [Oracle Developer Tools dla programu Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Inne oficjalnego produktów Oracle, w tym błyskawicznych klienta Oracle, są dostępne za pośrednictwem Menedżera pakietów NuGet.  Możesz pobrać Oracle przykładowe schematy zgodnie z instrukcjami w [dokumentacji Online Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL to system popularnych open source bazy danych, który jest powszechnie używany w przedsiębiorstwach i witryn sieci Web. Pliki do pobrania dla programu MySQL, MySQL dla programu Visual Studio oraz pokrewnych produktów są na [MySQL w systemie Windows](http://www.mysql.com/why-mysql/windows/).  Stron trzecich oferują różne rozszerzenia programu Visual Studio i aplikacje autonomiczne zarządzania dla programu MySQL. Możesz przeglądać ofert Menedżera pakietów NuGet (**narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL to bezpłatne, open source obiektu system relacyjnej bazy danych. Aby go zainstalować w systemie Windows, możesz pobrać go z [stronę pobierania PostgreSQL](http://www.postgresql.org/download/windows/).  Można również tworzyć PostgreSQL z kodu źródłowego.  PostgreSQL core system zawiera interfejs języka C. Wiele podmiotów Podaj pakietów NuGet przy użyciu PostgreSQL z aplikacji .NET.  Możesz przeglądać ofert Menedżera pakietów NuGet (**narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**) . Prawdopodobnie najpopularniejszych pakietu jest zapewniana przez [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite jest osadzony aparat bazy danych SQL działa w procesie aplikacji. Możesz pobrać go z [stronę pobierania SQLite](http://www.sqlite.org/download.html). Dostępne są także wiele innych firm pakietów NuGet dla bazy danych SQLite. Możesz przeglądać ofert Menedżera pakietów NuGet (**narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**) .

## <a name="firebird"></a>Firebird

Firebird to system bazy danych SQL typu open source. Możesz pobrać go z [stronę pobierania Firebird](http://firebirdsql.org/en/downloads/). Dostawca danych ADO.NET jest dostępna za pośrednictwem Menedżera pakietów NuGet.

## <a name="see-also"></a>Zobacz także

[Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
[Jak ustalić, wersji i wydania programu SQL Server i jego składników](http://support.microsoft.com/kb/321185)