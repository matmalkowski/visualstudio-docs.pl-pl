---
title: 'Porady: programowane Przywracanie zaznaczenia po wyszukiwaniu | Dokumentacja firmy Microsoft'
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
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: adbc31968b74dd6cb47f06e6feb2cd7d2848f7e7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Porady: Programowane przywracanie zaznaczenia po wyszukiwaniu
  Znajdowanie i zastępowanie tekstu w dokumencie, można przywrócić wybór oryginalnego użytkownika, po ukończeniu wyszukiwania.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Kod w przykładowa procedura wykorzystuje dwa <xref:Microsoft.Office.Interop.Word.Range> obiektów. Przechowuje jedną bieżącą <xref:Microsoft.Office.Interop.Word.Selection>, i jedną ustawia cały dokument ma być używana jako zakres wyszukiwania.  
  
### <a name="to-restore-the-users-original-selection-after-a-search"></a>Aby przywrócić użytkownika oryginalnego zaznaczenia po wyszukiwaniu  
  
1.  Utwórz <xref:Microsoft.Office.Interop.Word.Range> obiektów do dokumentu oraz bieżącego zaznaczenia.  
  
     [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
     [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2.  Wyszukiwanie i Zastąp operacji.  
  
     [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
     [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3.  Wybierz wartość początkową zakresu, aby przywrócić oryginalne określonego przez użytkownika.  
  
     [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
     [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
 W poniższym przykładzie przedstawiono metody ukończenia.  
  
## <a name="example"></a>Przykład  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Porady: programowane Ustawianie opcji wyszukiwania w programie Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Porady: programowane przechodzenie w pętli poprzez znalezione elementy w dokumentach](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  