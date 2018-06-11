---
title: 'Porady: programowane Dodawanie zdjęć i WordArt do dokumentów'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 61399df32ef0f22d1d0aacf23dea45c1357c7579
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255109"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Porady: programowane Dodawanie zdjęć i WordArt do dokumentów
  Obrazy i obiekty można dodać do dokumentów w czasie projektowania lub w czasie wykonywania. WordArt umożliwia dodanie ozdobne tekstu w dokumentach programu Microsoft Word pakietu Office. Te efektów tekstowych specjalne są rysowania obiektów, które można dostosować i Wstaw do dokumentu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="add-a-picture-at-design-time"></a>Dodawanie obrazu w czasie projektowania  
 Jeśli tworzysz dostosowania poziomie dokumentu, można dodać obrazu do dokumentu w czasie projektowania.  
  
### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Aby dodać obraz do dokumentu programu Word w czasie projektowania  
  
1.  Umieść kursor w miejscu, w którym chcesz wstawić obraz w dokumencie.  
  
2.  Kliknij przycisk **Wstaw** karty wstążki.  
  
3.  W **ilustracje** kliknij przycisk **obraz**.  
  
4.  W **Wstaw obraz** okno dialogowe, przejdź do obrazu, który chcesz wstawić, a następnie kliknij przycisk **Wstaw**.  
  
     Obraz jest dodawany do dokumentu w bieżącej lokalizacji kursora.  
  
## <a name="add-a-picture-at-runtime"></a>Dodawanie obrazu w czasie wykonywania  
 Można wstawić obrazu do dokumentu w bieżącej lokalizacji kursora.  
  
### <a name="to-add-a-picture-at-the-cursor-location"></a>Aby dodać obraz w lokalizacji kursora  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> metody <xref:Microsoft.Office.Interop.Word.InlineShapes> zbierania i przekazywania pliku.  
  
     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]  
  
## <a name="add-wordart-at-design-time"></a>Dodawanie obiektów WordArt w czasie projektowania  
 Jeśli tworzysz dostosowania poziomie dokumentu, można dodać WordArt do dokumentu w czasie projektowania.  
  
### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Aby dodać WordArt do dokumentów programu Word w czasie projektowania  
  
1.  Umieść kursor w miejscu Wstaw obiekt WordArt do dokumentu.  
  
2.  Kliknij przycisk **Wstaw** karty wstążki.  
  
3.  W **tekst** kliknij przycisk **WordArt**, a następnie wybierz styl WordArt.  
  
4.  Tekst, który ma być wyświetlany w dokumencie, aby dodać **edytowanie tekstu WordArt** okno dialogowe i kliknij przycisk **OK**.  
  
     Tekst zostanie dodany do dokumentu z wybrany styl WordArt zastosowany.  
  
## <a name="add-wordart-at-runtime"></a>Dodawanie obiektów WordArt w czasie wykonywania  
 Można wstawić obiektów WordArt do dokumentów w bieżącej lokalizacji kursora. Procedura wygląda różnie na poziomie dokumentu i dodatków VSTO.  
  
### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Aby dodać WordArt w lokalizacji kursora w dostosowaniu poziomie dokumentu  
  
1.  Pobierz pozycję po lewej stronie i największe bieżącej lokalizacji kursora.  
  
     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]  
  
2.  Wywołanie <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metody <xref:Microsoft.Office.Interop.Word.Shapes> obiektu w dokumencie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]  
  
### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Aby dodać WordArt w lokalizacji kursora w dodatku VSTO  
  
1.  Pobierz pozycję po lewej stronie i największe bieżącej lokalizacji kursora.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]  
  
2.  Wywołanie <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metody <xref:Microsoft.Office.Interop.Word.Shapes> obiektu dokumentów aktywnych (lub innego dokumentu, który określisz).  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
  
-   Obraz o nazwie *SamplePicture.jpg* musi istnieć na dysku C.  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Porady: programowane Wstawianie tekstu w dokumentach programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Porady: programowane Przywracanie zaznaczenia po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Porady: programowane zapisywanie dokumentów](../vsto/how-to-programmatically-save-documents.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  