---
title: "Porady: programowane zwijanie zakresów lub zaznaczenia w dokumentach | Dokumentacja firmy Microsoft"
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
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
ms.assetid: 0bd059dd-8606-42ae-a8a9-97f8f3bd5cc5
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c69fa3a13c251c31aff6ca54ccc0a553e293347a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Porady: Programowane zwijanie zakresów lub zaznaczenia w dokumentach
  Jeśli pracujesz z <xref:Microsoft.Office.Interop.Word.Range> lub <xref:Microsoft.Office.Interop.Word.Selection> obiektu, możesz chcieć zmienić zaznaczenie do punktu wstawiania przed wstawieniem tekstu, aby uniknąć zastępowania istniejącego tekstu. Zarówno <xref:Microsoft.Office.Interop.Word.Range> i <xref:Microsoft.Office.Interop.Word.Selection> obiekty mają Zwiń — metoda, która korzysta z <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> wartości wyliczenia:  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart>Zwija zaznaczenie do początku zaznaczenia. Jest to wartość domyślna, jeśli nie określisz wartości wyliczenia.  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd>Zwija zaznaczenie do końca zaznaczenia.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-collapse-a-range-and-insert-new-text"></a>Zwiń zakresu i Wstaw nowy tekst  
  
1.  Utwórz <xref:Microsoft.Office.Interop.Word.Range> obiekt, który składa się z pierwszym akapicie w dokumencie.  
  
     Poniższy przykład kodu może służyć w dostosowaniu poziomie dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
     [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]  
  
     Poniższy przykład kodu można używać w dodatku VSTO. Ten kod zawiera aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]  
  
2.  Użyj <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> wartości wyliczenia, aby zwinąć zakresu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
     [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]  
  
3.  Wstawianie nowego tekstu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
     [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]  
  
4.  Wybierz <xref:Microsoft.Office.Interop.Word.Range>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
     [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]  
  
 Jeśli używasz <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> wartości wyliczenia, tekst dodaje się na początku akapit.  
  
 [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
 [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]  
  
 Może oczekiwać, że wstawianie nowych zdania czy Wstaw go przed znaczników akapitu, ale oznacza to inaczej ponieważ oryginalny zakres obejmuje znaczników akapitu. Aby uzyskać więcej informacji, zobacz [porady: programowane wykluczyć akapitu znaków podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).  
  
## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu  
  
#### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Aby zwinąć zakresu w dostosowaniu poziomie dokumentu  
  
1.  W poniższym przykładzie przedstawiono metodę Zakończenie dostosowywania na poziomie dokumentu. Aby użyć tego kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
#### <a name="to-collapse-a-range-in-an-vsto-add-in"></a>Aby zwinąć zakresu w dodatku VSTO  
  
1.  W poniższym przykładzie przedstawiono metodę pełną dodatku VSTO. Aby użyć tego kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane Wstawianie tekstu w dokumentach programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Porady: programowane pobieranie początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Porady: programowane wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Porady: programowane rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Instrukcje: Programowe resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  