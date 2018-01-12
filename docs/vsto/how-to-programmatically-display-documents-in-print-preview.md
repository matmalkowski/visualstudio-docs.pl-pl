---
title: "Porady: programowane wyświetlanie dokumentów w podglądzie wydruku | Dokumentacja firmy Microsoft"
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
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c4da179b2ead999634f77d8c53f32e458326e961
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Porady: Programowane wyświetlanie dokumentów w podglądzie wydruku
  Rozwiązania generuje raport, można wyświetlić raport w trybie podglądu wydruku do użytkownika.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>Procedury dotyczące dostosowań na poziomie dokumentu  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Aby wyświetlić dokument w podglądzie wydruku printpreview — metoda  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> metody <xref:Microsoft.Office.Tools.Word.Document> klasy. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Aby wyświetlić dokument w podglądzie wydruku przez ustawienie właściwości printpreview —  
  
1.  Ustaw <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> właściwość <xref:Microsoft.Office.Interop.Word.Application> do obiektu **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>Procedury dotyczące dodatków narzędzi VSTO  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Aby wyświetlić dokument w podglądzie wydruku printpreview — metoda  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> metody <xref:Microsoft.Office.Interop.Word.Document> przewidzianą do podglądu. Aby użyć w tym przykładzie kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Aby wyświetlić dokument w podglądzie wydruku przez ustawienie właściwości printpreview —  
  
1.  Ustaw <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> właściwość <xref:Microsoft.Office.Interop.Word.Application> do obiektu **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane drukowanie dokumentów](../vsto/how-to-programmatically-print-documents.md)   
 [Porady: programowane otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Instrukcje: Programowe tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md)  
  
  