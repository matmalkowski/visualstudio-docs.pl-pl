---
title: 'Porady: tworzenie i wykonywanie instrukcji SQL, która zwraca pojedynczą wartość | Dokumentacja firmy Microsoft'
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
- data reader
- scalar values
- stored procedures, returning single value
- SQL statements, data commands
- DataReader object
- data commands, returning scalar values
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 762cf33bb739e4cf99e7b45d59b91df9e1a869c7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679112"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-a-single-value"></a>Porady: tworzenie i wykonywanie instrukcji SQL zwracających pojedynczą wartość
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wykonać instrukcję SQL, która zwraca pojedynczą wartość, można uruchomić zapytania TableAdapter, który jest skonfigurowany do uruchomienia instrukcji SQL (na przykład `CustomersTableAdapter.CustomerCount()`).  
  
 Jeśli aplikacja nie korzysta z TableAdapters, wywołaj `ExecuteScalar` metody na obiekt polecenia, ustawiając jego `CommandType` właściwość <xref:System.Data.CommandType>. ("Obiekt polecenia" odnosi się do określonego polecenia dla [.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) korzysta aplikacja. Adapterem, jeśli aplikacja korzysta z dostawcy danych .NET Framework dla programu SQL Server, obiekt polecenia będzie <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Następujące przykłady przedstawiają sposób wykonania instrukcji SQL, które zwracają pojedyncze wartości z bazy danych przy użyciu obu elementów TableAdapter lub polecenia obiektów. Aby uzyskać więcej informacji o wysyłaniu zapytań za pomocą poleceń i TableAdapters zobacz [wypełnienia zestawów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-tableadapter"></a>Wykonywanie instrukcji SQL, które zwracają wartości pojedynczej, za pomocą adaptera TableAdapter  
 W tym przykładzie pokazano, jak utworzyć za pomocą zapytań TableAdapter [edytowanie TableAdapters](../data-tools/editing-tableadapters.md), a następnie zawiera informacje na temat Zadeklaruj wystąpienie TableAdapter i wykonać zapytanie.  
  
#### <a name="to-create-an-sql-statement-returning-a-single-value-using-a-tableadapter"></a>Do tworzenia instrukcji SQL, zwracanie wartości pojedynczej za pomocą adaptera TableAdapter  
  
1.  Otwórz zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [porady: otwieranie zestawu w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Jeśli nie masz już jeden, należy utworzyć obiekt TableAdapter. Aby uzyskać więcej informacji na temat tworzenia elementów TableAdapter, zobacz [tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Jeśli masz już zapytanie na Twoje TableAdapter, która używa instrukcji SQL, aby zwracać pojedynczą wartość, następnie przejdź do następnej procedury "Aby"deklarować wystąpienia TableAdapter i wykonaj zapytanie. W przeciwnym razie przejdź do kroku 4, aby utworzyć nowe zapytanie, które zwraca pojedynczą wartość.  
  
4.  Kliknij prawym przyciskiem myszy obiekt TableAdapter, która ma i użyć menu skrótów, aby dodać zapytanie.  
  
     **Kreatora konfiguracji zapytania TableAdapter** zostanie otwarty.  
  
5.  Pozostaw wartość domyślną **użyj instrukcji SQL**, a następnie kliknij przycisk **dalej**.  
  
6.  Wybierz **SELECT, która zwraca pojedynczą wartość** opcji, a następnie kliknij przycisk **dalej**.  
  
7.  Wpisz instrukcję SQL lub użyj **konstruktora zapytań** pomocne w tworzeniu, a następnie kliknij przycisk **dalej**.  
  
8.  Podaj nazwę kwerendy.  
  
9. Ukończ pracę kreatora; Zapytanie jest dodawany do TableAdapter.  
  
10. Skompilowanie projektu.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Zadeklaruj wystąpienie TableAdapter i wykonywanie zapytania  
  
1.  Zadeklaruj wystąpienie TableAdapter, która zawiera kwerendę, którą chcesz wykonać.  
  
    -   Aby utworzyć wystąpienia usługi przy użyciu narzędzi czasu projektowania, przeciągnij TableAdapter z **przybornika**. (Składniki w twoim projekcie są teraz wyświetlane w **przybornika** pod nagłówkiem, który odpowiada nazwa projektu.) Jeśli nie ma elementu TableAdapter **przybornika**, a następnie może być konieczne skompilowanie projektu.  
  
         —lub—  
  
    -   Aby utworzyć wystąpienie w kodzie, Zastąp następujący kod, za pomocą nazwy swojej <xref:System.Data.DataSet> i TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapter nie faktycznie znajdują się wewnątrz klasy ich skojarzonego zestawu danych. Każdy zestaw danych zawiera odpowiednią kolekcję elementów TableAdapter w jego własnej przestrzeni nazw. Na przykład, jeśli masz zestaw danych o nazwie `SalesDataSet`, a następnie będzie istnieć `SalesDataSetTableAdapters` przestrzeń nazw zawierająca jego adapterów TableAdapter.  
  
2.  Zapytania należy wywołać, jak każda inna metoda wywoływałby w kodzie. Zapytanie jest metoda w metodzie TableAdapter. Zastąp następujący kod nazwy TableAdapter i zapytania. Należy również podawać żadnych parametrów wymaganych przez zapytanie oraz zrobić coś z wartością zwracaną (na przykład przypisać ją do zmiennej). Jeśli nie masz pewności, jeśli zapytanie wymaga parametrów, lub parametry wymaga, a następnie wyszukaj IntelliSense wymagany podpis zapytania. W zależności od tego, czy zapytanie pobiera parametry, czy nie kod powinien wyglądać podobny do jednego z poniższych przykładów:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  Prawdopodobnie konieczne będzie przypisanie wartości zwracane przez zapytanie do zmiennej. Zwracany typ danych na podstawie kwerendy, zapytań TableAdapter, które zwraca pojedynczą wartość (w przeciwieństwie do `ExecuteScalar` metody, która zwraca obiekt). Na przykład jeśli zapytanie TableAdapter wybierze jednokolumnową, którego typem danych jest liczba całkowita, wartość zwracana przez zapytanie jest liczbą całkowitą. Jeśli kolumna dopuszcza wartości null, wartość zwracana jest jednym z typów dopuszczających wartości zerowe (na przykład `Nullable(Of Integer)`). Aby uzyskać więcej informacji na temat typów dopuszczających wartość null, zobacz <xref:System.Nullable>. Kompletny kod, Zadeklaruj wystąpienie TableAdapter i wykonywanie zapytania, powinny wyglądać podobnie do następujących (w tym przykładzie przyjęto założenie, zwracana wartość jest liczbą całkowitą; Dostosuj swój kod, zgodnie z typem danych zwróconych przez zapytanie):  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-command-object"></a>Wykonywanie instrukcji SQL, które zwracają wartości pojedynczej przy użyciu obiektu polecenia  
 Poniższy przykład pokazuje, jak utworzyć polecenie i wykonaj instrukcję SQL, która zwraca pojedynczą wartość. Aby uzyskać informacji na temat ustawiania i pobierania wartości parametrów dla polecenia, zobacz [porady: zestaw i pobieranie parametrów dla obiektów poleceń](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 W tym przykładzie użyto <xref:System.Data.SqlClient.SqlCommand> obiektu i wymaga:  
  
-   Odwołuje się do <xref:System>, <xref:System.Data>, i <xref:System.Xml> przestrzeni nazw.  
  
-   Połączenie danych o nazwie `SqlConnection1`.  
  
-   Tabela o nazwie `Customers` w danych źródłowych `SqlConnection1` łączy się z. (W przeciwnym razie trzeba prawidłową instrukcję SQL dla źródła danych).  
  
#### <a name="to-execute-an-sql-statement-returning-a-single-value-using-a-datacommand"></a>Aby wykonać instrukcję SQL zwraca pojedynczą wartość przy Voteonreviewactivity  
  
-   Dodaj następujący kod do metody, która ma zostać wykonany kod z. Zwraca pojedynczą wartość, wywołując `ExecuteScalar` metoda polecenia (na przykład <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). Dane są zwracane w <xref:System.Object>.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#10)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#10)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aplikacja wymaga uprawnień dostępu do bazy danych i wykonaj instrukcję SQL.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Porady: tworzenie zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Porady: edytowanie zapytań TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Porady: wypełnianie zestawu danych danymi](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Wypełnij zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Porady: Ustawianie i pobieranie parametrów dla obiektów poleceń](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)