---
title: 'Porady: programowane Dodawanie komentarzy do tekstu w dokumentach'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ca0d15ee69bb58aae765c03c1233a78bfeeb119c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676202"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Porady: programowane Dodawanie komentarzy do tekstu w dokumentach
  Właściwość komentarze klasy dokumentu dodaje komentarz do zakresu w dokumencie programu Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Poniższy przykład dodaje komentarz do pierwszego akapitu w dokumencie.  
  
## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Aby dodać nowy komentarz do tekstu w dostosowaniu na poziomie dokumentu  
  
1.  Wywołaj <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metody <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> właściwości i podaj zakres i tekst komentarza. Aby użyć w poniższym przykładzie kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Aby dodać nowy komentarz do tekstu w dodatku narzędzi VSTO  
  
1.  Wywołaj <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metody <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> właściwości i podaj zakres i tekst komentarza.  
  
     Poniższy przykład kodu dodaje komentarz do aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Aby zmienić inicjały użytkownika, które program Word dodaje do komentarzy, użyj <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane usuwanie wszystkich komentarzy z dokumentów](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Element hosta dokumentu](../vsto/document-host-item.md)  
  
  