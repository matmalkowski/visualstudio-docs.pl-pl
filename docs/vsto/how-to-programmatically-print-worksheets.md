---
title: 'Porady: programowane Drukowanie arkuszy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d9bd4d28afb1eca2ff07a8847081864c7af5744
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  