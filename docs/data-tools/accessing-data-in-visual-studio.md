---
title: "Uzyskiwanie dostępu do danych w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
caps.latest.revision: "100"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 8102301ee098ef662f27c8a6dc586a683a85d177
ms.sourcegitcommit: 1aa9282b1f0bc2795df3264cbd1e331cc44c23f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2017
---
# <a name="accessing-data-in-visual-studio"></a>Uzyskiwanie dostępu do danych w programie Visual Studio

W programie Visual Studio, można utworzyć aplikacji, które łączenie z danymi w praktycznie dowolne bazy danych produktu lub usługi, w dowolnym miejscu i formatu — na komputerze lokalnym, w sieci lokalnej lub w chmurze public, private lub hybrydowego.

W przypadku aplikacji w JavaScript, Python, PHP, Ruby lub C++ połączenie z danych tak jak wykonywanie dodatkowych czynności, uzyskując bibliotek i pisanie kodu. W przypadku aplikacji .NET Visual Studio udostępnia narzędzia, które umożliwia Eksplorowanie źródeł danych, tworzyć modele obiektów do przechowywania i obsługi danych w pamięci i powiązania danych interfejsu użytkownika. Microsoft Azure udostępnia zestawy SDK dla platformy .NET, Java, Node.js, PHP, Python, Ruby i aplikacji mobilnych i narzędzia programu Visual Studio do połączenia usługi Azure Storage.

