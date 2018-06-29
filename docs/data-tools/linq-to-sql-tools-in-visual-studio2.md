---
title: Visual Studio Projektanta obiektów relacyjnych — omówienie
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7c7abaa95c3b7c8f5ab78b4d58f383243b176f7a
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089415"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ do SQL narzędzi w programie Visual Studio

LINQ do SQL był pierwszy technologii mapowania obiektu relacyjnego wydane przez firmę Microsoft. Działa dobrze w podstawowe scenariusze i może być obsługiwany w programie Visual Studio, ale nie jest już opracowywane aktywne. Użyj LINQ do SQL podczas obsługi starszych aplikacji, który już jest używany lub w aplikacjach proste, użyj programu SQL Server, które nie wymagają mapowania wielu tabel. Ogólnie rzecz biorąc nowych aplikacji należy używać programu Entity Framework, gdy wymagana jest warstwa relacyjnej obiektu mapowania.

W programie Visual Studio Utwórz LINQ w klasach SQL, które reprezentują tabel SQL przy użyciu **Projektant obiektów relacyjnych** (**Projektanta obiektów relacyjnych**).

**Projektanta obiektów relacyjnych** ma dwa różne obszary na jego powierzchni projektowej: jednostek okienka po lewej stronie i metod po prawej stronie. W okienku jednostek jest powierzchnię projektu głównego, który wyświetla klas jednostek, powiązania i hierarchii dziedziczenia. W okienku metod jest powierzchnię projektu, który wyświetla <xref:System.Data.Linq.DataContext> metod, które są mapowane na procedury składowane i funkcje.

**Projektanta obiektów relacyjnych** zapewnia powierzchni wizualnego projektu do tworzenia [LINQ do SQL](/dotnet/framework/data/adonet/sql/linq/index) klas jednostek i skojarzenia (relacji), które są oparte na obiektach w bazie danych. Innymi słowy **Projektanta obiektów relacyjnych** tworzy model obiektów w aplikacji, która mapuje do obiektów w bazie danych. Generowany jest również silnie typizowanego <xref:System.Data.Linq.DataContext> która wysyła i odbiera dane między klasami jednostki i bazy danych. **Projektanta obiektów relacyjnych** również funkcje do mapowania procedury składowane i funkcje, które mają <xref:System.Data.Linq.DataContext> metody zwracający dane i wypełniania klas jednostek. Na koniec **Projektanta obiektów relacyjnych** zapewnia możliwość projektowania relacji dziedziczenia między klasami jednostki.

## <a name="open-the-or-designer"></a>Otwórz Projektanta obiektów relacyjnych

Aby dodać LINQ do SQL modelu jednostki do projektu, wybierz **projektu** > **Dodaj nowy element**, a następnie wybierz **klasy LINQ do SQL** z listy elementów projektu:

