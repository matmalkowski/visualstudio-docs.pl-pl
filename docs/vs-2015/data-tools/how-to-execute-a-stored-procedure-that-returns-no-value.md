---
title: 'Porady: wykonywanie procedury przechowywanej, która nie zwraca wartości | Dokumentacja firmy Microsoft'
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
- ExecuteNonQuery method
- stored procedures, creating
- stored procedures, executing
ms.assetid: 8a929e96-2cf5-43a5-b5b7-c0a5a397bbc5
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0a9c80f37e5d569fd3a257f678256f01aba44925
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42692401"
---
# <a name="how-to-execute-a-stored-procedure-that-returns-no-value"></a>Porady: wykonywanie procedury przechowywanej, która nie zwraca wartości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wykonać procedury przechowywanej, która nie zwraca żadnej wartości, można uruchomić zapytania TableAdapter, która jest skonfigurowana do uruchamiania procedury składowanej (na przykład `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Jeśli aplikacja nie korzysta z TableAdapters, wywołaj `ExecuteNonQuery` metody na obiekt polecenia, ustawiając jego `CommandType` właściwość <xref:System.Data.CommandType>. ("Obiekt polecenia" odnosi się do określonego polecenia dla [.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) korzysta aplikacja. Adapterem, jeśli aplikacja wykorzystuje .NET Framework Data Provider for SQL Server, obiekt polecenia będzie <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Poniższe przykłady pokazują, jak na wykonanie procedury składowane, które zwracają nie wartości z bazy danych przy użyciu obu elementów TableAdapter lub polecenia obiektów. Aby uzyskać więcej informacji o wysyłaniu zapytań za pomocą poleceń i TableAdapters zobacz [wypełnienia zestawów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-stored-procedures-that-return-no-values-using-a-tableadapter"></a>Wykonywanie procedur składowanych, które nie zwracają żadnych wartości za pomocą adaptera TableAdapter  
 W tym przykładzie pokazano, jak utworzyć za pomocą zapytań TableAdapter [edytowanie TableAdapters](../data-tools/editing-tableadapters.md), a następnie zawiera informacje na temat Zadeklaruj wystąpienie TableAdapter i wykonać zapytanie.  
  
#### <a name="to-create-a-stored-procedure-that-returns-no-value-using-a-tableadapter"></a>Aby utworzyć procedurę składowaną, która nie zwraca wartości za pomocą adaptera TableAdapter  
  
1.  Otwórz zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [porady: otwieranie zestawu w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Jeśli nie masz już jeden, należy utworzyć obiekt TableAdapter. Aby uzyskać więcej informacji na temat tworzenia elementów TableAdapter, zobacz [tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Jeśli masz już zapytanie na Twoje TableAdapter korzystającej z procedury składowanej, która nie zwraca wartości, przejdź do następnej procedury "Aby"deklarować wystąpienia TableAdapter i wykonaj zapytanie. W przeciwnym razie przejdź do kroku 4, aby utworzyć nową kwerendę, która nie zwraca wartości.  
  
4.  Kliknij prawym przyciskiem myszy obiekt TableAdapter, która ma i użyć menu skrótów, aby dodać zapytanie.  
  
     **Kreatora konfiguracji zapytania TableAdapter** zostanie otwarty.  
  
5.  Wybierz **Użyj istniejącą procedurę składowaną**, a następnie kliknij przycisk **dalej**.  
  
6.  Wybierz procedurę składowaną z listy rozwijanej, a następnie kliknij przycisk **dalej**.  
  
7.  Wybierz opcję, aby zwrócić **żadnej wartości**, a następnie kliknij przycisk **dalej**.  
  
8.  Podaj nazwę kwerendy.  
  
9. Kliknij przycisk **dalej**, lub **Zakończ** aby zakończyć działanie kreatora; zapytanie zostanie dodany do TableAdapter.  
  
10. Skompilowanie projektu.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Zadeklaruj wystąpienie TableAdapter i wykonywanie zapytania  
  
1.  Zadeklaruj wystąpienie TableAdapter, który zawiera zapytanie, które chcesz wykonać.  
  
    -   Aby utworzyć wystąpienia usługi przy użyciu narzędzi czasu projektowania, przeciągnij TableAdapter z **przybornika**. (Składniki w twoim projekcie są teraz wyświetlane w **przybornika** pod nagłówkiem, który odpowiada nazwa projektu.) Jeśli nie ma elementu TableAdapter **przybornika**, a następnie może być konieczne skompilowanie projektu.  
  
         —lub—  
  
    -   Aby utworzyć wystąpienie w kodzie, Zastąp następujący kod, za pomocą nazwy swojej <xref:System.Data.DataSet> i TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapter nie faktycznie znajdują się wewnątrz klasy ich skojarzonego zestawu danych. Każdy zestaw danych zawiera odpowiednią kolekcję elementów TableAdapter w jego własnej przestrzeni nazw. Na przykład, jeśli masz zestaw danych o nazwie `SalesDataSet`, a następnie będzie istnieć `SalesDataSetTableAdapters` przestrzeń nazw zawierająca jego adapterów TableAdapter.  
  
2.  Zapytania należy wywołać, jak każda inna metoda wywoływałby w kodzie. Zapytanie jest metoda w metodzie TableAdapter. Zastąp następujący kod nazwy TableAdapter i zapytania. Należy również podawać żadnych parametrów wymaganych przez zapytanie. Jeśli nie masz pewności, jeśli zapytanie wymaga parametrów, lub parametry wymaga, a następnie wyszukaj IntelliSense wymagany podpis zapytania. W zależności od tego, czy zapytanie pobiera parametry, czy nie kod powinien wyglądać podobny do jednego z poniższych przykładów:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Kompletny kod, Zadeklaruj wystąpienie TableAdapter i wykonaj zapytanie powinien wyglądać podobnie do następującego:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-stored-procedures-that-return-no-value-using-a-command-object"></a>Wykonywanie procedury składowane, które zwracają nie wartości za pomocą obiektu polecenia  
 Poniższy przykład pokazuje, jak utworzyć polecenie i wykonaj procedurę składowaną, która nie zwraca wartości. Aby uzyskać informacji na temat ustawiania i pobierania wartości parametrów dla polecenia, zobacz [porady: zestaw i pobieranie parametrów dla obiektów poleceń](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 W tym przykładzie użyto <xref:System.Data.SqlClient.SqlCommand> obiektu i wymaga:  
  
-   Odwołuje się do <xref:System>, <xref:System.Data>, i <xref:System.Xml> przestrzeni nazw.  
  
#### <a name="to-execute-a-stored-procedure-that-returns-no-value-using-a-datacommand"></a>Aby wykonać procedurę składowaną, która nie zwraca wartości przy użyciu Voteonreviewactivity  
  
-   Dodaj następujący kod do metody, którą chcesz wykonać procedurę składowaną z. Wywołaj `ExecuteNonQuery` metoda polecenie, aby zwracać żadnej wartości (na przykład <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#15)]
     [!code-vb[VbRaddataFillingAndExecuting#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#15)]  
  
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