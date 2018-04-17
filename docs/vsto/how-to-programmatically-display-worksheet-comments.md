---
title: 'Porady: programowane wyświetlanie komentarzy do arkusza | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4f7ec00b58358fb51331a40ed246e4205c206323
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Porady: Programowane wyświetlanie komentarzy do arkusza
  Można programowo pokazywać i ukrywać komentarzy w arkuszach programu Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Aby wyświetlić wszystkie komentarze do arkusza w dostosowaniu poziomie dokumentu  
  
1.  Ustaw <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> właściwości **true** Jeśli chcesz wyświetlić komentarze; w przeciwnym razie **false**. Ten kod muszą znajdować się w klasie arkusza nie znajduje się w `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Aby wyświetlić wszystkie komentarze do arkusza w dodatku VSTO poziomie aplikacji  
  
1.  Ustaw <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> właściwości **true** Jeśli chcesz wyświetlić komentarze; w przeciwnym razie **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Porady: programowane Dodawanie i usuwanie komentarzy do arkusza](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Przegląd obiektów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)  
  
  