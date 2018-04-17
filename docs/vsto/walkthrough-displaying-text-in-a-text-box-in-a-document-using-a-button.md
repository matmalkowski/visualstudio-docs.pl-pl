---
title: 'Wskazówki: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 086137debfa35cb08dfa3b315208ce3686d74153
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button"></a>Wskazówka: wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku
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
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu dokument programu Word.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu dokument programu Word o nazwie **Moje przycisk Word**. W kreatorze Wybierz **Utwórz nowy dokument**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy dokument programu Word w Projektancie i dodaje **Moje przycisk Word** projektu do **Eksploratora rozwiązań**.  
  
## <a name="adding-controls-to-the-word-document"></a>Dodawanie formantów do dokumentów programu Word  
 Formanty interfejsu użytkownika składają się z przycisku i pola tekstowego na dokument programu Word.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>Aby dodać przycisk i pole tekstowe  
  
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
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Wypełnianie pola tekstowego, po kliknięciu przycisku  
 Za każdym razem, gdy użytkownik kliknie przycisk **Hello World!** dodaje się do pola tekstowego.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Można zapisać w polu tekstowym, po kliknięciu przycisku  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument**, a następnie kliknij przycisk **kod widoku** menu skrótów.  
  
2.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń przycisku.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  W języku C#, należy dodać program obsługi zdarzeń dla przycisku do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzeń. Aby uzyskać informacje dotyczące tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować dokument, aby upewnić się, że komunikat **Hello World!** zostanie wyświetlony w polu tekstowym, po kliknięciu przycisku.  
  
#### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Kliknij przycisk.  
  
3.  Upewnij się, że **Witaj świecie!** zostanie wyświetlona w polu tekstowym.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawy za pomocą przycisków i pola tekstu w dokumentach programu Word. Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Zmienianie formatowania za pomocą pola kombi Aby uzyskać więcej informacji, zobacz [wskazówki: zmiana dokumentu formatowania za pomocą formantów CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Za pomocą przycisków radiowych, aby wybrać styl wykresu. Aby uzyskać więcej informacji, zobacz [wskazówki: Aktualizacja wykresu w dokumencie przy użyciu przycisków](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)   
 [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Porady: dodawanie formantów do dokumentów pakietu Office formularzy systemu Windows](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Przegląd obiektów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)  
  
  