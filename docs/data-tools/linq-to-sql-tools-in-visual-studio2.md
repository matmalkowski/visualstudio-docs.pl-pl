---
title: "Visual Studio Projektanta obiektów relacyjnych — omówienie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: cba3d5568ee2fa2b4af0eb9c10995c813fe09c01
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ do SQL narzędzia w programie Visual Studio
LINQ do SQL był pierwszy technologii mapowania obiektu relacyjnego wydane przez firmę Microsoft. Działa dobrze w podstawowe scenariusze i może być obsługiwany w programie Visual Studio, ale nie jest już opracowywane aktywne. Użyj LINQ do SQL podczas obsługi starszych aplikacji, który już jest używany lub w aplikacjach proste, użyj programu SQL Server, które nie wymagają mapowania wielu tabel. Ogólnie rzecz biorąc nowych aplikacji należy używać programu Entity Framework, gdy wymagana jest warstwa relacyjnej obiektu mapowania.  
  
W programie Visual Studio możesz utworzyć LINQ w klasach SQL, które reprezentują tabel SQL za pomocą Projektanta obiektów relacyjnych (Projektanta obiektów relacyjnych).  
  
[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Ma dwa różne obszary na jego powierzchni projektowej: jednostek okienka po lewej stronie i metod po prawej stronie. W okienku jednostek jest powierzchnię projektu głównego, który wyświetla klas jednostek, powiązania i hierarchii dziedziczenia. W okienku metod jest powierzchnię projektu, który wyświetla <xref:System.Data.Linq.DataContext> metod, które są mapowane na procedury składowane i funkcje.  
  
[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Zapewnia powierzchni wizualnego projektu do tworzenia [LINQ do SQL](/dotnet/framework/data/adonet/sql/linq/index) klas jednostek i skojarzenia (relacji), które są oparte na obiektach w bazie danych. Innymi słowy [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] służy do tworzenia modeli obiektów w aplikacji, która mapuje do obiektów w bazie danych. Generowany jest również silnie typizowanego <xref:System.Data.Linq.DataContext> używany do wysyłania i odbierania danych między klasami jednostki i bazy danych. [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Również funkcje do mapowania procedury składowane i funkcje, które mają <xref:System.Data.Linq.DataContext> metody zwracający dane i wypełniania klas jednostek. Na koniec [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] zapewnia możliwość projektowania relacji dziedziczenia między klasami jednostki.  
  
## <a name="opening-the-or-designer"></a>Otworzyć Projektanta obiektów relacyjnych  
 Aby dodać LINQ do SQL modelu jednostki do projektu, wybierz **projektu**, **Dodaj nowy element** , a następnie wybierz **klasy LINQ do SQL** z listy elementów projektu:  
  
 ![Klasy LINQ do SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata klasy LINQ do SQL")  
  
 Visual Studio tworzy plik .dbml i dodaje go do rozwiązania. Jest to plik mapowania XML i jego pliki kodu powiązanego.  
  
 ![Klasy LINQ do SQL w Eksploratorze rozwiązań](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ do SQL klas w Eksploratorze rozwiązań")  
  
 Po wybraniu pliku .dbml programu Visual Studio zawiera powierzchnię Projektanta obiektów relacyjnych umożliwia wizualnie tworzyć modelu. Na poniższej ilustracji przedstawiono projektanta po tabeli klientów Northwind i zamówień został przeciągnięty, z poziomu Eksploratora serwera. Należy zwrócić uwagę relacji między tabelami.  
  
 ![LINQ do SQL projektanta](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ do SQL projektanta")  
  
> [!IMPORTANT]
>  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Jest mapowania relacyjnego prostego obiektu, ponieważ obsługuje on tylko relacje 1:1 mapowania. Innymi słowy Klasa jednostki może mieć tylko relacji mapowania 1:1 z tabeli bazy danych lub widoku. Mapowanie złożonych, takie jak mapowania klasy jednostki do tabeli dołączonego do nie jest obsługiwany; Użyj programu Entity Framework dla złożonych mapowania. Ponadto projektanta jest generator kodu jednokierunkowe. Oznacza to, że tylko zmiany wprowadzone na powierzchnię projektanta są odzwierciedlane w pliku kodu. Ręczne wprowadzanie zmian w pliku kodu nie są uwzględnione w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Wszelkie zmiany wprowadzone ręcznie w pliku kodu zostaną zastąpione, gdy projektant jest zapisywana i ponownego wygenerowania kodu. Informacje o tym, jak dodać kod użytkownika i rozszerzenie klasy generowane przez [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], zobacz [porady: rozszerzanie kod wygenerowany przez Projektanta obiektów relacyjnych](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).  
  
## <a name="creating-and-configuring-the-datacontext"></a>Tworzenie i konfigurowanie DataContext  
 Po dodaniu **klasy LINQ do SQL** elementu do projektu i Otwórz [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], pusty powierzchnię reprezentuje pustą <xref:System.Data.Linq.DataContext> gotowe do skonfigurowania. <xref:System.Data.Linq.DataContext> jest skonfigurowana z informacjami dotyczącymi połączenia udostępniane przez pierwszy element zostanie przeciągnięty na powierzchnię projektu. W związku z tym <xref:System.Data.Linq.DataContext> jest konfigurowana przy użyciu informacji o połączeniu z poziomu pierwszego elementu porzucony na powierzchnię projektu. Aby uzyskać więcej informacji na temat <xref:System.Data.Linq.DataContext> , zobacz klasy [metodę DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Tworzenie klas jednostek mapowane na bazę danych, tabele i widoki  
 Możesz tworzyć klasy jednostki zamapowane do tabel i widoków przeciągając tabele i widoki z **Eksploratora serwera**/**Eksploratora bazy danych** na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Jak wskazano w poprzedniej sekcji <xref:System.Data.Linq.DataContext> jest skonfigurowana z informacjami dotyczącymi połączenia udostępniane przez pierwszy element zostanie przeciągnięty na powierzchnię projektu. Jeśli kolejne elementu, który używa innego połączenia jest dodawany do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], można zmienić połączenia dla <xref:System.Data.Linq.DataContext>. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie klasy LINQ do SQL zamapowane do tabel i widoków (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Tworzenie DataContext metod, które mogą wywoływać procedury składowane i funkcje  
 Można utworzyć <xref:System.Data.Linq.DataContext> metod, które wywołują (są mapowane na) procedury składowane i funkcje, przeciągając je z **Eksploratora serwera**/**Eksploratora bazy danych** na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Procedury składowane i funkcje zostaną dodane do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] jako metody <xref:System.Data.Linq.DataContext>.  
  
> [!NOTE]
>  Przeciągnięcie procedury składowane i funkcje z **Eksploratora serwera**/**Eksploratora bazy danych** na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], zwracany typ wygenerowany <xref:System.Data.Linq.DataContext> różni się — metoda w zależności od tego, gdzie można usunąć elementu. Aby uzyskać więcej informacji, zobacz [metodę DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurowanie DataContext zapisują dane pomiędzy klasami jednostki i w bazie danych przy użyciu procedur składowanych  
 Jak wspomniano wcześniej, można utworzyć <xref:System.Data.Linq.DataContext> metod, które mogą wywoływać procedury składowane i funkcje. Ponadto można także przypisać procedur składowanych, które mogą być używane dla domyślnej [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] zachowania w czasie wykonywania, który wykonuje wstawiania, aktualizacji i usuwa. Aby uzyskać więcej informacji, zobacz [porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="inheritance-and-the-or-designer"></a>Projektant obiektów relacyjnych i dziedziczenie  
 Inne obiekty, takich jak [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy można użyć dziedziczenia i pochodzić z innych klas. W bazie danych relacji dziedziczenia są tworzone na kilka sposobów. [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Obsługuje koncepcja dziedziczenia pojedynczej tabeli, jak często jest zaimplementowana w systemach relacyjnych. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie dziedziczenia za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).  
  
## <a name="linq-to-sql-queries"></a>LINQ do SQL zapytań  
 Klasy jednostki tworzone przez [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] są przeznaczone do użytku z [LINQ (zapytania język Language-Integrated)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d). Aby uzyskać więcej informacji, zobacz [porady: Kwerenda dotycząca informacji](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Oddzielanie wygenerowany element DataContext i kod klasy jednostki w różnych przestrzeniach nazw  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Zapewnia **Namespace kontekstu** i **Namespace jednostki** właściwości <xref:System.Data.Linq.DataContext>. Te właściwości określają, jakie przestrzeni nazw <xref:System.Data.Linq.DataContext> i do zostaje wygenerowany kod klasy jednostki. Domyślnie te właściwości są puste i <xref:System.Data.Linq.DataContext> i klas jednostek są generowane w przestrzeni nazw aplikacji. Aby wygenerować kod w przestrzeni nazw innych niż przestrzeń nazw aplikacji, wprowadź wartość do **Namespace kontekstu** i/lub **Namespace jednostki** właściwości.
  
## <a name="reference-content"></a>Odwołanie do zawartości
<xref:System.Linq>  
<xref:System.Data.Linq>  
  
## <a name="see-also"></a>Zobacz także
[LINQ do SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)    
[Często zadawane pytania (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions) 