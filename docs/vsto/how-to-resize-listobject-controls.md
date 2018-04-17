---
title: 'Porady: zmiana rozmiaru formantów ListObject | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 12a81e6bb4a0484b79ad42b8fbab77db97ea82c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-resize-listobject-controls"></a>Porady: zmiana rozmiaru formantów ListObject
  Ustawianie rozmiaru <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolować po dodaniu go do programu Microsoft Office Excel; jednak warto zmienić w późniejszym czasie. Na przykład można zmienić listy dwie kolumny na trzy kolumny.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Możesz zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> formantów w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu. Możesz zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> formantów w czasie wykonywania w projekcie dodatku VSTO.  
  
 W tym temacie opisano następujące zadania:  
  
-   [Zmiana rozmiaru formantów ListObject w czasie projektowania](#designtime)  
  
-   [Zmiana rozmiaru formantów ListObject w czasie wykonywania w projektach na poziomie dokumentu](#runtimedoclevel)  
  
-   [Zmiana rozmiaru formantów ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
 Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.ListObject> formantów, zobacz [ListObject — formant](../vsto/listobject-control.md).  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: Dodawanie kolumn do obiektów powiązanych z danymi listy w czasie wykonywania?](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> Zmiana rozmiaru formantu ListObject w czasie projektowania  
 Aby zmienić rozmiar listy, kliknij i przeciągnij uchwyt zmiany rozmiaru lub ponownie zdefiniować jego rozmiaru w **Zmień rozmiar listy** okno dialogowe.  
  
#### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Aby zmienić rozmiar listy przy użyciu okna dialogowego Zmiana rozmiaru listy  
  
  
1.  Kliknij w dowolnym miejscu <xref:Microsoft.Office.Tools.Excel.ListObject> tabeli. **Narzędzia tabel, projektowanie** zostanie wyświetlona karta na Wstążce.  
  
2.  W sekcji właściwości kliknij **rozmiar tabeli**.  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  Wybierz nowy zakres danych dla tej tabeli.  
  
4.  Kliknij przycisk **OK**.  
  
##  <a name="runtimedoclevel"></a> Zmiana rozmiaru formantu ListObject w czasie wykonywania w projektach na poziomie dokumentu  
 Możesz zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> formantu w czasie wykonywania za pomocą <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> metody. Nie można użyć tej metody, aby przenieść <xref:Microsoft.Office.Tools.Excel.ListObject> formant do nowej lokalizacji w arkuszu. Nagłówki muszą znajdować się w tym samym wierszu, a po zmianie rozmiaru <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli musi nakładają się na oryginalnym obiekt listy. Po zmianie rozmiaru <xref:Microsoft.Office.Tools.Excel.ListObject> formant musi zawierać wiersz nagłówka i co najmniej jeden wiersz danych.  
  
#### <a name="to-resize-a-list-object-programmatically"></a>Aby zmienić rozmiar obiektu listy programowo  
  
1.  Utwórz <xref:Microsoft.Office.Tools.Excel.ListObject> formant, który obejmuje komórki **A1** za pośrednictwem **B3** na `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  Zmień rozmiar listy na komórki **A1** za pośrednictwem **C5**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> Zmiana rozmiaru ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Możesz zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.ListObject> sterowania wszystkie otwarte arkusza w czasie wykonywania. Aby uzyskać więcej informacji o sposobie dodawania <xref:Microsoft.Office.Tools.Excel.ListObject> sterowania do arkusza za pomocą dodatku VSTO, zobacz [porady: dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
#### <a name="to-resize-a-list-object-programmatically"></a>Aby zmienić rozmiar obiektu listy programowo  
  
1.  Utwórz <xref:Microsoft.Office.Tools.Excel.ListObject> formant, który obejmuje komórki **A1** za pośrednictwem **B3** na `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]  
  
2.  Zmień rozmiar listy na komórki **A1** za pośrednictwem **C5**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject — formant](../vsto/listobject-control.md)   
 [Porady: dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Porady: zmiana rozmiaru formantów zakładki](../vsto/how-to-resize-bookmark-controls.md)   
 [Instrukcje: Zmiana rozmiaru kontrolek NamedRange](../vsto/how-to-resize-namedrange-controls.md)  
  
  