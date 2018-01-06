---
title: 'Porady: programowane Wstawianie tekstu w dokumentach programu Word | Dokumentacja firmy Microsoft'
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
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
ms.assetid: 405d7442-8ba3-4fcc-b17e-7b289ffd3967
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: be7cc1dfcaf367fe890b32e4ba4523800936b819
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Porady: Programowane wstawianie tekstu w dokumentach programu Word
  Istnieją trzy główne metody Wstawianie tekstu w dokumentach programu Microsoft Office Word:  
  
-   Wstawianie tekstu w zakresie.  
  
-   Zastąp tekst w zakresie nowego tekstu.  
  
-   Użyj <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> metody <xref:Microsoft.Office.Interop.Word.Selection> obiektu, aby wstawić tekst na kursora lub zaznaczenia.  
  
> [!NOTE]  
>  Można również wstawić tekst do formantów zawartości i zakładki. Aby uzyskać więcej informacji, zobacz [formantów zawartości](../vsto/content-controls.md) i [formant zakładki](../vsto/bookmark-control.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="inserting-text-in-a-range"></a>Wstawianie tekstu w zakresie  
 Użyj <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwość <xref:Microsoft.Office.Interop.Word.Range> obiektu Wstawianie tekstu w dokumencie.  
  
#### <a name="to-insert-text-in-a-range"></a>Wstawianie tekstu w zakresie  
  
1.  Określ zakres na początku dokumentu i wstawić tekst **nowy tekst**.  
  
     Poniższy przykład kodu może służyć w dostosowaniu poziomie dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]  
  
     Poniższy przykład kodu można używać w dodatku VSTO. Ten kod zawiera aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]  
  
2.  Wybierz <xref:Microsoft.Office.Interop.Word.Range> obiektu, który ma rozszerzonej z jednego znaku do długości wstawionego tekstu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]  
  
## <a name="replacing-text-in-a-range"></a>Zastępowanie tekstu w zakresie  
 Jeśli określony zakres zawiera tekst, cały tekst w zakresie jest zastępowany wstawionego tekstu.  
  
#### <a name="to-replace-text-in-a-range"></a>Aby zastąpić tekst w zakresie  
  
1.  Utwórz <xref:Microsoft.Office.Interop.Word.Range> obiekt, który składa się z pierwsze 12 znaków w dokumencie.  
  
     Poniższy przykład kodu może służyć w dostosowaniu poziomie dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]  
  
     Poniższy przykład kodu można używać w dodatku VSTO. Ten kod zawiera aktywny dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]  
  
2.  Zastąp te znaki z ciągiem **nowy tekst**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]  
  
3.  Wybierz zakres.  
  
     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]  
  
## <a name="inserting-text-using-typetext"></a>Wstawianie tekstu przy użyciu obiektu TypeText  
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> Metody wstawia tekst w zaznaczenia. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>zachowuje się inaczej w zależności od opcji na komputerze użytkownika. Kod w poniższej procedurze deklaruje <xref:Microsoft.Office.Interop.Word.Selection> zmiennej obiektu i wyłącza **zastępowania** opcji w przypadku, gdy jest włączona. Jeśli **zastępowania** opcja jest aktywna, a następnie tekst obok kursora jest zastępowany.  
  
#### <a name="to-insert-text-using-the-typetext-method"></a>Aby wstawić tekst przy użyciu metody obiektu TypeText  
  
1.  Deklarowanie <xref:Microsoft.Office.Interop.Word.Selection> zmienna obiektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
     [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]  
  
2.  Wyłącz **zastępowania** opcji w przypadku, gdy jest włączona.  
  
     [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
     [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]  
  
3.  Sprawdź, czy bieżące zaznaczenie jest punkt wstawiania.  
  
     Jeśli tak jest, kod wstawia zdanie przy użyciu <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>i następnie akapitu znacznik przy użyciu <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> metody.  
  
     [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
     [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]  
  
4.  Kod w **ElseIf** zablokować testy, aby zobaczyć, czy zaznaczenie jest zaznaczeniem normalnego. Jeśli tak jest, następnie inne **Jeśli** zablokować testy, aby sprawdzić, czy **ReplaceSelection** opcja jest włączona. Jeśli tak jest, w kodzie użyto <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> Metoda wyboru, aby zwinąć zaznaczenie punkt wstawiania na początku bloku zaznaczonego tekstu. Wstaw tekst i znacznik akapitu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
     [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]  
  
5.  Jeśli zaznaczenie nie znajduje się punkt wstawiania lub bloku zaznaczonego tekstu, a następnie kod w **Else** bloku nie działają.  
  
     [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
     [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]  
  
 Można również użyć <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> metody <xref:Microsoft.Office.Interop.Word.Selection> obiektu, który naśladuje funkcji klawisza na klawiaturze. Jednak jeśli chodzi o Wstawianie i operowanie nimi tekstu, <xref:Microsoft.Office.Interop.Word.Range> obiektu zapewnia większą kontrolę.  
  
 Poniższy przykład przedstawia kompletny kod. Aby użyć tego przykładu, należy uruchomić kod z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
 [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
 [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane formatowanie tekstu w dokumentach](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [Porady: programowane definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Instrukcje: Programowe rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
  
  