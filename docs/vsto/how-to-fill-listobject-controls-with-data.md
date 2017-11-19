---
title: "Porady: wypełnianie formantów ListObject danymi | Dokumentacja firmy Microsoft"
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
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
ms.assetid: bf692c77-f5cc-456a-9a5c-84ed3067d7eb
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 01103645dcf26cb3a2e227142b722b24fc291c91
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-fill-listobject-controls-with-data"></a>Porady: wypełnianie formantów ListObject danymi
  Powiązanie danych można użyć jako sposób, aby szybko dodać dane do dokumentu. Po powiązaniu danych na obiekt listy, możesz odłączyć obiekt listy są wyświetlane dane, ale nie jest już powiązany ze źródłem danych.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak: utworzyć listy w programie Excel, który jest połączony z listy programu SharePoint?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
### <a name="to-bind-data-to-a-listobject-control"></a>Wiązanie danych do formantu ListObject  
  
1.  Utwórz <xref:System.Data.DataTable> na poziomie klasy.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]  
  
2.  Dodawanie kolumn próbki i dane w `Startup` obsługi zdarzeń `Sheet1` klasy (w projektach na poziomie dokumentu) lub `ThisAddIn` klasy (w projektach na poziomie aplikacji).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]  
  
3.  Wywołanie <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> — metoda i przekaż nazwy kolumn w kolejności, powinien zostać wyświetlony. Kolejność kolumn w obiekcie listy może się różnić od kolejności, w jakiej występują w <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]  
  
### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>Aby odłączyć ListObject — formant ze źródła danych  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> metody `List1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład kodu zakłada masz istniejącą <xref:Microsoft.Office.Tools.Excel.ListObject> o nazwie `list1` w arkuszu, w której znajduje się ten kod.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Porady: mapowanie kolumn ListObject do danych](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject — formant](../vsto/listobject-control.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Porady: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Porady: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  