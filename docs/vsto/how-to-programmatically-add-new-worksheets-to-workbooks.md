---
title: 'Porady: programowane Dodawanie nowych arkuszy ze skoroszytami | Dokumentacja firmy Microsoft'
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
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 239d4cdba093fa81eea75e1a74906b184e6ba855
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Porady: Programowane dodawanie nowych arkuszy do skoroszytu
  Można programowo utworzyć arkusz, a następnie dodaj arkusz do kolekcji arkuszy w skoroszycie.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Aby dodać nowy arkusz do skoroszytu w dostosowaniu poziomie dokumentu  
  
1.  Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]  
  
     Nowy arkusz jest natywny <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu, a nie element hosta. Jeśli chcesz dodać <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta, należy dodać arkusza w czasie projektowania.  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Aby dodać nowy arkusz do skoroszytu w dodatku VSTO  
  
1.  Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]  
  
     Nowy arkusz jest natywny <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu, a nie element hosta. Można również generować <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta z natywnego <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Porady: programowane usuwanie arkuszy ze skoroszytu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Porady: programowane Zaznaczanie arkuszy](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  