![Klasy LINQ do SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Program Visual Studio tworzy *.dbml* plików i dodaje go do rozwiązania. Jest to plik mapowania XML i jego pliki kodu powiązanego.

![Klasy LINQ do SQL w Eksploratorze rozwiązań](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Po wybraniu *.dbml* plików programu Visual Studio zawiera **Projektanta obiektów relacyjnych** powierzchni, która pozwala wizualnie tworzyć modelu. Na poniższej ilustracji przedstawiono projektanta po Northwind `Customers` i `Orders` tabel ma zostać przeciągnięte z **Eksploratora serwera**. Należy zwrócić uwagę relacji między tabelami.

![LINQ do SQL projektanta](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **Projektanta obiektów relacyjnych** jest mapowania relacyjnego prostego obiektu, ponieważ obsługuje on tylko relacje 1:1 mapowania. Innymi słowy Klasa jednostki może mieć tylko relacji mapowania 1:1 z tabeli bazy danych lub widoku. Mapowanie złożonych, takie jak mapowania klasy jednostki do tabeli dołączonego do nie jest obsługiwany; Użyj programu Entity Framework dla złożonych mapowania. Ponadto projektanta jest generator kodu jednokierunkowe. Oznacza to, że tylko zmiany wprowadzone na powierzchnię projektanta są odzwierciedlane w pliku kodu. Ręczne wprowadzanie zmian w pliku kodu nie są uwzględnione w **Projektanta obiektów relacyjnych**. Wszelkie zmiany wprowadzone ręcznie w pliku kodu zostaną zastąpione, gdy projektant jest zapisywana i ponownego wygenerowania kodu. Informacje o tym, jak dodać kod użytkownika i rozszerzenie klasy generowane przez **Projektanta obiektów relacyjnych**, zobacz [porady: rozszerzanie kod wygenerowany przez Projektanta obiektów relacyjnych](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Tworzenie i konfigurowanie DataContext

Po dodaniu **klasy LINQ do SQL** elementu do projektu i Otwórz **Projektanta obiektów relacyjnych**, pusty powierzchnię reprezentuje pustą <xref:System.Data.Linq.DataContext> gotowe do skonfigurowania. <xref:System.Data.Linq.DataContext> jest skonfigurowana z informacjami dotyczącymi połączenia udostępniane przez pierwszy element zostanie przeciągnięty na powierzchnię projektu. W związku z tym <xref:System.Data.Linq.DataContext> jest konfigurowana przy użyciu informacji o połączeniu z poziomu pierwszego elementu porzucony na powierzchnię projektu. Aby uzyskać więcej informacji na temat <xref:System.Data.Linq.DataContext> , zobacz klasy [metodę DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Tworzenie klas jednostek mapowane na bazę danych, tabele i widoki

Możesz tworzyć klasy jednostki zamapowane do tabel i widoków przeciągając tabele i widoki z **Eksploratora serwera** lub **Eksploratora bazy danych** na **Projektanta obiektów relacyjnych**. Jak wskazano w poprzedniej sekcji <xref:System.Data.Linq.DataContext> jest skonfigurowana z informacjami dotyczącymi połączenia udostępniane przez pierwszy element zostanie przeciągnięty na powierzchnię projektu. Jeśli kolejne elementu, który używa innego połączenia jest dodawany do **Projektanta obiektów relacyjnych**, można zmienić połączenia dla <xref:System.Data.Linq.DataContext>. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie klasy LINQ do SQL zamapowane do tabel i widoków (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Utwórz metody DataContext, które mogą wywoływać procedury składowane i funkcje

Można utworzyć <xref:System.Data.Linq.DataContext> metod, które wywołują (są mapowane na) procedury składowane i funkcje, przeciągając je z **Eksploratora serwera** lub **Eksploratora bazy danych** na **Projektanta obiektów relacyjnych** . Procedury składowane i funkcje zostaną dodane do **Projektanta obiektów relacyjnych** jako metody <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Przeciągnięcie procedury składowane i funkcje z **Eksploratora serwera** lub **Eksploratora bazy danych** na **Projektanta obiektów relacyjnych**, zwracany typ wygenerowany <xref:System.Data.Linq.DataContext> metoda różni się w zależności od tego, gdzie upuścić element. Aby uzyskać więcej informacji, zobacz [metodę DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Skonfiguruj DataContext zapisują dane pomiędzy klasami jednostki i w bazie danych przy użyciu procedur składowanych

Jak wspomniano wcześniej, można utworzyć <xref:System.Data.Linq.DataContext> metod, które mogą wywoływać procedury składowane i funkcje. Ponadto można także przypisać procedur składowanych, które są używane do domyślnego LINQ do zachowania w czasie wykonywania SQL, który przeprowadza wstawiania, aktualizacji i usuwania. Aby uzyskać więcej informacji, zobacz [porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Projektant obiektów relacyjnych i dziedziczenie

Podobnie jak inne obiekty klasy LINQ do SQL można użyć dziedziczenia i pochodzić z innych klas. W bazie danych relacji dziedziczenia są tworzone na kilka sposobów. **Projektanta obiektów relacyjnych** obsługuje koncepcja dziedziczenia pojedynczej tabeli, jak często jest zaimplementowana w systemach relacyjnych. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie dziedziczenia za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>LINQ do SQL zapytań

Klasy jednostki tworzone przez **Projektanta obiektów relacyjnych** są przeznaczone do użytku z [zapytanie o języku zintegrowanym (LINQ)](/dotnet/csharp/linq/). Aby uzyskać więcej informacji, zobacz [porady: Kwerenda dotycząca informacji](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Oddziel wygenerowany kod klasy DataContext i jednostek w różnych przestrzeniach nazw

**Projektanta obiektów relacyjnych** zapewnia **Namespace kontekstu** i **Namespace jednostki** właściwości <xref:System.Data.Linq.DataContext>. Te właściwości określają, jakie przestrzeni nazw <xref:System.Data.Linq.DataContext> i do zostaje wygenerowany kod klasy jednostki. Domyślnie te właściwości są puste i <xref:System.Data.Linq.DataContext> i klas jednostek są generowane w przestrzeni nazw aplikacji. Aby wygenerować kod w przestrzeni nazw innych niż przestrzeń nazw aplikacji, wprowadź wartość do **Namespace kontekstu** i/lub **Namespace jednostki** właściwości.

## <a name="reference-content"></a>Odwołanie do zawartości

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Często zadawane pytania (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)