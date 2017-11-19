---
title: "Wskazówki: Złożone powiązanie danych w VSTO dodatku projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
ms.assetid: ff52fb56-1f67-4ae2-a3d1-93038619d4e6
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9b106e9d1ef1fc10c5c0cd99ceaed76f87408713
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Wskazówki: Złożone danych powiązania w projekcie dodatku narzędzi VSTO
  Dane można powiązać z formanty hosta i formantów formularzy systemu Windows w projektów dodatku VSTO. W tym przewodniku pokazano, jak dodawanie formantów do arkusza programu Microsoft Office Excel i powiązanie kontrolek z danymi w czasie wykonywania.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie <xref:Microsoft.Office.Tools.Excel.ListObject> formantu do arkusza w czasie wykonywania.  
  
-   Tworzenie <xref:System.Windows.Forms.BindingSource> łączące formantu do wystąpienia zestawu danych.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)]lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Dostęp do działającego wystąpienia programu SQL Server 2005 lub SQL Server 2005 Express, która ma `AdventureWorksLT` przykładową bazę danych do niego dołączony. Możesz pobrać `AdventureWorksLT` bazy danych z [witryny sieci Web w witrynie CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Aby uzyskać więcej informacji na temat dołączania bazy danych zobacz następujące tematy:  
  
    -   Aby dołączyć bazę danych przy użyciu programu SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [porady: dołączanie bazy danych (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Aby dołączyć bazę danych przy użyciu wiersza polecenia, zobacz [porady: dołączanie pliku bazy danych do programu SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-new-project"></a>Tworzenie nowego projektu  
 Pierwszym krokiem jest do tworzenia projektów dodatku VSTO programu Excel.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektów dodatku VSTO programu Excel o nazwie **zapełnianie arkuszy z bazy danych**, za pomocą Visual Basic lub C#.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otworzy `ThisAddIn.vb` lub `ThisAddIn.cs` plików i dodaje **zapełnianie arkuszy z bazy danych** projektu do **Eksploratora rozwiązań**.  
  
## <a name="creating-a-data-source"></a>Tworzenie źródła danych  
 Użyj **źródeł danych** okno, aby dodać typizowanego zestaw danych do projektu.  
  
#### <a name="to-add-a-typed-dataset-to-the-project"></a>Aby dodać typizowanego zestaw danych do projektu  
  
1.  Jeśli **źródeł danych** okna nie jest widoczne, wyświetl ją, z menu, wybierając **widoku**, **inne okna**, **źródeł danych**.  
  
2.  Wybierz **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
3.  Kliknij przycisk **bazy danych**, a następnie kliknij przycisk **dalej**.  
  
4.  Jeśli masz istniejące połączenie z `AdventureWorksLT` bazy danych, wybierz to połączenie i kliknij przycisk **dalej**.  
  
     W przeciwnym razie kliknij przycisk **nowe połączenie**i użyj **Dodawanie połączenia** okno dialogowe, aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
5.  W **zapisać parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.  
  
6.  W **wybierz obiekty bazy danych użytkownika** rozwiń pozycję **tabel** i wybierz **adresu (SalesLT)**.  
  
7.  Kliknij przycisk **Zakończ**.  
  
     Plik AdventureWorksLTDataSet.xsd jest dodawany do **Eksploratora rozwiązań**. Ten plik definiuje następujące elementy:  
  
    -   Typizowanego zestaw danych o nazwie `AdventureWorksLTDataSet`. Ten zestaw danych reprezentuje zawartość **adresu (SalesLT)** tabeli w bazie danych AdventureWorksLT.  
  
    -   TableAdapter o nazwie `AddressTableAdapter`. Ten obiekt TableAdapter może służyć do odczytywania i zapisywania danych `AdventureWorksLTDataSet`. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Użyje obu tych obiektów w dalszej części tego przewodnika.  
  
## <a name="creating-controls-and-binding-controls-to-data"></a>Tworzenie formantów i powiązywanie kontrolek z danymi  
 W ramach tego przewodnika <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli Wyświetla wszystkie dane w tabeli zaznaczonej zaraz po otwarciu skoroszytu. Obiekt listy używa <xref:System.Windows.Forms.BindingSource> do połączenia z bazą danych formantu.  
  
 Aby uzyskać więcej informacji na temat powiązanie kontrolek z danymi, zobacz [powiązania danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Aby dodać obiekt listy, zestawu danych i tabeli karty  
  
1.  W `ThisAddIn` klasy, deklaruje następującego formantów na wyświetlanie `Address` spis `AdventureWorksLTDataSet` zestawu danych.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]  
  
2.  W `ThisAddIn_Startup` metody, Dodaj następujący kod do zainicjowania zestawu danych i wypełnić dataset z informacjami z `AdventureWorksLTDataSet` zestawu danych.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]  
  
3.  Dodaj następujący kod do `ThisAddIn_Startup` metody. Generuje element hosta, rozszerzający arkusza. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]  
  
4.  Utwórz zakres i Dodaj <xref:Microsoft.Office.Tools.Excel.ListObject> formantu.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]  
  
5.  Obiekt listy, aby powiązać `AdventureWorksLTDataSet` przy użyciu <xref:System.Windows.Forms.BindingSource>. Podaj nazwy kolumny, które chcesz powiązać z obiektem listy.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]  
  
## <a name="testing-the-add-in"></a>Testowanie dodatku  
 Po uruchomieniu programu Excel, <xref:Microsoft.Office.Tools.Excel.ListObject> kontrola wyświetla dane z `Address` spis `AdventureWorksLTDataSet` zestawu danych.  
  
#### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO  
  
-   Naciśnij klawisz **F5**.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie `addressListObject` jest tworzony w arkuszu. Jednocześnie, obiekt zestawu danych o nazwie `adventureWorksLTDataSet` i <xref:System.Windows.Forms.BindingSource> o nazwie `addressBindingSource` zostaną dodane do projektu. <xref:Microsoft.Office.Tools.Excel.ListObject> Jest powiązany z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana z obiektem zestawu danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Porady: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Porady: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Porady: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Porady: przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Porady: aktualizowanie źródła danych danymi z formanty hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Wskazówki: Proste powiązanie danych w projektach na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [Wskazówki: Złożone powiązanie danych w projektach na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [Korzystanie z plików lokalnej bazy danych w rozwiązań Office ― omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources)   
 [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Korzystanie z plików lokalnej bazy danych w rozwiązań Office ― omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Łączenie z danymi w aplikacjach formularzy systemu Windows](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Informacje o składniku BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  