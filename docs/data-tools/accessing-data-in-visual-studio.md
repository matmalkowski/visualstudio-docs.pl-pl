---
title: Uzyskiwanie dostępu do danych w programie Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4b43463dc35fa3f9703162817f6a8d63f44a87b8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="accessing-data-in-visual-studio"></a>Uzyskiwanie dostępu do danych w programie Visual Studio

W programie Visual Studio, można utworzyć aplikacji, które łączenie z danymi w praktycznie dowolne bazy danych produktu lub usługi, w dowolnym miejscu i formatu — na komputerze lokalnym, w sieci lokalnej lub w chmurze public, private lub hybrydowego.

W przypadku aplikacji w JavaScript, Python, PHP, Ruby lub C++ połączenie z danych tak jak wykonywanie dodatkowych czynności, uzyskując bibliotek i pisanie kodu. W przypadku aplikacji .NET Visual Studio udostępnia narzędzia, które umożliwia Eksplorowanie źródeł danych, tworzyć modele obiektów do przechowywania i obsługi danych w pamięci i powiązania danych interfejsu użytkownika. Microsoft Azure udostępnia zestawy SDK dla platformy .NET, Java, Node.js, PHP, Python, Ruby i aplikacji mobilnych i narzędzia programu Visual Studio do połączenia usługi Azure Storage.

