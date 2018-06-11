---
title: 'Porady: programowane ukrywanie tekstu w dokumentach'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f90a467fcb8fa22a93774aa22427976e60875168
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257348"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Porady: programowane ukrywanie tekstu w dokumentach
  Tekst w dokumencie można ukryć, ustawiając <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> właściwość <xref:Microsoft.Office.Interop.Word.Range.Font%2A> dla określonego zakresu tekstu.  
  
 Na przykład można tymczasowo ukryć tekst wewnątrz <xref:Microsoft.Office.Tools.Word.Bookmark> (w dostosowaniu poziomie dokumentu) lub <xref:Microsoft.Office.Interop.Word.Bookmark> (w VSTO Dodaj) przed wysłaniem dokumentu do drukarki.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Aby ukryć tekst w formancie zakładki podczas wydruku dokumentu  
  
1.  Tworzenie procedury, która ukrywa cały tekst, który znajduje się w określonym zakresie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]  
  
2.  Tworzenie procedury, która odkrywa cały tekst, który znajduje się w określonym zakresie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]  
  
3.  Zakres zakładek do przekazania `HideText` metody, wydrukować dokument, a następnie przekazać do tego samego zakresu `UnhideText` metody.  
  
     Poniższy przykład kodu może służyć w dostosowaniu poziomie dokumentu. Aby użyć tego przykładu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]  
  
     Poniższy przykład kodu można używać w dodatku VSTO. W tym przykładzie użyto aktywny dokument. Aby użyć w przykładzie, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 Ten przykład kodu zakłada, że dokument zawiera <xref:Microsoft.Office.Tools.Word.Bookmark> formantu (w dostosowaniu poziomie dokumentu) lub <xref:Microsoft.Office.Interop.Word.Bookmark> kontrolki (dodatku VSTO) o nazwie `bookmark1`.  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane drukowanie dokumentów](../vsto/how-to-programmatically-print-documents.md)   
 [Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Porady: programowane Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Porady: programowane Aktualizowanie tekstu zakładki](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  