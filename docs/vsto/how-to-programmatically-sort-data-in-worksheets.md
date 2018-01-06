---
title: 'Porady: programowane sortowanie danych w arkuszach | Dokumentacja firmy Microsoft'
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
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b519dad9f2736b7c4451dd01964b3b16cac8ad2d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Porady: programowane sortowanie danych w arkuszach
  Można sortować dane znajdujące się na listach i zakresów arkusza w czasie wykonywania. Poniższy kod sortuje zakres wielokolumnowego o nazwie `Fruits` dane w pierwszej kolumnie, a następnie dane w drugiej kolumnie.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sorting-data-in-a-document-level-customization"></a>Sortowanie danych w dostosowaniu poziomie dokumentu  
  
#### <a name="to-sort-data-in-a-namedrange-control"></a>Aby posortować dane w namedrange — formant  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> metody <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu. Poniższy przykład wymaga <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `Fruits` w arkuszu. Ten kod muszą znajdować się w klasie arkusza nie znajduje się w `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
 Umieść następujący kod w Sheet1.vb lub Sheet1.cs, aby posortować dane w <xref:Microsoft.Office.Tools.Excel.ListObject> formantu. Kod założono, że <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie `fruitList` w arkuszu o nazwie `Sheet1`.  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>Aby posortować dane w ListObject — formant  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metody <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> właściwość <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki hosta.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sorting-data-in-a-vsto-add-in"></a>Sortowanie danych w dodatku narzędzi VSTO  
  
#### <a name="to-sort-data-in-a-native-range"></a>Sortowanie danych w zakresie natywnych  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metody natywnej Excel <xref:Microsoft.Office.Interop.Excel.Range> formantu. Poniższy przykład wymaga macierzystego formantu programu Excel o nazwie `Fruits` w arkuszu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>Aby posortować dane w ListObject — formant  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metody <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> właściwości natywnego programu Excel <xref:Microsoft.Office.Interop.Excel.ListObject> formantu. W poniższym przykładzie założono, że masz natywnego programu Excel <xref:Microsoft.Office.Interop.Excel.ListObject> formantu o nazwie `fruitList` w aktywnym arkuszu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Porady: programowane automatyczne wypełnianie zakresów przyrostowo zmieniającymi się danymi](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Porady: programowane odwoływanie do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Porady: programowane stosowanie stylów do zakresów arkusza w skoroszycie](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [ListObject — formant](../vsto/listobject-control.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  