Następujące przedstawiono kilka z wielu systemów magazynu i bazy danych, które mogą być używane w programie Visual Studio. [Microsoft Azure](https://azure.microsoft.com/) oferty są usług danych, które obejmują wszystkie inicjowania obsługi i zarządzania odpowiedni magazyn danych.  [Azure Tools dla Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) jest opcjonalnym składnikiem, który umożliwia pracę z magazynów Azure danych bezpośrednio z programu Visual Studio. Większości produktów innych SQL i NoSQL bazy danych wymienione w tym miejscu może być obsługiwany na komputerze lokalnym, w sieci lokalnej lub w systemie Microsoft Azure na maszynie wirtualnej. W tym scenariuszu jest odpowiedzialny za zarządzanie sama baza danych.

**Microsoft Azure**

||||
|-|-|-|
|Baza danych SQL|Azure Cosmos DB|Magazyn (obiekty BLOB, tabel, kolejek, plików)|
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
|Apache Cassandra|CouchDB|MongoDB|
|Lokalizacji|OrientDB|RavenDB|
|VelocityDB|||

i więcej...

Wielu dostawców bazy danych i stron trzecich obsługiwać integracji z programem Visual Studio pakietów NuGet. Można eksplorować oferty nuget.org lub za pomocą Menedżera pakietów NuGet w programie Visual Studio (**narzędzia** > **Menedżera pakietów NuGet** > **zarządzania pakietami NuGet Pakietami dla rozwiązania**). Inne produkty bazy danych integracji z programem Visual Studio jako rozszerzenie. Przeglądaj tych ofert w programie Visual Studio Marketplace, przechodząc do **narzędzia**, **rozszerzenia i aktualizacje** , a następnie wybierając **Online** w okienku po lewej stronie okno dialogowe. Aby uzyskać więcej informacji, zobacz [systemów zgodne bazy danych dla programu Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Rozszerzona obsługa programu SQL Server 2005 zakończona w dniu 12 kwietnia 2016 r. Nie ma żadnej gwarancji, że narzędzia danych w programie Visual Studio 2015 i później będą nadal działały z programu SQL Server 2005 po tej dacie. Aby uzyskać więcej informacji, zobacz [powiadomienia zakończenia pomocy technicznej dla programu SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Języków .NET

Wszystkie .NET dostępu do danych, w tym w .NET Core jest oparta na ADO.NET, zestaw klas, który definiuje interfejs do uzyskiwania dostępu do dowolnego rodzaju źródła danych relacyjnych i nierelacyjnych. Visual Studio ma kilka narzędzi i projektantów, które współpracują z ADO.NET umożliwiające nawiązywanie połączeń z bazami danych, manipulowania danymi i przedstawiają dane do użytkownika. Dokumentacja w tej sekcji opisano sposób używania tych narzędzi. Można również zaprogramować bezpośrednio przed ADO.NET— obiekty polecenia. Aby uzyskać więcej informacji na temat bezpośrednie wywoływanie interfejsów API ADO.NET, zobacz [ADO.NET](/dotnet/framework/data/adonet/index).

Dokumentacja dostępu do danych związane z platformy ASP.NET, zobacz [Praca z danymi](http://www.asp.net/web-forms/overview/presenting-and-managing-data) w witrynie platformy ASP.NET. Samouczek na platformie ASP.NET MVC przy użyciu programu Entity Framework, zobacz [wprowadzenie do programu Entity Framework 6 Code First przy użyciu MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Uniwersalnych aplikacji platformy systemu Windows (UWP) w języku C# lub Visual Basic umożliwia dostęp do usługi Azure Storage i innymi usługami Azure zestaw Microsoft Azure SDK dla platformy .NET. Klasa Windows.Web.HttpClient umożliwia komunikację z dowolnej usługi RESTful. Aby uzyskać więcej informacji, zobacz [sposób nawiązywania połączenia z serwerem HTTP przy użyciu Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Do przechowywania danych na komputerze lokalnym zalecanym rozwiązaniem jest użycie SQLite, w którym jest uruchomiona w tym samym procesie co aplikacja. Jeśli warstwa relacyjnej obiektu mapowania (ORM) jest wymagana, można użyć programu Entity Framework. Aby uzyskać więcej informacji, zobacz [dostęp do danych](/windows/uwp/data-access/index) w Centrum deweloperów systemu Windows.

Jeśli łączysz się z usługami Azure, pamiętaj pobrać najnowszą [Azure SDK tools](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Dostawcy danych

Aby baza danych jest dostępne w ADO.NET, musi on mieć niestandardowej *dostawcy danych ADO.NET* lub #else musi ujawniać interfejsu ODBC lub OLE DB. Firma Microsoft udostępnia [listą dostawców danych ADO.NET](https://msdn.microsoft.com/data/dd363565) dla produktów programu SQL Server, a także dostawców ODBC i OLE DB.

### <a name="data-modeling"></a>Modelowanie danych

W środowisku .NET wyświetlane są trzy opcje do modelowania i manipulację danymi w pamięci po jej pobraniu ze źródła danych:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) preferowaną technologią ORM firmy Microsoft. Służy on do program względem danych relacyjnych jako najwyższej jakości obiekty .NET. Dla nowych aplikacji należy najpierw wybrać domyślne gdy model jest wymagany. Wymaga dodatkowej pomocy technicznej z podstawowym dostawcy ADO.NET.

[LINQ do SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) mapowania obiektów relacyjnych wcześniejszych generacji. Sprawdza się w przypadku mniej złożonych scenariuszy, ale nie jest już aktywne programowanie.

[Zestawy danych](../data-tools/dataset-tools-in-visual-studio.md) najstarsze trzy technologie modelowania. Jest on przeznaczony głównie dla szybkiego opracowywania aplikacji "formularzy nad danymi", w których są nie przetwarzania dużych ilości danych lub wykonywanie złożonych zapytań lub przekształcenia. Obiekt DataSet składa się z elementu DataTable i DataRow obiektów, które logicznie przypominają bardziej obiekty .NET obiektów bazy danych SQL. Stosunkowo proste aplikacje oparte na SQL źródła danych zestawy danych może nadal być dobrym rozwiązaniem.

Nie jest wymagane, aby użyć dowolnego z tych technologii. W niektórych scenariuszach, szczególnie w przypadku, gdy ma kluczowe znaczenie, po prostu umożliwia obiektu DataReader odczytu z bazy danych i skopiuj wartości, które należy do obiektu kolekcji, takie jak listy\<T >.

## <a name="native-c"></a>Natywnych języka C++

Aplikacje w języku C++ łączących się z programem SQL Server należy używać [Microsoft® ODBC sterownika 13.1 dla programu SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) w większości przypadków. Jeśli serwery są połączone, konieczne jest OLE DB i do tego użyć [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Dostęp do innych baz danych przy użyciu [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) lub bezpośrednio sterowników OLE DB. ODBC jest bieżący interfejs standardowego bazy danych, ale większość systemów bazy danych zawiera funkcje niestandardowe, które nie będą dostępne za pośrednictwem interfejsu ODBC. OLE DB jest starszych technologii dostępu do danych COM, który jest nadal obsługiwane, ale nie jest zalecane dla nowych aplikacji. Aby uzyskać więcej informacji, zobacz [dostęp do danych w programie Visual C++](/cpp/data/data-access-in-cpp).

Programy używające usługi REST w języku C++ można użyć [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Programy C++, które współpracują z usługi Magazyn Microsoft Azure mogą używać [klienta magazynu Microsoft Azure](http://www.nuget.org/packages/wastorage).

Modelowanie danych&mdash;programu Visual Studio nie ma warstwy ORM dla języka C++. [ODB](http://www.codesynthesis.com/products/odb/) jest popularnych ORM open source dla języka C++.

Aby dowiedzieć się więcej o nawiązywaniu połączeń z bazami danych z aplikacji C++, zobacz [narzędzi danych programu Visual Studio dla języka C++](../data-tools/visual-studio-data-tools-for-cpp.md). Aby uzyskać więcej informacji na temat starszych technologii dostępu do danych Visual C++, zobacz [dostęp do danych](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript w programie Visual Studio](/scripting/javascript/javascript-language-reference) jest językiem pierwszej klasy umożliwiające tworzenie wieloplatformowych aplikacji, aplikacji platformy uniwersalnej systemu Windows, usługi w chmurze, witryn sieci Web i aplikacji sieci web. Bower, Grunt, Gulp, npm i NuGet z poziomu programu Visual Studio można użyć do zainstalowania z ulubionych bibliotek JavaScript i produkty bazy danych. Podłączanie do magazynu Azure i usług przez pobieranie zestawów SDK z [witryny sieci Web Azure](https://azure.microsoft.com/). Edge.js jest biblioteki, która łączy się ze źródłami danych ADO.NET JavaScript po stronie serwera (Node.js).

## <a name="python"></a>Python

Zainstaluj [Python obsługi w programie Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) do tworzenia aplikacji Python. Dokumentację platformy Azure ma kilka samouczków na łączenie z danymi, takie jak następujące:

- [Obsługa platformy Django i bazy danych SQL Azure](/azure/app-service/app-service-web-get-started-python)
- [Obsługa platformy Django i MySQL na platformie Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Praca z [obiekty BLOB](/azure/storage/blobs/storage-quickstart-blobs-python), [pliki](/azure/storage/files/storage-python-how-to-use-file-storage), [kolejek](/azure/storage/queues/storage-python-how-to-use-queue-storage), i [tabele (DB kosmetyczka)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Tematy pokrewne

[Platforma Microsoft AI](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;zawiera wprowadzenie do chmury inteligentnego firmy Microsoft, w tym Cortana Analytics Suite i obsługę Internetu rzeczy.

[Microsoft Azure Storage](/azure/storage/)&mdash;zawiera opis usługi Azure Storage i jak tworzyć aplikacje przy użyciu Azure blob, tabel, kolejek i plików.

[Baza danych SQL Azure](/azure/sql-database/)&mdash;opisano sposób podłączania do usługi Azure SQL Database, relacyjnej bazy danych jako usługa.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;opisano narzędzia, które upraszczają proces projektowania, eksploracji, testowania i wdrażania aplikacji połączonych danych i baz danych.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;opis architektury ADO.NET i jak używać klas ADO.NET, aby zarządzać danych aplikacji i korzystać z źródła danych i XML.

[ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)&mdash;opisuje sposób tworzenia aplikacji danych, które umożliwiają deweloperom program w odniesieniu do modelu koncepcyjnego zamiast bezpośrednio przed relacyjnej bazy danych.

[4.5 usługi danych WCF](/dotnet/framework/data/wcf/index)&mdash;informacje dotyczące używania [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] do wdrożenia usług danych w Internecie lub intranecie, które implementują [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

[Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)&mdash;zawiera linki do tematów, w których opisano, jak działa dane w rozwiązaniach pakietu Office. W tym informacje o programowanie zorientowane na schemat, buforowanie danych i dostępu do danych po stronie serwera.

[LINQ (zapytania język Language-Integrated)](/dotnet/csharp/linq/)&mdash;zawiera opis możliwości zapytania wbudowanych w języku C# i Visual Basic i wspólnego modelu do wykonywania zapytań relacyjnych baz danych, dokumentów XML, zestawy danych i kolekcji w pamięci.

[Narzędzia XML w Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;omówiono pracy z funkcjami programu .NET Framework XML debugowania XSLT danych XML i architektura zapytanie w języku XML.

[Dokumenty XML i dane](/dotnet/standard/data/xml/index)&mdash;zawiera omówienie kompleksowy, zintegrowany zestaw klas, które współpracują z dokumentów XML i danych w programie .NET Framework.
