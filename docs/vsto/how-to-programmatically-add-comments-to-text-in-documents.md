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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2702d8aed4dce16a2dde1c42b2b1410ebded14e3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
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
  
  