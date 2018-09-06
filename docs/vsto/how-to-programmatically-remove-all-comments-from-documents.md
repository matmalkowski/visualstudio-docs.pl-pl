---
title: 'Porady: programowane usuwanie wszystkich komentarzy z dokumentów'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 005414fce7b7bc04c22b266f5f5f6d54a399a182
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677260"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Porady: programowane usuwanie wszystkich komentarzy z dokumentów
  Użyj `DeleteAllComments` metodę, aby usunąć wszystkie komentarze z dokumentu programu Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Aby usunąć wszystkie komentarze z dokumentu, który jest częścią dostosowywania poziomie dokumentu  
  
1.  Wywołaj <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> metody `ThisDocument` klasy w projekcie. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` klasy.  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Aby usunąć wszystkie komentarze z dokumentu za pomocą dodatku narzędzi VSTO  
  
1.  Wywołaj <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> metody <xref:Microsoft.Office.Interop.Word.Document> z którego chcesz usunąć komentarze.  
  
     Poniższy kod usuwa wszystkie komentarze z aktywnego dokumentu. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane Dodawanie komentarzy do tekstu w dokumentach](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Element hosta dokumentu](../vsto/document-host-item.md)  
  
  