---
title: 'Porady: mapowanie kolumn ListObject do danych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 370f82c6a167a9747a3a41ac3720bc4f679fb8d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-map-listobject-columns-to-data"></a>Porady: mapowanie kolumn ListObject do danych
  Po powiązaniu <xref:Microsoft.Office.Tools.Excel.ListObject> formant <xref:System.Data.DataTable>, możesz nie chcieć wyświetlanie wszystkich kolumn na liście, mogą też niektóre kolumny, które nie są powiązane z danymi. Można zamapować kolumny, które mają być wyświetlane w <xref:Microsoft.Office.Tools.Excel.ListObject> podczas wywoływania <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metody.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak: utworzyć listy w programie Excel, który jest połączony z listy programu SharePoint?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## <a name="mapping-columns"></a>Mapowanie kolumn  
  
#### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Aby mapować tabelę danych do kolumn na liście  
  
1.  Utwórz <xref:System.Data.DataTable> na poziomie klasy.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]  
  
2.  Dodawanie kolumn próbki i dane w `Startup` obsługi zdarzeń `Sheet1` klasy (w projektach na poziomie dokumentu) lub `ThisAddIn` klasy (w projekcie dodatku narzędzi VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]  
  
3.  Wywołanie <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> — metoda i przekaż nazwy kolumn w kolejności, powinien zostać wyświetlony. Obiekt listy będą powiązane nowo utworzonego <xref:System.Data.DataTable>, ale kolejności kolumn w obiekcie listy będą się różnić od kolejności ich występowania w <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]  
  
## <a name="specifying-unmapped-columns"></a>Określanie Niemapowane kolumn  
 Podczas mapowania kolumn <xref:System.Data.DataTable>, można również określić, że przekazywanie pustego ciągu nie należy do danych powiązany niektóre kolumny. Nowej kolumny, która nie jest powiązany z danymi jest dodawane do <xref:Microsoft.Office.Tools.Excel.ListObject> formantu.  
  
#### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Aby określić Niemapowane kolumny, gdy mapowanie kolumn ListObject  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> — metoda i przekaż nazwy kolumn w kolejności, powinien zostać wyświetlony. Użyj pustego ciągu, aby wskazać, gdzie jest dodawana kolumna Niemapowane; w takim przypadku między kolumnę tytułu, a ostatnia nazwa.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład kodu zakłada masz istniejącą <xref:Microsoft.Office.Tools.Excel.ListObject> o nazwie `list1` w arkuszu, w której znajduje się ten kod.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Porady: wypełnianie formantów ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject, kontrolka](../vsto/listobject-control.md)  
  
  