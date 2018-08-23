---
title: 'Porady: tworzenie i wykonywanie instrukcji SQL, która nie zwraca wartości | Dokumentacja firmy Microsoft'
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
- method calls, examples
- calling methods, examples
- SQL statements, executing
- SQL statements, creating
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 2dd78fe0144718337fc589e0d8f8948d5353dd6c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681478"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-no-value"></a>Porady: tworzenie i wykonywanie instrukcji SQL nie zwracających wartości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wykonać instrukcję SQL, która nie zwraca wartości, można uruchomić zapytania TableAdapter, który jest skonfigurowany do uruchomienia instrukcji SQL (na przykład `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Jeśli aplikacja nie korzysta z TableAdapters, wywołaj `ExecuteNonQuery` metody na obiekt polecenia, ustawiając jego `CommandType` właściwość <xref:System.Data.CommandType>. ("Obiekt polecenia" odnosi się do określonego polecenia dla [.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) korzysta aplikacja. Adapterem, jeśli aplikacja korzysta z dostawcy danych .NET Framework dla programu SQL Server, obiekt polecenia będzie <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Następujące przykłady przedstawiają sposób wykonania instrukcji SQL, które zwracają żadnej wartości z bazy danych przy użyciu obu elementów TableAdapter lub polecenia obiektów. Aby uzyskać więcej informacji o wysyłaniu zapytań za pomocą poleceń i TableAdapters zobacz [wypełnienia zestawów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
## <a name="executing-sql-statements-that-return-no-values-using-a-tableadapter"></a>Wykonywanie instrukcji SQL, które nie zwracają żadnych wartości za pomocą adaptera TableAdapter  
 W tym przykładzie pokazano, jak utworzyć za pomocą zapytań TableAdapter [edytowanie TableAdapters](../data-tools/editing-tableadapters.md), a następnie zawiera informacje na temat Zadeklaruj wystąpienie TableAdapter i wykonać zapytanie.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-an-sql-statement-that-returns-no-value-using-a-tableadapter"></a>Do tworzenia instrukcji SQL, która nie zwraca wartości za pomocą adaptera TableAdapter  
  
1.  Otwórz zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [porady: otwieranie zestawu w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Jeśli nie masz już jeden, należy utworzyć obiekt TableAdapter. Aby uzyskać więcej informacji na temat tworzenia elementów TableAdapter, zobacz [tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Jeśli masz już zapytanie na Twoje TableAdapter, która używa instrukcji SQL, która nie zwraca wartości, następnie przejdź do następnej procedury "Aby"deklarować wystąpienia TableAdapter i wykonaj zapytanie. W przeciwnym razie przejdź do kroku 4, aby utworzyć nową kwerendę, która nie zwraca wartości.  
  
4.  Kliknij prawym przyciskiem myszy obiekt TableAdapter, która ma i użyć menu skrótów, aby dodać zapytanie.  
  
     **Kreatora konfiguracji zapytania TableAdapter** zostanie otwarty.  
  
5.  Pozostaw wartość domyślną **użyj instrukcji SQL**, a następnie kliknij przycisk **dalej**.  
  
6.  Wybierz **aktualizacji**, **Wstaw** lub **Usuń** opcji, a następnie kliknij przycisk **dalej**.  
  
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
        >  TableAdapter nie faktycznie znajdują się wewnątrz klasy ich skojarzonego zestawu danych. Każdy zestaw danych zawiera odpowiednią kolekcję elementów TableAdapter w jego własnej przestrzeni nazw. Na przykład, jeśli masz zestaw danych o nazwie `SalesDataSet`, będzie istnieć `SalesDataSetTableAdapters` przestrzeń nazw zawierająca jego adapterów TableAdapter.  
  
2.  Zapytania należy wywołać, jak każda inna metoda wywoływałby w kodzie. Zapytanie jest metoda w metodzie TableAdapter. Zastąp następujący kod nazwy TableAdapter i zapytania. Należy również podawać żadnych parametrów wymaganych przez zapytanie. Jeśli nie masz pewności, jeśli zapytanie wymaga parametrów, lub parametry wymaga, a następnie wyszukaj IntelliSense wymagany podpis zapytania. W zależności od tego, czy zapytanie pobiera parametry, czy nie kod powinien wyglądać podobny do jednego z poniższych przykładów:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Zapytania, które firma Microsoft należy traktować jako niezwracającej wartości, w rzeczywistości zwracają wartość — całkowitą reprezentującą liczbę wierszy dotyczy zapytanie. Kompletny kod, Zadeklaruj wystąpienie TableAdapter i wykonywanie zapytania powinien wyglądać podobnie do następującego:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-sql-statements-that-return-no-value-using-a-command-object"></a>Wykonywanie instrukcji SQL, które zwracają nie wartości za pomocą obiektu polecenia  
 Poniższy przykład pokazuje, jak utworzyć polecenie i wykonaj instrukcję SQL, która nie zwraca wartości. Aby uzyskać informacji na temat ustawiania i pobierania wartości parametrów dla polecenia, zobacz [porady: zestaw i pobieranie parametrów dla obiektów poleceń](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 W tym przykładzie użyto <xref:System.Data.SqlClient.SqlCommand> obiektu i wymaga:  
  
-   Odwołuje się do <xref:System>, <xref:System.Data>, i <xref:System.Xml> przestrzeni nazw.  
  
-   Połączenie danych o nazwie `SqlConnection1`.  
  
-   Tabela o nazwie `Customers` w danych źródłowych `SqlConnection1` łączy się z. (W przeciwnym razie trzeba prawidłową instrukcję SQL dla źródła danych).  
  
#### <a name="to-execute-an-sql-statement-that-returns-no-value-using-a-datacommand"></a>Do wykonania instrukcji SQL, która nie zwraca wartości przy użyciu Voteonreviewactivity  
  
-   Dodaj następujący kod do metody, którą chcesz wykonać instrukcję SQL z. Wywołaj `ExecuteNonQuery` metoda polecenie, aby zwracać żadnej wartości (na przykład <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#12)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#12)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aplikacja wymaga uprawnień dostępu do bazy danych i wykonaj instrukcję SQL.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Porady: tworzenie zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Porady: edytowanie zapytań TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Porady: wypełnianie zestawu danych danymi](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Wypełnij zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Porady: Ustawianie i pobieranie parametrów dla obiektów poleceń](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)