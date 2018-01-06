---
title: 'Porady: programowane Dodawanie komentarzy do tekstu w dokumentach | Dokumentacja firmy Microsoft'
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
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
ms.assetid: 4e396e31-01bf-424c-be6b-9a1806bcd572
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 69f320ef3e7b3914d9d6eadb7466b3a216ef95d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Porady: Programowane dodawanie komentarzy do tekstu w dokumentach
  Właściwość komentarze klasy dokumentu dodaje komentarz do zakresu tekstu w dokumencie programu Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Poniższy przykład dodaje komentarz do akapitu w dokumencie.  
  
### <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Aby dodać nowy komentarz do tekstu w dostosowaniu poziomie dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metody <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> właściwości i podaj zakres i tekst komentarza. Skorzystaj z następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
### <a name="to-add-a-new-comment-to-text-in-an-vsto-add-in"></a>Aby dodać nowy komentarz do tekstu w dodatku VSTO  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metody <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> właściwości i podaj zakres i tekst komentarza.  
  
     Poniższy przykładowy kod dodaje komentarz do aktywnego dokumentu. Aby użyć tego przykładu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aby zmienić inicjały użytkownika, które Word dodaje do komentarzy, użyj <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane usuwanie wszystkich komentarzy z dokumentów](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Element hosta dokumentu](../vsto/document-host-item.md)  
  
  