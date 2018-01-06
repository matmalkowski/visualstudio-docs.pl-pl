---
title: "Porady: programowane stosowanie stylów do zakresów arkusza w skoroszycie | Dokumentacja firmy Microsoft"
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
- ranges, styles
- styles, workbook ranges
- workbooks, styles
ms.assetid: c7e781ed-f366-45bb-aeb6-69c10d19d842
caps.latest.revision: "51"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f2700b7a8a2a07c77bfbd6961443fdf57cd3cc07
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Porady: Programowane stosowanie stylów do zakresów arkusza w skoroszycie
  Style o nazwie można stosować do regionów w skoroszycie. Excel udostępnia wiele wstępnie zdefiniowanych stylów.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 **Formatowanie komórek** okno dialogowe wyświetla wszystkie opcje można użyć do formatowania komórek i każdej z tych opcji jest dostępny z poziomu kodu. Aby wyświetlić to okno dialogowe w programie Excel, kliknij przycisk **komórek** na **Format** menu.  
  
### <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Aby zastosować styl nazwanym zakresem w dostosowaniu poziomie dokumentu  
  
1.  Tworzenie nowego stylu i ustaw jego atrybuty.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#53)]  
  
2.  Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolować, przypisać tekstu, a następnie Zastosuj nowy styl. Ten kod muszą znajdować się w klasie arkusza nie znajduje się w `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#54)]  
  
### <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Aby wyczyścić stylu z nazwanego zakresu w dostosowaniu poziomie dokumentu  
  
1.  Styl normalny do zakresu. Ten kod muszą znajdować się w klasie arkusza nie znajduje się w `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#55)]  
  
### <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Aby zastosować styl nazwanym zakresem w dodatku VSTO  
  
1.  Tworzenie nowego stylu i ustaw jego atrybuty.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#28)]  
  
2.  Utwórz <xref:Microsoft.Office.Interop.Excel.Range>, przypisać tekstu, a następnie Zastosuj nowy styl.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#29)]  
  
### <a name="to-clear-a-style-from-a-named-range-in-an-vsto-add-in"></a>Aby wyczyścić stylu z nazwanego zakresu w dodatku VSTO  
  
1.  Styl normalny do zakresu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#56)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z zakresami](../vsto/working-with-ranges.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  