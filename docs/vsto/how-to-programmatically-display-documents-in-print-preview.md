---
title: 'Porady: programowane wyświetlanie dokumentów w podglądzie wydruku'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1a2ab538707156826be3a31252cde16e67edff9c
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257228"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Porady: programowane wyświetlanie dokumentów w podglądzie wydruku
  Rozwiązania generuje raport, można wyświetlić raport w trybie podglądu wydruku do użytkownika.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>Procedury dotyczące dostosowań na poziomie dokumentu  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Aby wyświetlić dokument w podglądzie wydruku printpreview — metoda  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> metody <xref:Microsoft.Office.Tools.Word.Document> klasy. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Aby wyświetlić dokument w podglądzie wydruku przez ustawienie właściwości printpreview —  
  
1.  Ustaw <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> właściwość <xref:Microsoft.Office.Interop.Word.Application> do obiektu **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>Procedury dotyczące dodatków narzędzi VSTO  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Aby wyświetlić dokument w podglądzie wydruku printpreview — metoda  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> metody <xref:Microsoft.Office.Interop.Word.Document> przewidzianą do podglądu. Aby użyć w tym przykładzie kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Aby wyświetlić dokument w podglądzie wydruku przez ustawienie właściwości printpreview —  
  
1.  Ustaw <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> właściwość <xref:Microsoft.Office.Interop.Word.Application> do obiektu **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane drukowanie dokumentów](../vsto/how-to-programmatically-print-documents.md)   
 [Porady: programowane otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Porady: programowane tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md)  
  
  