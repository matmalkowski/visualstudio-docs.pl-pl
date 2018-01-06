---
title: 'Porady: programowane formatowanie tekstu w dokumentach | Dokumentacja firmy Microsoft'
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
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
ms.assetid: 0a84893b-5ccc-4515-a2dc-95773ee8eaba
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 30bc3e878be8667b8ea306bcf7ba3a9648a706c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Porady: Programowane formatowanie tekstu w dokumentach
  Można użyć <xref:Microsoft.Office.Interop.Word.Range> obiekt do formatu tekstu w dokumencie programu Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 W poniższym przykładzie wybiera pierwszy akapitu w dokumencie i zmienia rozmiar czcionki, nazwa czcionki i wyrównania. Następnie wybiera zakres i wyświetla komunikat, aby wstrzymać przed wykonaniem w następnej sekcji kodu. Następna sekcja wywołuje metodę cofania <xref:Microsoft.Office.Tools.Word.Document> element hosta (na poziomie dokumentu dostosowanie) lub <xref:Microsoft.Office.Interop.Word.Document> klasy (w przypadku dodatku VSTO) trzy razy. Stosuje styl wcięcie normalny, a Wyświetla komunikat, aby wstrzymać kod. Następnie kod wywołuje <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> raz, metody i wyświetla okno komunikatu.  
  
## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu  
  
#### <a name="to-format-text-using-a-document-level-customization"></a>Aby sformatować tekst przy użyciu dostosowania poziomie dokumentu  
  
1.  Poniższy przykład służy w dostosowaniu poziomie dokumentu. Aby użyć tego kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]  
  
## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO  
  
#### <a name="to-format-text-using-a-vsto-add-in"></a>Aby sformatować tekst przy użyciu dodatku narzędzi VSTO  
  
1.  Poniższy przykład służy w dodatku VSTO. W tym przykładzie użyto aktywny dokument. Aby użyć tego kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Porady: programowane Wstawianie tekstu w dokumentach programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Instrukcje: Programowe wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  