---
title: "Porady: programowane Aktualizowanie tekstu zakładki | Dokumentacja firmy Microsoft"
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
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: af3252f87bd3c7d6a6c6e75ae85cea4cd75bd1e9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Porady: Programowane aktualizowanie tekstu zakładki
  Tekst można wstawiać do symbolu zastępczego zakładki w dokumencie programu Microsoft Office Word tak, aby można było odzyskać tekst w późniejszym czasie lub tekst w zakładki. Jeśli tworzysz dostosowania poziomie dokumentu, można także zaktualizować tekst w <xref:Microsoft.Office.Tools.Word.Bookmark> formant, który jest powiązany z danymi. Aby uzyskać więcej informacji, zobacz [wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Obiekt zakładki może mieć jeden z dwóch typów:  
  
-   A <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki hosta.  
  
     <xref:Microsoft.Office.Tools.Word.Bookmark>Formanty rozszerzyć natywnego <xref:Microsoft.Office.Interop.Word.Bookmark> obiektów przez włączenie wiązania z danymi i udostępnia zdarzenia. Aby uzyskać informacje o formantach hosta, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
-   Natywny <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu.  
  
     <xref:Microsoft.Office.Interop.Word.Bookmark>obiekty nie mają możliwości powiązania zdarzenia lub dane.  
  
 Po przypisaniu tekst do zakładki to zachowanie różni się między <xref:Microsoft.Office.Interop.Word.Bookmark> i <xref:Microsoft.Office.Tools.Word.Bookmark>. Aby uzyskać więcej informacji, zobacz [formant zakładki](../vsto/bookmark-control.md).  
  
## <a name="using-host-controls"></a>Używanie formantów hosta  
  
#### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Aby zaktualizować zawartość zakładki przy użyciu formant zakładki  
  
1.  Tworzenie procedury, która przyjmuje `bookmark` argument nazwę zakładki, a `newText` argument ciągu można przypisać do <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwości.  
  
    > [!NOTE]  
    >  Przypisywanie tekst <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> lub <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> właściwość <xref:Microsoft.Office.Tools.Word.Bookmark> formantu nie powoduje zakładkę do usunięcia.  
  
     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]  
  
2.  Przypisz *newText* ciąg <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwość <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]  
  
## <a name="using-word-objects"></a>Za pomocą obiektów programu Word  
  
#### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Aby zaktualizować zawartość zakładki przy użyciu obiektu zakładki programu Word  
  
1.  Tworzenie procedury, która ma `bookmark` argument nazwy <xref:Microsoft.Office.Interop.Word.Bookmark>, a `newText` argument ciągu można przypisać do <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwość zakładki.  
  
    > [!NOTE]  
    >  Przypisywanie tekstu do natywnego programu Word <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu powoduje zakładkę do usunięcia.  
  
     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]  
  
2.  Przypisz *newText* ciąg <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwość zakładki, która automatycznie usuwa zakładki. Następnie ponownie Dodaj zakładkę do <xref:Microsoft.Office.Interop.Word.Bookmarks> kolekcji.  
  
     Poniższy przykład kodu może służyć w dostosowaniu poziomie dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]  
  
     Poniższy przykład kodu można używać w dodatku VSTO. W tym przykładzie użyto aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane Wstawianie tekstu w dokumentach programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md)   
 [Bookmark, kontrolka](../vsto/bookmark-control.md)  
  
  