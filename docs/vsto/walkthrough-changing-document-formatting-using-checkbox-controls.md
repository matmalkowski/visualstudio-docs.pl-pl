---
title: 'Wskazówki: Zmiana formatowania dokumentu za pomocą formantów CheckBox'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 459253c6a84add4fcca68565d5bf082dc0931f22
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Wskazówki: Zmiana formatowania dokumentu za pomocą formantów CheckBox
  W tym przewodniku pokazano, jak używać formanty formularzy systemu Windows w dostosowaniu poziomie dokumentu dla programu Microsoft Office Word do zmiany formatowania tekstu.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie tekstu i formantu do dokumentu w projektach na poziomie dokumentu w czasie projektowania.  
  
-   Formatowanie tekstu, po wybraniu opcji.  
  
 Aby zobaczyć wynik jako ukończonego próbka, zobacz przykład formanty programu Word w [Office development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Utwórz projekt  
 Pierwszym krokiem jest utworzenie projektu dokument programu Word.  
  
### <a name="create-a-new-project"></a>Tworzenie nowego projektu  
  
1.  Tworzenie projektu dokument programu Word o nazwie **Moje formatowania Word**. W kreatorze Wybierz **Utwórz nowy dokument**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy dokument programu Word w Projektancie i dodaje **Moje formatowania Word** projektu do **Eksploratora rozwiązań**.  
  
## <a name="add-text-and-controls-to-the-word-document"></a>Dodawanie tekstu i formantów do dokumentu programu Word  
 W ramach tego przewodnika, Dodaj trzy pola wyboru i tekst w <xref:Microsoft.Office.Tools.Word.Bookmark> formantu do dokumentu programu Word. Pola wyboru będą widoczne dla użytkownika opcje formatowania tekstu.  
  
### <a name="add-three-check-boxes"></a>Dodaj trzy pola wyboru  
  
1.  Sprawdź, czy dokument jest otwarty w projektancie programu Visual Studio.  
  
2.  Z **formanty standardowe** karcie **przybornika**, przeciągnij pierwszy <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> formantu do dokumentu.  
  
3.  W **właściwości** okna, Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**applyBoldFont**|  
    |**Tekst**|**Bold**|  
  
4.  Naciśnij klawisz **Enter** przenieść punkt wstawiania poniżej pierwsze pole wyboru.  
  
5.  Dodawanie drugiego pola wyboru w dokumencie poniżej `ApplyBoldFont` pole wyboru i zmienić następujących właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**applyItalicFont**|  
    |**Tekst**|**Kursywa**|  
  
6.  Naciśnij klawisz **Enter** przenieść punkt wstawiania poniżej drugiego pola wyboru.  
  
7.  Dodaj do dokumentu poniżej trzecie pole wyboru `ApplyItalicFont` pole wyboru i zmienić następujących właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**applyUnderlineFont**|  
    |**Tekst**|**Podkreślenie**|  
  
### <a name="add-text-and-a-bookmark-control"></a>Dodawanie tekstu i formant zakładki  
  
1.  Przenieś punkt wstawiania poniżej formanty pól wyboru i wpisz następujący tekst:  
  
     **Kliknij pole wyboru, aby zmienić formatowanie ten tekst.**  
  
2.  Z **formanty Word** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> formantu do dokumentu.  
  
     **Dodaj formant zakładki** zostanie wyświetlone okno dialogowe.  
  
3.  Zaznacz tekst dodany do dokumentu, a następnie kliknij przycisk **OK**.  
  
     A <xref:Microsoft.Office.Tools.Word.Bookmark> formantu o nazwie **Bookmark1** jest dodawany do zaznaczonego tekstu w dokumencie.  
  
4.  W **właściwości** okna, zmień wartość **(nazwa)** właściwości **fontText.**  
  
 Następnie należy napisać kod do formatowania tekstu, gdy pole wyboru jest zaznaczone lub wyczyszczone.  
  
## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Formatowanie tekstu, gdy pole wyboru jest zaznaczone lub wyczyszczone  
 Gdy użytkownik wybierze opcję formatowania, Zmień format tekstu w dokumencie.  
  
### <a name="change-formatting-when-a-check-box-is-selected"></a>Zmienianie formatowania po zaznaczeniu pola wyboru  
  
1.  Kliknij prawym przyciskiem myszy `ThisDocument` w **Eksploratora rozwiązań**, a następnie kliknij przycisk **kod widoku** menu skrótów.  
  
2.  Język C# tylko, Dodaj następujące ograniczenia, aby **ThisDocument** klasy.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]  
  
3.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń `applyBoldFont` pole wyboru.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]  
  
4.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń `applyItalicFont` pole wyboru.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]  
  
5.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń `applyUnderlineFont` pole wyboru.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]  
  
6.  W języku C#, należy dodać obsługę zdarzeń dla pola tekstowego <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzeń. Aby uzyskać informacje o sposobie tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować dokument, aby sprawdzić, czy tekst jest prawidłowo sformatowane, zaznacz lub usuń zaznaczenie pola wyboru.  
  
### <a name="test-your-document"></a>Dokument należy przetestować  
  
1.  Naciśnij klawisz **F5** do uruchomienia projektu.  
  
2.  Wybierz lub wyczyść pole wyboru.  
  
3.  Upewnij się, że tekst jest prawidłowo sformatowany.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawy za pomocą pola wyboru i programowane Zmienianie formatowania tekstu na dokumentów programu Word. Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Użyj przycisku, aby wypełnić pole tekstowe. Aby uzyskać więcej informacji, zobacz [wskazówki: wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Za pomocą przycisków radiowych, aby wybrać styl wykresu. Aby uzyskać więcej informacji, zobacz [wskazówki: Aktualizacja wykresu w dokumencie za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  

## <a name="see-also"></a>Zobacz także  
 [Wskazówki dotyczące przy użyciu programu Word](../vsto/walkthroughs-using-word.md)   
 [Office development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Ograniczenia formantów formularzy systemu Windows w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  