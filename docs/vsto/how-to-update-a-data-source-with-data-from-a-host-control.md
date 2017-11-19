---
title: "Porady: aktualizowanie źródła danych danymi z kontrolką hosta | Dokumentacja firmy Microsoft"
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
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1fd4716e81d280e049a8cbd1a5206b52f2714e27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Porady: aktualizowanie źródła danych danymi z kontrolką hosta
  Można powiązać ze źródłem danych formantu hosta i aktualizowanie źródła danych zmiany wprowadzone w danych w formancie. W tym procesie istnieją dwa podstawowe kroki:  
  
1.  Aktualizowanie źródła danych w pamięci modyfikacji danych w formancie. Zazwyczaj jest źródło danych w pamięci <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub inny obiekt danych.  
  
2.  Aktualizują bazę danych w źródle danych w pamięci. Ma to zastosowanie tylko wtedy, gdy źródło danych jest podłączony do wewnętrznej bazy danych, na przykład w bazie danych programu SQL Server lub programu Microsoft Office Access.  
  
 Aby uzyskać więcej informacji na temat kontrolki hosta i powiązania danych, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md) i [powiązania danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="updating-the-in-memory-data-source"></a>Aktualizowanie źródła danych w pamięci  
 Domyślnie formanty hosta, które umożliwiają proste powiązanie danych (na przykład formantów zawartości do dokumentu programu Word lub formant nazwany zakres na arkuszu programu Excel) nie należy zapisywać zmiany danych w źródle danych w pamięci. Oznacza to gdy użytkownik końcowy zmieni wartość w formancie hosta, a następnie przechodzi od formantu, nowa wartość w formancie nie są automatycznie zapisywane w źródle danych.  
  
 Zapisanie danych w źródle danych, można napisać kod, który aktualizuje źródła danych w odpowiedzi na zdarzenia w czasie wykonywania, lub skonfigurować formantu można automatycznie zaktualizować źródła danych, gdy wartość w formancie zostanie zmieniona.  
  
 Nie trzeba zapisać <xref:Microsoft.Office.Tools.Excel.ListObject> zmieni się ze źródłem danych w pamięci. Po powiązaniu <xref:Microsoft.Office.Tools.Excel.ListObject> formantu z danymi, <xref:Microsoft.Office.Tools.Excel.ListObject> formant automatycznie zapisuje zmiany w źródle danych w pamięci bez konieczności dodatkowego kodu.  
  
#### <a name="to-update-the-in-memory-data-source-at-run-time"></a>Aby zaktualizować źródła danych w pamięci w czasie wykonywania  
  
-   Wywołanie <xref:System.Windows.Forms.Binding.WriteValue%2A> metody <xref:System.Windows.Forms.Binding> obiekt, który wiąże formantu ze źródłem danych.  
  
     Poniższy przykład zapisuje zmiany wprowadzone <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu w arkuszu programu Excel do źródła danych. W tym przykładzie założono, że <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `namedRange1` z jego <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości powiązany z polem w źródle danych.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]  
  
### <a name="automatically-updating-the-in-memory-data-source"></a>Automatyczne aktualizowanie źródła danych w pamięci  
 Formant można także skonfigurować, tak aby automatycznie aktualizuje źródła danych w pamięci. W projekcie poziomie dokumentu można to zrobić za pomocą kodu lub projektanta. W projekcie dodatku narzędzi VSTO należy użyć kodu.  
  
##### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Aby ustawić kontrolę można automatycznie zaktualizować źródła danych w pamięci przy użyciu kodu  
  
