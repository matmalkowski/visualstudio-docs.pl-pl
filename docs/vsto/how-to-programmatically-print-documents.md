---
title: "Porady: programowane drukowanie dokumentów | Dokumentacja firmy Microsoft"
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
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9e967ae840486126f5f5fb457e2b1ef8eda57881
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-print-documents"></a>Porady: Programowane drukowanie dokumentów
  Można drukować cały dokument programu Microsoft Office Word lub części dokumentu, do drukarki domyślnej.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="printing-a-document-that-is-part-of-a-document-level-customization"></a>Drukowanie dokumentu, który jest częścią dostosowania poziomie dokumentu  
  
#### <a name="to-print-the-entire-document"></a>Aby wydrukować cały dokument.  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> metody `ThisDocument` klasy w projekcie do drukowania w całym dokumencie. Aby użyć tego przykładu, należy uruchomić kod z `ThisDocument` klasy.  
  
     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]  
  
#### <a name="to-print-the-current-page-of-the-document"></a>Aby wydrukować bieżącą stronę z dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> metody `ThisDocument` klasy w projekcie i określ drukowane jedną kopię bieżącej strony. Aby użyć tego przykładu, należy uruchomić kod z `ThisDocument` klasy.  
  
     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]  
  
## <a name="printing-a-document-by-using-an-vsto-add-in"></a>Drukowanie dokumentu przy użyciu dodatku narzędzi VSTO  
  
#### <a name="to-print-an-entire-document"></a>Aby wydrukować cały dokument.  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> metody <xref:Microsoft.Office.Interop.Word.Document> obiekt, który chcesz wydrukować. Poniższy przykład kodu Drukuje aktywny dokument. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]  
  
#### <a name="to-print-the-current-page-of-a-document"></a>Aby wydrukować bieżącą stronę z dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> metody <xref:Microsoft.Office.Interop.Word.Document> obiekt, który ma być drukowania i określ drukowane jedną kopię bieżącej strony. Poniższy przykład kodu Drukuje aktywny dokument. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]  
  
## <a name="see-also"></a>Zobacz też  
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  