---
title: 'Porady: programowane Dodawanie i usuwanie komentarzy do arkusza | Dokumentacja firmy Microsoft'
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
- ranges, comments
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9351dd018c2db4832db20a4abbdaa050f060793e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Porady: Programowane dodawanie i usuwanie komentarzy do arkusza
  Można programowo Dodawanie i usuwanie komentarzy w arkuszach programu Microsoft Office Excel. Komentarze można dodawać tylko do pojedynczego komórek, aby nie zakresów wielu komórek.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="adding-and-deleting-a-comment-in-a-document-level-project"></a>Dodawanie i usuwanie komentarza w projektach na poziomie dokumentu  
 Poniższe przykłady założono, że istnieje pojedynczych komórek <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `dateComment` w arkuszu o nazwie `Sheet1`.  
  
#### <a name="to-add-a-new-comment-to-a-named-range"></a>Aby dodać nowy komentarz do nazwanego zakresu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> metody <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli i Podaj tekst komentarza. Ten kod należy umieścić w `Sheet1` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>Aby usunąć komentarz z nazwanego zakresu  
  
1.  Sprawdź, czy komentarz istnieje zakresu i usuń go. Ten kod należy umieścić w `Sheet1` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="adding-and-deleting-a-comment-in-an-vsto-add-in-project"></a>Dodawanie i usuwanie komentarza w projekcie dodatku narzędzi VSTO  
 Poniższe przykłady założono, że istnieje pojedynczych komórek <xref:Microsoft.Office.Interop.Excel.Range> o nazwie `dateComment` w aktywnym arkuszu.  
  
#### <a name="to-add-a-new-comment-to-an-excel-range"></a>Aby dodać nowy komentarz do zakresu programu Excel  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> metody <xref:Microsoft.Office.Interop.Excel.Range> i Podaj tekst komentarza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
#### <a name="to-delete-a-comment-from-an-excel-range"></a>Aby usunąć komentarz z zakresu programu Excel  
  
1.  Sprawdź, czy komentarz istnieje zakresu i usuń go.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Porady: programowane wyświetlanie komentarzy do arkusza](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange, kontrolka](../vsto/namedrange-control.md)  
  
  