1.  Użyj trybu System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged <xref:System.Windows.Forms.Binding> obiekt, który wiąże formantu ze źródłem danych. Dostępne są dwie opcje do aktualizowania źródła danych:  
  
    -   Aby zaktualizować źródła danych, gdy formant zostanie zweryfikowany, ustaw tą właściwość na System.Windows.Forms.DataSourceUpdateMode.OnValidation.  
  
    -   Aby zaktualizować źródła danych, gdy wartość właściwości powiązanych z danymi formantu zostanie zmieniona, ustaw tą właściwość na System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged.  
  
        > [!NOTE]  
        >  Opcja System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged nie dotyczą formanty hosta programu Word, ponieważ Word jest nie oferta dokumentu. Zmień lub zmiana sterowania powiadomień. Jednak ta opcja umożliwia formanty formularzy systemu Windows w dokumentach programu Word.  
  
     Poniższy przykład konfiguruje <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu można automatycznie zaktualizować źródła danych, gdy wartość w formancie zostanie zmieniona. W tym przykładzie założono, że <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `namedRange1` z jego <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości powiązany z polem w źródle danych.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]  
  
##### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Aby ustawić kontrolę można automatycznie zaktualizować źródła danych w pamięci przy użyciu narzędzia Projektant  
  
1.  W programie Visual Studio Otwórz dokument programu Word lub skoroszyt programu Excel w projektancie.  
  
2.  Kliknij formant, który ma być automatycznie zaktualizować źródła danych.  
  
3.  W **właściwości** okna, rozwiń węzeł **(DataBindings)** właściwości.  
  
4.  Obok pozycji **(zaawansowane)** właściwości, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton — zrzut ekranu")).  
  
5.  W **formatowanie i zaawansowane powiązanie** okno dialogowe, kliknij przycisk **trybu aktualizacji źródła danych** listy rozwijanej i wybierz jedną z następujących wartości:  
  
    -   Aby zaktualizować źródła danych, gdy formant zostanie zweryfikowany, wybierz **OnValidation**.  
  
    -   Aby zaktualizować źródła danych, gdy wartość właściwości powiązanych z danymi formantu zostanie zmieniona, wybierz **OnPropertyChanged**.  
  
        > [!NOTE]  
        >  **OnPropertyChanged** opcji nie ma zastosowania do kontrolki hosta programu Word, ponieważ Word jest nie oferta dokumentu. Zmień lub zmiana sterowania powiadomień. Jednak ta opcja umożliwia formanty formularzy systemu Windows w dokumentach programu Word.  
  
6.  Zamknij **formatowanie i zaawansowane powiązanie** okno dialogowe.  
  
## <a name="updating-the-database"></a>Uaktualnienie bazy danych  
 Jeśli źródło danych w pamięci jest skojarzona z bazą danych, musisz zaktualizować bazy danych ze zmianami w źródle danych. Aby uzyskać więcej informacji na temat aktualizowania bazy danych, zobacz [zapisać danych w bazie danych](../data-tools/save-data-back-to-the-database.md) i [aktualizowanie danych za pomocą TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .  
  
#### <a name="to-update-the-database"></a>Aby zaktualizować bazę danych  
  
1.  Wywołanie <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody <xref:System.Windows.Forms.BindingSource> dla formantu.  
  
     <xref:System.Windows.Forms.BindingSource> Jest generowany automatycznie podczas dodawania formantu powiązanego z danymi do dokumentu lub skoroszytu w czasie projektowania. <xref:System.Windows.Forms.BindingSource> Łączy formantu typizowanego obiektu dataset w projekcie. Aby uzyskać więcej informacji, zobacz [informacje o składniku BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
     Poniższy przykład kodu zakłada, że projekt zawiera <xref:System.Windows.Forms.BindingSource> o nazwie `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]  
  
2.  Wywołanie `Update` metody TableAdapter wygenerowany w projekcie.  
  
     TableAdapter jest generowany automatycznie podczas dodawania formantu powiązanego z danymi do dokumentu lub skoroszytu w czasie projektowania. TableAdapter łączy typizowanego obiektu dataset w projekcie w bazie danych. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Poniższy przykład kodu zakłada mają połączenie z tabeli Klienci w bazie danych Northwind, i że projekt zawiera TableAdapter o nazwie `customersTableAdapter` i typizowanego zestaw danych o nazwie `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Zapisywanie danych w bazie danych](../data-tools/save-data-back-to-the-database.md)    
 [Aktualizowanie danych za pomocą TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Porady: przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Porady: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Porady: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Porady: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  