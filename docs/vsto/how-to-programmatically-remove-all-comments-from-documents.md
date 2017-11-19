---
title: "Porady: programowane usuwanie wszystkich komentarzy z dokumentów | Dokumentacja firmy Microsoft"
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
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c85ea6dba57d69c4936ac05687516c0195a1d82f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Porady: Programowane usuwanie wszystkich komentarzy z dokumentów
  Metoda operacji DeleteAllComments umożliwia usuwanie wszystkich komentarzy z dokumentu programu Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Usuwanie wszystkich komentarzy z dokumentu, który jest częścią dostosowania poziomie dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> metody `ThisDocument` klasy w projekcie. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` klasy.  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
### <a name="to-remove-all-comments-from-a-document-by-using-an-vsto-add-in"></a>Aby usunąć wszystkie komentarze z dokumentu za pomocą dodatków narzędzi VSTO  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> metody <xref:Microsoft.Office.Interop.Word.Document> z którego chcesz usunąć komentarz.  
  
     Poniższy przykład kodu usuwa wszystkie komentarze z aktywnego dokumentu. Aby użyć w tym przykładzie kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane Dodawanie komentarzy do tekstu w dokumentach](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Element hosta dokumentu](../vsto/document-host-item.md)  
  
  