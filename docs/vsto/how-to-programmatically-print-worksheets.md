---
title: 'Porady: programowane Drukowanie arkuszy | Dokumentacja firmy Microsoft'
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
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
ms.assetid: 312bfcd7-0a74-421c-b42e-df71a06b7bdf
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 030580d2db7490a7ce806cca86477659a0b00267
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-print-worksheets"></a>Porady: Programowane drukowanie arkuszy
  Można drukować żadnych arkusza w skoroszycie.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="printing-a-worksheet-in-a-document-level-customization"></a>Drukowanie do arkusza w dostosowaniu poziomie dokumentu  
  
#### <a name="to-print-a-worksheet"></a>Aby wydrukować arkusza  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> metody `Sheet1`żądania dwie kopie i wyświetlić podgląd przed wydrukowaniem dokumentu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]  
  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> Metoda pozwala na wyświetlanie określony obiekt w **Podgląd wydruku** okna. Poniższy kod zakłada masz <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta o nazwie `Sheet1`.  
  
#### <a name="to-preview-a-page-before-printing"></a>Aby wyświetlić podgląd strony przed wydrukowaniem  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> metody arkusza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]  
  
## <a name="printing-a-worksheet-in-a-vsto-add-in"></a>Drukowanie do arkusza w dodatku narzędzi VSTO  
  
#### <a name="to-print-a-worksheet"></a>Aby wydrukować arkusza  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> metody aktywnego arkusza żądania dwie kopie i wyświetlić podgląd przed wydrukowaniem dokumentu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]  
  
 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> Metoda pozwala na wyświetlanie określony obiekt w **Podgląd wydruku** okna.  
  
#### <a name="to-preview-a-page-before-printing"></a>Aby wyświetlić podgląd strony przed wydrukowaniem  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metody aktywnego arkusza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Porady: programowane sprawdzanie pisowni w arkuszach](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Element hosta arkusza](../vsto/worksheet-host-item.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  