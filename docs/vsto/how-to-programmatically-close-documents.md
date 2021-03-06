---
title: 'Porady: programowane zamykanie dokumentów'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a846aded5d24f84fdaeac79a1bad6c61a3f5570
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257777"
---
# <a name="how-to-programmatically-close-documents"></a>Porady: programowane zamykanie dokumentów
  Możesz zamknąć aktywny dokument, lub można określić dokumentu, aby zamknąć.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="close-the-active-document"></a>Zamyka aktywny dokument.  
 Istnieją dwie procedury zamykanie dokumentów aktywnych: jeden dla Dostosowywanie na poziomie dokumentu i jeden dla dodatków VSTO.  
  
### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Aby zamknąć aktywny dokument w dostosowaniu poziomie dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Word.Document.Close%2A> metody `ThisDocument` klasy w projekcie, aby zamknąć dokument służącej do dostosowywania. Skorzystaj z następującego przykładu kodu, uruchom go z `ThisDocument` klasy.  
  
    > [!NOTE]  
    >  W tym przykładzie przekazuje <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> do wartości *SaveChanges* parametr, aby zamknąć bez zapisywania zmian lub monitowania użytkownika.  
  
     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]  
  
### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Aby zamknąć aktywny dokument w dodatku VSTO  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word._Document.Close%2A> metody <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> właściwość, aby zamknąć aktywny dokument. Skorzystaj z następującego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
    > [!NOTE]  
    >  W tym przykładzie przekazuje <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> do wartości *SaveChanges* parametr, aby zamknąć bez zapisywania zmian lub monitowania użytkownika.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]  
  
## <a name="close-a-document-that-you-specify-by-name"></a>Zamyka dokument, który jest określany na podstawie nazwy  
 Tak jak zamknąć dokument, który jest określany na podstawie nazwy jest taki sam dla dodatków VSTO i dostosowywanie na poziomie dokumentu.  
  
### <a name="to-close-a-document-that-you-specify-by-name"></a>Aby zamknąć dokument, który jest określany na podstawie nazwy  
  
1.  Określ nazwę dokumentu jako argument <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> kolekcji, a następnie wywołania <xref:Microsoft.Office.Interop.Word._Document.Close%2A> metody. Poniższy przykład kodu zakłada, że dokument o nazwie **NewDocument** jest otwarty w programie Word.  
  
    > [!NOTE]  
    >  W tym przykładzie przekazuje <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> do wartości *SaveChanges* parametr, aby zamknąć bez zapisywania zmian lub monitowania użytkownika.  
  
     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Porady: programowane zapisywanie dokumentów](../vsto/how-to-programmatically-save-documents.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  