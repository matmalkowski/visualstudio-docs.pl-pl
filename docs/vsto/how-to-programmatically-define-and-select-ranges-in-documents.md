---
title: "Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach | Dokumentacja firmy Microsoft"
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
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0c99b40147d08a924b9f66a0f8a45a29204e37bc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Porady: Programowane definiowanie i zaznaczanie zakresów w dokumentach
  Można zdefiniować zakres na dokument programu Microsoft Word pakietu Office przy użyciu <xref:Microsoft.Office.Interop.Word.Range> obiektu. Zaznacza cały dokument. na kilka sposobów, na przykład za pomocą <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> obiekt lub przy użyciu właściwości Content <xref:Microsoft.Office.Tools.Word.Document> klasy (w dostosowaniu poziomie dokumentu) lub <xref:Microsoft.Office.Interop.Word.Document> klasy (w Dodatku narzędzi VSTO).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="defining-a-range"></a>Definiowanie zakresu  
 Poniższy przykład przedstawia sposób tworzenia nowego <xref:Microsoft.Office.Interop.Word.Range> obiekt, który obejmuje siedem pierwsze znaki w aktywnym dokumencie, łącznie z niedrukowalne znaki. Następnie wybiera on tekst w zakresie.  
  
#### <a name="to-define-a-range-in-a-document-level-customization"></a>Aby zdefiniować zakres na dostosowanie poziomie dokumentu  
  
1.  Dodaj zakres do dokumentu, przekazując znaku początkową i końcową <xref:Microsoft.Office.Tools.Word.Document.Range%2A> metody <xref:Microsoft.Office.Tools.Word.Document> klasy. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]  
  
#### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Aby zdefiniować zakres za pomocą dodatków narzędzi VSTO  
  
1.  Dodaj zakres do dokumentu, przekazując znaku początkową i końcową <xref:Microsoft.Office.Interop.Word._Document.Range%2A> metody <xref:Microsoft.Office.Interop.Word.Document> klasy. Poniższy przykładowy kod dodaje zakres do aktywnego dokumentu. Aby użyć w tym przykładzie kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]  
  
## <a name="selecting-a-range-in-a-document-level-customization"></a>Wybieranie zakresu w dostosowaniu poziomie dokumentu  
 Poniższe przykłady przedstawiają sposób zaznacza cały dokument za pomocą <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> obiekt lub przy użyciu <xref:Microsoft.Office.Tools.Word.Document.Content%2A> właściwość <xref:Microsoft.Office.Tools.Word.Document> klasy.  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Aby zaznaczyć cały dokument. jako zakres przy użyciu metody Select  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> zawierający cały dokument. Skorzystaj z następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Aby zaznaczyć cały dokument. jako zakres przy użyciu właściwości zawartości  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.Document.Content%2A> właściwość, aby zdefiniować zakres obejmujący cały dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
     [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]  
  
 Aby zdefiniować zakres, można użyć metody i właściwości innych obiektów.  
  
#### <a name="to-select-a-sentence-in-the-active-document"></a>Aby wybrać zdanie w aktywnym dokumencie  
  
1.  Ustaw zakres przy użyciu <xref:Microsoft.Office.Interop.Word.Sentences> kolekcji. Użyj indeksu zdania, który chcesz wybrać.  
  
     [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
     [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]  
  
 Innym sposobem wybierz zdania jest ręcznie ustawić wartości początkowa i końcowa zakresu.  
  
#### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Aby wybrać zdania ręcznie ustawić wartości początkowa i końcowa  
  
1.  Utwórz zmienną zakresu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]  
  
2.  Sprawdź, czy istnieją co najmniej dwa zdania dokumentu, ustaw *Start* i *zakończenia* argumenty zakresu, a następnie wybierz zakres.  
  
     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]  
  
## <a name="selecting-a-range-by-using-a-vsto-add-in"></a>Wybieranie zakresu przy użyciu dodatku narzędzi VSTO  
 Poniższe przykłady przedstawiają sposób zaznacza cały dokument za pomocą <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> obiekt lub przy użyciu <xref:Microsoft.Office.Interop.Word._Document.Content%2A> właściwość <xref:Microsoft.Office.Interop.Word.Document> klasy.  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Aby zaznaczyć cały dokument. jako zakres przy użyciu metody Select  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> zawierający cały dokument. Poniższy przykład kodu Zaznacza zawartość aktywnego dokumentu. Aby użyć w tym przykładzie kodu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Aby zaznaczyć cały dokument. jako zakres przy użyciu właściwości zawartości  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word._Document.Content%2A> właściwość, aby zdefiniować zakres obejmujący cały dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]  
  
 Aby zdefiniować zakres, można użyć metody i właściwości innych obiektów.  
  
#### <a name="to-select-a-sentence-in-the-active-document"></a>Aby wybrać zdanie w aktywnym dokumencie  
  
1.  Ustaw zakres przy użyciu <xref:Microsoft.Office.Interop.Word.Sentences> kolekcji. Użyj indeksu zdania, który chcesz wybrać.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]  
  
 Innym sposobem wybierz zdania jest ręcznie ustawić wartości początkowa i końcowa zakresu.  
  
#### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Aby wybrać zdania ręcznie ustawić wartości początkowa i końcowa  
  
1.  Utwórz zmienną zakresu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]  
  
2.  Sprawdź, czy istnieją co najmniej dwa zdania dokumentu, ustaw *Start* i *zakończenia* argumenty zakresu, a następnie wybierz zakres.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md)   
 [Porady: programowane rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Porady: programowane pobieranie początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Porady: programowane rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Porady: programowane Resetowanie zakresów w programie Word dokumentów](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Porady: programowane zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Instrukcje: Programowe wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  