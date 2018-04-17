---
title: Narzędzia zestawu danych w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7db4eaf50f04d0baf082f6612ee7bd13a0d30ed6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="dataset-tools-in-visual-studio"></a>Narzędzia zestawu danych w programie Visual Studio
> [!NOTE]
>  Zestawy danych i klas pokrewnych są starsze technologii .NET z wczesnym 2000s, które umożliwiają aplikacjom pracować z danymi w pamięci, odłączeniu aplikacji z bazy danych. Są one szczególnie przydatne w przypadku aplikacji, które umożliwiają użytkownikom modyfikowanie danych i utrwalania zmian w bazie danych. Mimo że zestawy danych okazały się bardzo pomyślne technologii, zalecane jest użycie programu Entity Framework nowych aplikacji .NET. Entity Framework zapewnia bardziej naturalne sposób pracy z danych tabelarycznych jako modele obiektów i ma prostsze interfejsu programowania.  
  
 Obiekt DataSet jest obiektem w pamięci, który jest zasadniczo mini bazy danych. Zawiera obiekty DataTable, DataColumn i DataRow, w których można przechowywać i modyfikowanie danych z jednego lub więcej baz danych bez konieczności obsługi otwartego połączenia. Zestawu danych przechowuje informacje o zmianach wprowadzonych w danych, więc aktualizacje mogą być śledzone i odesłany do bazy danych, gdy aplikacja stanie się ponownie.  
  
 Zestawy danych i klas pokrewnych są zdefiniowane w obszarze nazw System.dane w bibliotece klas programu .NET Framework. Można tworzyć i modyfikować zestawy danych dynamicznie w kodzie. Aby uzyskać więcej informacji o tym, jak to zrobić Zobacz ADO.NET. Dokumentacja w tej sekcji przedstawiono sposób pracy z zestawami danych przy użyciu programu Visual Studio projektantów. Jedyną operacją, należy wiedzieć: zestawów danych, które są nawiązywane przy użyciu projektantów użyć obiektów TableAdapter do interakcji z bazy danych, podczas gdy zestawów danych wprowadzonych programowo obiektów element DataAdapter. Informacji o tworzeniu zestawów danych programowo, zobacz [obiektów DataAdapter i DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).  
  
 Jeśli aplikacja wymaga tylko do odczytu danych z bazy danych i wykonuje aktualizacje, dodaje lub usuwa, można zwykle osiągnąć wyższą wydajność przy użyciu obiektu DataReader do pobierania danych do ogólnego obiekt listy lub innej kolekcji. Jeśli dane są wyświetlane, użytkownik może wiązania danych interfejsu użytkownika do kolekcji.  
  
## <a name="dataset-workflow"></a>Zestaw danych przepływu pracy  
 Program Visual Studio udostępnia wiele narzędzi do uproszczenia pracy z zestawami danych. Podstawowy przepływ pracy end-to-end jest:  
  
-   Użyj **źródła danych** okna, aby utworzyć nowy zestaw danych z jednego lub więcej źródeł danych. Użyj **Projektant obiektów Dataset** do konfigurowania zestawu danych i ustawienia swoich właściwości. Na przykład należy określić tabel ze źródła danych do uwzględnienia, a które kolumny w każdej tabeli. Wybierz uważnie zaoszczędzić ilość pamięci, która wymaga zestawu danych. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Określ relacje między tabelami, dzięki czemu klucze obce są prawidłowo obsługiwane. Aby uzyskać więcej informacji, zobacz [wypełnienia zestawów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
-   Użyj **TableAdapter Kreator konfiguracji** do określenia zapytania lub procedury przechowywanej, która będzie wypełniania zestawu danych i jakie operacje bazy danych (update, delete itd.) do wdrożenia. Aby uzyskać więcej informacji zobacz następujące tematy:  
  
    -   [Wypełnianie zbiorów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [Edytowanie danych w zestawach danych](../data-tools/edit-data-in-datasets.md)  
  
    -   [Weryfikowanie danych w zestawach danych](../data-tools/validate-data-in-datasets.md)  
  
    -   [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)  
  
-   Zapytania i wyszukiwanie danych w zestawie danych. Aby uzyskać więcej informacji, zobacz [zapytania zestawów danych](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] Umożliwia [LINQ (zapytania język Language-Integrated)](/dotnet/csharp/linq/) nad danymi w <xref:System.Data.DataSet> obiektu. Aby uzyskać więcej informacji, zobacz [LINQ do DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
-   Użyj **źródeł danych** okna powiązanie formantów interfejsu użytkownika do zestawu danych lub jego poszczególnych kolumn i określić, które kolumny będą można edytować użytkownika. Aby uzyskać więcej informacji, zobacz [powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="datasets-and-n-tier-architecture"></a>Architektura zestawów danych i N-warstwowa  
 Aby uzyskać informacje dotyczące zestawów danych w aplikacjach warstwowych, zobacz [Praca z zestawami danych w aplikacjach warstwowych](../data-tools/work-with-datasets-in-n-tier-applications.md).  
  
## <a name="datasets-and-xml"></a>Zestawy danych i XML  
 Aby dowiedzieć się, jak konwertowanie zestawów danych do i z pliku XML, zobacz [danych XML odczytu do zestawu danych](../data-tools/read-xml-data-into-a-dataset.md) i [Zapisywanie zestawu danych jako XML](../data-tools/save-a-dataset-as-xml.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)