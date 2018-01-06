---
title: "Porady: zmiana rozmiaru formantów NamedRange | Dokumentacja firmy Microsoft"
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
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
ms.assetid: 7d6f0b2f-be46-49b7-9f38-b4c8849683f7
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3ef581f46dd834a253e32ab169fc7d36c1c1514b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-namedrange-controls"></a>Porady: zmiana rozmiaru formantów NamedRange
  Można ustawić rozmiaru <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolować po dodaniu go do dokumentu programu Microsoft Office Excel; jednak warto zmienić w późniejszym czasie.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Można zmienić rozmiar nazwanego zakresu, w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu. Można również zmienić rozmiar nazwanych zakresów w czasie wykonywania w dodatkach VSTO poziomie aplikacji.  
  
 W tym temacie opisano następujące zadania:  
  
-   [Zmiana rozmiaru formantów NamedRange w czasie projektowania](#designtime)  
  
-   [Zmiana rozmiaru formantów NamedRange w czasie wykonywania w projektach na poziomie dokumentu](#runtimedoclevel)  
  
-   [Zmiana rozmiaru formantów NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
##  <a name="designtime"></a>Zmiana rozmiaru formantów NamedRange w czasie projektowania  
 Zmień rozmiar nazwanego zakresu przez ponowne definiowanie rozmiaru w **Definiowanie nazwy** okno dialogowe.  
  
#### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Aby zmienić rozmiar nazwanego zakresu przy użyciu nazwy zdefiniować okno dialogowe  
  
1.  Kliknij prawym przyciskiem myszy <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu.  
  
2.  Kliknij przycisk **Zarządzaj nazwane zakresy** menu skrótów.  
  
     **Definiowanie nazwy** zostanie wyświetlone okno dialogowe.  
  
3.  Wybierz nazwanego zakresu, który chcesz zmienić.  
  
4.  Wyczyść **odwołuje się do** pola.  
  
5.  Zaznacz komórki, które chcesz użyć do zdefiniowania rozmiaru nazwanego zakresu.  
  
6.  Kliknij przycisk **OK**.  
  
##  <a name="runtimedoclevel"></a>Zmiana rozmiaru formantów NamedRange w czasie wykonywania w projektach na poziomie dokumentu  
 Możesz zmienić rozmiar nazwany zakres programowo przy użyciu <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> właściwości.  
  
> [!NOTE]  
>  W **właściwości** okna, <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> właściwość jest oznaczona jako tylko do odczytu.  
  
#### <a name="to-resize-a-named-range-programmatically"></a>Aby programowo zmienić rozmiar nazwanego zakresu  
  
1.  Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce **A1** z `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]  
  
2.  Zmień rozmiar nazwanego zakresu, aby uwzględnić komórki **B1**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a>Zmiana rozmiaru formantów NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Możesz zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.NamedRange> sterowania wszystkie otwarte arkusza w czasie wykonywania. Aby uzyskać więcej informacji o sposobie dodawania <xref:Microsoft.Office.Tools.Excel.NamedRange> sterowania do arkusza za pomocą dodatku VSTO, zobacz [porady: dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
#### <a name="to-resize-a-named-range-programmatically"></a>Aby programowo zmienić rozmiar nazwanego zakresu  
  
1.  Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce **A1** z `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]  
  
2.  Zmień rozmiar nazwanego zakresu, aby uwzględnić komórki **B1**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Porady: dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Porady: zmiana rozmiaru formantów zakładki](../vsto/how-to-resize-bookmark-controls.md)   
 [Instrukcje: Zmiana rozmiaru kontrolek ListObject](../vsto/how-to-resize-listobject-controls.md)  
  
  