Następujące przedstawiono kilka z wielu systemów magazynu i bazy danych, które mogą być używane w programie Visual Studio. [Microsoft Azure](https://azure.microsoft.com/) oferty są usług danych, które obejmują wszystkie inicjowania obsługi i zarządzania odpowiedni magazyn danych.  [Azure Tools dla Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) jest opcjonalnym składnikiem, który umożliwia pracę z magazynów Azure danych bezpośrednio z programu Visual Studio. Większości produktów innych SQL i NoSQL bazy danych wymienione w tym miejscu może być obsługiwany na komputerze lokalnym, w sieci lokalnej lub w systemie Microsoft Azure na maszynie wirtualnej. W tym scenariuszu jest odpowiedzialny za zarządzanie sama baza danych.

**Microsoft Azure**

||||
|-|-|-|
|Baza danych SQL|Usługi DocumentDB|Magazyn (obiekty BLOB, tabel, kolejek, plików)|
|Magazyn danych SQL|Baza danych SQL Server Stretch|StorSimple|

i więcej...

**SQL**

||||
|-|-|-|
|SQL Server 2005-2016, w tym Express i LocalDB|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

i więcej...

**NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|Bazy danych MongoDB|
|Lokalizacji|OrientDB|RavenDB|
|VelocityDB|||

i więcej...

Wielu dostawców bazy danych i stron trzecich obsługiwać integracji z programem Visual Studio pakietów NuGet. Można eksplorować oferty nuget.org lub za pomocą Menedżera pakietów NuGet w programie Visual Studio (**narzędzia** > **Menedżera pakietów NuGet** > **zarządzania pakietami NuGet Pakietami dla rozwiązania**). Inne produkty bazy danych integracji z programem Visual Studio jako rozszerzenie. Przeglądaj tych ofert w programie Visual Studio Marketplace, przechodząc do **narzędzia**, **rozszerzenia i aktualizacje** , a następnie wybierając **Online** w okienku po lewej stronie okno dialogowe. Aby uzyskać więcej informacji, zobacz [systemów zgodne bazy danych dla programu Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Rozszerzona obsługa programu SQL Server 2005 zakończona w dniu 12 kwietnia 2016 r. Nie ma żadnej gwarancji, że narzędzia danych w programie Visual Studio 2015 i później będą nadal działały z programu SQL Server 2005 po tej dacie. Aby uzyskać więcej informacji, zobacz [powiadomienia zakończenia pomocy technicznej dla programu SQL Server 2005](https://www.microsoft.com/server-cloud/products/sql-server-2005/).

## <a name="net-languages"></a>Języków .NET

Wszystkie .NET dostępu do danych, w tym w .NET Core jest oparta na ADO.NET, zestaw klas, który definiuje interfejs do uzyskiwania dostępu do dowolnego rodzaju źródła danych relacyjnych i nierelacyjnych. Visual Studio ma kilka narzędzi i projektantów, które współpracują z ADO.NET umożliwiające nawiązywanie połączeń z bazami danych, manipulowania danymi i przedstawiają dane do użytkownika. Dokumentacja w tej sekcji opisano sposób używania tych narzędzi. Można również zaprogramować bezpośrednio przed ADO.NET— obiekty polecenia. Aby uzyskać więcej informacji na temat bezpośrednie wywoływanie interfejsów API ADO.NET, zobacz [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) w bibliotece MSDN.

Dokumentacja dostępu do danych związane z platformy ASP.NET, zobacz [Praca z danymi](http://www.asp.net/web-forms/overview/presenting-and-managing-data) w witrynie platformy ASP.NET. Samouczek na platformie ASP.NET MVC przy użyciu programu Entity Framework, zobacz [wprowadzenie do programu Entity Framework 6 Code First przy użyciu MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Uniwersalnych aplikacji platformy systemu Windows (UWP) w języku C# lub Visual Basic umożliwia dostęp do usługi Azure Storage i innymi usługami Azure zestaw Microsoft Azure SDK dla platformy .NET. Klasa Windows.Web.HttpClient umożliwia komunikację z dowolnej usługi RESTful. Aby uzyskać więcej informacji, zobacz [sposób nawiązywania połączenia z serwerem HTTP przy użyciu Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Do przechowywania danych na komputerze lokalnym zalecanym rozwiązaniem jest użycie SQLite, w którym jest uruchomiona w tym samym procesie co aplikacja. Jeśli warstwa relacyjnej obiektu mapowania (ORM) jest wymagana, można użyć programu Entity Framework. Aby uzyskać więcej informacji, zobacz [dostęp do danych](https://msdn.microsoft.com/windows/uwp/data-access/index) w Centrum deweloperów systemu Windows.

Jeśli łączysz się z usługami Azure, pamiętaj pobrać najnowszą [Azure SDK tools](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Dostawcy danych

Aby baza danych jest dostępne w ADO.NET, musi on mieć niestandardowej *dostawcy danych ADO.NET* lub #else musi ujawniać interfejsu ODBC lub OLE DB. Firma Microsoft udostępnia [listą dostawców danych ADO.NET](https://msdn.microsoft.com/data/dd363565) dla produktów programu SQL Server, a także dostawców ODBC i OLE DB.

### <a name="data-modeling"></a>Modelowanie danych

W środowisku .NET wyświetlane są trzy opcje do modelowania i manipulację danymi w pamięci po jej pobraniu ze źródła danych:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md)  
Preferowaną technologią ORM firmy Microsoft. Służy on do program względem danych relacyjnych jako najwyższej jakości obiekty .NET. Dla nowych aplikacji należy najpierw wybrać domyślne gdy model jest wymagany. Wymaga dodatkowej pomocy technicznej z podstawowym dostawcy ADO.NET.

[LINQ do SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
Mapowania obiektów relacyjnych wcześniejszych generacji. Sprawdza się w przypadku mniej złożonych scenariuszy, ale nie jest już aktywne programowanie.

[Zbiory danych](../data-tools/dataset-tools-in-visual-studio.md)  
Najstarsze trzy technologie modelowania. Jest on przeznaczony głównie dla szybkiego opracowywania aplikacji "formularzy nad danymi", w których są nie przetwarzania dużych ilości danych lub wykonywanie złożonych zapytań lub przekształcenia. Obiekt DataSet składa się z elementu DataTable i DataRow obiektów, które logicznie przypominają bardziej obiekty .NET obiektów bazy danych SQL. Stosunkowo proste aplikacje oparte na SQL źródła danych zestawy danych może nadal być dobrym rozwiązaniem.

Nie jest wymagane, aby użyć dowolnego z tych technologii. W niektórych scenariuszach, szczególnie w przypadku, gdy ma kluczowe znaczenie, po prostu umożliwia obiektu DataReader odczytu z bazy danych i skopiuj wartości, które należy do obiektu kolekcji, takie jak listy\<T >.

## <a name="native-c"></a>Natywnych języka C++

Aplikacje w języku C++ łączących się z programem SQL Server należy używać [Microsoft® ODBC sterownika 13.1 dla programu SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) w większości przypadków. Jeśli serwery są połączone, konieczne jest OLE DB i do tego użyć [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Dostęp do innych baz danych przy użyciu [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) lub bezpośrednio sterowników OLE DB. ODBC jest bieżący interfejs standardowego bazy danych, ale większość systemów bazy danych zawiera funkcje niestandardowe, które nie będą dostępne za pośrednictwem interfejsu ODBC. OLE DB jest starszych technologii dostępu do danych COM, który jest nadal obsługiwane, ale nie jest zalecane dla nowych aplikacji. Aby uzyskać więcej informacji, zobacz [dostęp do danych w programie Visual C++](https://docs.microsoft.com/cpp/data/).

Programy używające usługi REST w języku C++ można użyć [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Programy C++, które współpracują z usługi Magazyn Microsoft Azure mogą używać [klienta magazynu Microsoft Azure](http://www.nuget.org/packages/wastorage).

Modelowanie danych&mdash;programu Visual Studio nie ma warstwy ORM dla języka C++. [ODB](http://www.codesynthesis.com/products/odb/) jest popularnych ORM open source dla języka C++.

Aby dowiedzieć się więcej o nawiązywaniu połączeń z bazami danych z aplikacji C++, zobacz [narzędzi danych programu Visual Studio dla języka C++](../data-tools/visual-studio-data-tools-for-cpp.md). Aby uzyskać więcej informacji na temat starszych technologii dostępu do danych Visual C++, zobacz [dostęp do danych](http://msdn.microsoft.com/Library/a9455752-39c4-4457-b14e-197772d3df0b).

## <a name="javascript"></a>JavaScript

[JavaScript w programie Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) jest językiem pierwszej klasy umożliwiające tworzenie wieloplatformowych aplikacji, aplikacji platformy uniwersalnej systemu Windows, usługi w chmurze, witryn sieci Web i aplikacji sieci web. Bower, Grunt, Gulp, npm i NuGet z poziomu programu Visual Studio można użyć do zainstalowania z ulubionych bibliotek JavaScript i produkty bazy danych. Podłączanie do magazynu Azure i usług przez pobieranie zestawów SDK z [witryny sieci Web Azure](https://azure.microsoft.com/). Edge.js jest biblioteki, która łączy się ze źródłami danych ADO.NET JavaScript po stronie serwera (Node.js).

## <a name="python"></a>Python

Zainstaluj [narzędzi Python Tools for Visual Studio](http://microsoft.github.io/PTVS/) wraz z ulubionych framework Python w taki sposób, aby tworzyć aplikacje języka CPython lub IronPython (.NET). Narzędzia Python Tools for Visual Studio witryny sieci Web ma kilka samouczki dotyczące nawiązywania połączenia danych, w tym [Django i bazy danych SQL Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django i MySQL na platformie Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) i [Bottle i bazy danych MongoDB na Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="related-topics"></a>Tematy pokrewne

[Dane, urządzeń i analiza](https://msdn.microsoft.com/data-and-devices)  
Wprowadzenie do chmury inteligentnego firmy Microsoft, w tym Cortana Analytics Suite i obsługę Internetu rzeczy.

[Magazyn Microsoft Azure](https://azure.microCsoft.com/documentation/services/storage/)  
Zawiera opis usługi Azure Storage i jak tworzyć aplikacje przy użyciu Azure blob, tabel, kolejek i plików.

[Baza danych Azure SQL](https://azure.microsoft.com/documentation/services/sql-database/)  
Zawiera opis sposobu łączenia z bazą danych Azure SQL, relacyjnej bazy danych jako usługa.

[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)  
Zawiera opis narzędzi, które upraszczają proces projektowania, eksploracji, testowania i wdrażania aplikacji połączonych danych i baz danych.

[ADO.NET](/dotnet/framework/data/adonet/index)  
Opis architektury ADO.NET i jak używać klas ADO.NET, aby zarządzać danych aplikacji i korzystać z źródła danych i XML.

[ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)  
Opisuje sposób tworzenia aplikacji danych, które umożliwiają deweloperom program w odniesieniu do modelu koncepcyjnego zamiast bezpośrednio przed relacyjnej bazy danych.

[Usługi danych WCF 4.5](/dotnet/framework/data/wcf/index)  
Informacje dotyczące używania [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] do wdrożenia usług danych w Internecie lub intranecie, które implementują [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

[Dane w rozwiązaniach pakietu Office](/office-dev/office-dev/data-in-office-solutions)  
Zawiera linki do tematów, w których opisano, jak działa dane w rozwiązaniach pakietu Office. W tym informacje o programowanie zorientowane na schemat, buforowanie danych i dostępu do danych po stronie serwera.

[LINQ (zapytania o języku zintegrowanym)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
Zawiera opis możliwości zapytania wbudowanych w języku C# i Visual Basic i wspólnego modelu do wykonywania zapytań relacyjnych baz danych, dokumentów XML, zestawy danych i kolekcji w pamięci.

[Narzędzia XML w Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)  
Zawiera omówienie pracy z funkcjami programu .NET Framework XML debugowania XSLT danych XML i architektura zapytanie w języku XML.

[Dokumenty XML i dane](/dotnet/standard/data/xml/index)  
Zawiera omówienie kompleksowy, zintegrowany zestaw klas, które współpracują z dokumentów XML i danych w programie .NET Framework.