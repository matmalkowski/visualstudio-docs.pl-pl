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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9aa3e4b21aedff239aabde616b12a4f59281ec0a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
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
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  