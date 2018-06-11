---
title: 'Wskazówki: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44cbabd41e40c0e157a75fa260985752e3d5e016
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257914"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Wskazówki: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku
  W tym przewodniku pokazano, jak używać przycisków i pola tekstowe w dostosowaniu poziomie dokumentu dla programu Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie formantów do dokumentów programu Word w projektach na poziomie dokumentu w czasie projektowania.  
  
-   Wypełnianie pola tekstowego, gdy przycisk zostanie kliknięty.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Utwórz projekt  
 Pierwszym krokiem jest utworzenie projektu dokument programu Word.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu dokument programu Word o nazwie **Moje przycisk Word**. W kreatorze Wybierz **Utwórz nowy dokument**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy dokument programu Word w Projektancie i dodaje **Moje przycisk Word** projektu do **Eksploratora rozwiązań**.  
  
## <a name="add-controls-to-the-word-document"></a>Dodawanie formantów do dokumentów programu Word  
 Formanty interfejsu użytkownika składają się z przycisku i pola tekstowego na dokument programu Word.  
  
### <a name="to-add-a-button-and-a-text-box"></a>Aby dodać przycisk i pole tekstowe  
  
1.  Sprawdź, czy dokument jest otwarty w projektancie programu Visual Studio.  
  
2.  Z **formanty standardowe** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Word.Controls.TextBox> formantu do dokumentu.  
  
    > [!NOTE]  
    >  W programie Word, są usuwane formantów wiersza z tekstem domyślnie. Można zmodyfikować formantów i obiektów kształtu są wstawiane przez zmianę domyślnych na **Edytuj** karcie **opcje** okno dialogowe w programie Word.  
  
3.  Na **widoku** menu, kliknij przycisk **okna właściwości**.  
  
4.  Znajdź **Poletekstowe1** w **właściwości** pola rozwijanego okna i zmień **nazwa** właściwości pola tekstowego **Wyświetlany_tekst**.  
  
5.  Przeciągnij **przycisk** kontroli w dokumencie i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**insertText**|  
    |**Tekst**|**Wstawianie tekstu**|  
  
 Teraz można napisać kod, który będzie uruchamiany po kliknięciu przycisku.  
  
## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Wypełnij pola tekstowego, po kliknięciu przycisku  
 Za każdym razem, gdy użytkownik kliknie przycisk **Hello World!** dodaje się do pola tekstowego.  
  
### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Można zapisać w polu tekstowym, po kliknięciu przycisku  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument**, a następnie kliknij przycisk **kod widoku** menu skrótów.  
  
2.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń przycisku.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  W języku C#, należy dodać program obsługi zdarzeń dla przycisku do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzeń. Aby uzyskać informacje dotyczące tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować dokument, aby upewnić się, że komunikat **Hello World!** zostanie wyświetlony w polu tekstowym, po kliknięciu przycisku.  
  
### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz **F5** do uruchomienia projektu.  
  
2.  Kliknij przycisk.  
  
3.  Upewnij się, że **Witaj świecie!** zostanie wyświetlona w polu tekstowym.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawy za pomocą przycisków i pola tekstu w dokumentach programu Word. Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Zmienianie formatowania za pomocą pola kombi Aby uzyskać więcej informacji, zobacz [wskazówki: dokument Zmienianie formatowania za pomocą formantów CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Za pomocą przycisków radiowych, aby wybrać styl wykresu. Aby uzyskać więcej informacji, zobacz [wskazówki: Aktualizacja wykresu w dokumencie za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Formanty formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Wskazówki dotyczące przy użyciu programu Word](../vsto/walkthroughs-using-word.md)   
 [Office development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Porady: dodawanie formantów formularzy systemu Windows do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)  
  
  