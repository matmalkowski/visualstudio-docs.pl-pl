---
title: "Porady: programowane Resetowanie zakresów w programie Word dokumentów | Dokumentacja firmy Microsoft"
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
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 08a2b57c9f30fab0b975ecf84ef8e0fb3127d346
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Porady: Programowane resetowanie zakresów w dokumentach programu Word
  Użyj <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> metodę, aby zmienić rozmiar zakresu istniejącego dokumentu Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-reset-an-existing-range"></a>Aby zresetować istniejący zakres  
  
1.  Ustaw zakres początkowy pierwszych siedem znaków w dokumencie.  
  
     Poniższy przykład kodu może służyć w dostosowaniu poziomie dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]  
  
     Poniższy przykład kodu można używać w dodatku VSTO. Ten kod zawiera aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]  
  
2.  Użyj <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> Rozpocznij zakres przy drugie zdanie i Zakończ ją na końcu piątej zdanie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]  
  
## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu  
  
#### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Aby zresetować zakresu istniejących w dostosowaniu poziomie dokumentu  
  
1.  Poniższy przykład przedstawia pełny przykład dostosowywania na poziomie dokumentu. Aby użyć tego kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
#### <a name="to-reset-an-existing-range-in-an-vsto-add-in"></a>Aby zresetować istniejący zakres w dodatku VSTO  
  
1.  Poniższy przykład przedstawia pełny przykład dodatku VSTO. Aby użyć tego kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Porady: programowane pobieranie początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Instrukcje: Programowe zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)  
  
  