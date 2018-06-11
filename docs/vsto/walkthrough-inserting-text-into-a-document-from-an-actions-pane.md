---
title: 'Wskazówki: Wstawianie tekstu do dokumentu z okienka akcji'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 488b885b40b4cda064ae15438822ab85725526ac
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258483"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Wskazówki: Wstawianie tekstu do dokumentu z okienka akcji
  Ten przewodnik przedstawia sposób tworzenia okienka akcji w dokumencie programu Microsoft Office Word. W okienku Akcje zawiera dwa formanty, które gromadzenia danych wejściowych, a następnie wyślij go do dokumentu.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Projektowanie interfejsu za pomocą formantów formularzy systemu Windows na formancie w okienku Akcje.  
  
-   Wyświetl okienko akcji po otwarciu aplikacji.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Utwórz projekt  
 Pierwszym krokiem jest utworzenie projektu dokument programu Word.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu dokument programu Word o nazwie **Moje podstawowe okienka Akcje**. W kreatorze Wybierz **Utwórz nowy dokument**. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy dokument programu Word w Projektancie i dodaje **Moje podstawowe okienka Akcje** projektu do **Eksploratora rozwiązań**.  
  
## <a name="add-text-and-bookmarks-to-the-document"></a>Dodawanie tekstu i zakładki w dokumencie  
 W okienku Akcje wysyła do zakładki w dokumencie tekstowym. Projektowanie dokument, wpisz tekst do tworzenia podstawowej postaci.  
  
### <a name="to-add-text-to-your-document"></a>Aby dodać tekstu do dokumentu  
  
1.  W dokumencie programu Word, należy wpisać następujący tekst:  
  
     **21 marca 2008**  
  
     **Nazwa**  
  
     **Adres**  
  
     **To jest przykład okienka podstawowe działania w programie Word.**  
  
 Możesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli w dokumencie, przeciągając je z **przybornika** w programie Visual Studio lub za pomocą **zakładki** okno dialogowe w programie Word.  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>Aby dodać kontrolkę zakładki w dokumencie  
  
1.  Z **formanty Word** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> formantu do dokumentu.  
  
     **Dodaj formant zakładki** zostanie wyświetlone okno dialogowe.  
  
2.  Zaznacz słowo **nazwa**, bez wybierając znacznik akapitu i kliknij przycisk **OK**.  
  
    > [!NOTE]  
    >  Znak powinny być poza zakładki. Znaczniki akapitu nie są widoczne w dokumencie, kliknij przycisk **narzędzia** menu wskaż **narzędzia Microsoft Office Word** , a następnie kliknij przycisk **opcje**. Kliknij przycisk **widoku** , a następnie wybierz **znaczniki akapitów** pole wyboru w **znaczniki formatowania** sekcji **opcje** okno dialogowe.  
  
3.  W **właściwości** Zmień **nazwa** właściwość **Bookmark1** do **showName**.  
  
4.  Zaznacz słowo **adres**, bez zaznaczania znak akapitu.  
  
5.  Na **Wstaw** karty wstążki w **łącza** kliknij przycisk **zakładki**.  
  
6.  W **zakładki** okno dialogowe, typ **showAddress** w **zakładką** polu i kliknij przycisk **Dodaj**.  
  
## <a name="add-controls-to-the-actions-pane"></a>Dodawanie formantów do okienka Akcje  
 Projektowanie interfejsu w okienku Akcje, Dodaj formant okienka Akcje do projektu, a następnie dodaj formanty formularzy systemu Windows do formantu w okienku Akcje.  
  
### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolkę okienka Akcje  
  
1.  Wybierz **Moje podstawowe okienka Akcje** projektu w **Eksploratora rozwiązań**.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **formant okienka Akcje**, nazwa formantu **InsertTextControl,** i kliknij przycisk **Dodaj**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Aby dodać kontrolki formularza systemu Windows do formant okienka Akcje  
  
1.  Jeśli formant okienka Akcje nie jest widoczne w projektancie, kliknij dwukrotnie **InsertTextControl**.  
  
2.  Z **formanty standardowe** karcie **przybornika**, przeciągnij **etykiety** formant do formantu w okienku Akcje.  
  
3.  Zmień **tekst** właściwości formantu etykiety **nazwa**.  
  
4.  Dodaj **pole tekstowe** sterowania do formantu w okienku Akcje, a następnie Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**GetName**|  
    |**Rozmiar**|**130, 20**|  
  
5.  Dodaj drugi **etykiety** sterowania do formantu w okienku Akcje, a następnie zmień **tekst** właściwości **adres**.  
  
6.  Dodaj drugi **pole tekstowe** sterowania do formantu w okienku Akcje, a następnie Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**GetAddress**|  
    |**Akceptuje Return**|**True**|  
    |**Wiele linii**|**True**|  
    |**Rozmiar**|**130, 40**|  
  
7.  Dodaj **przycisk** sterowania do formantu w okienku Akcje, a następnie Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**addText**|  
    |**Tekst**|**Wstaw**|  
  
## <a name="add-code-to-insert-text-into-the-document"></a>Dodaj kod, aby wstawić tekst do dokumentu  
 W okienku akcji, pisanie kodu, który wstawia tekst z pola tekstowe do odpowiedniej <xref:Microsoft.Office.Tools.Word.Bookmark> formantów w dokumencie. Można użyć `Globals` klasy dostęp do formantów w dokumencie z kontrolkami w okienku akcji. Aby uzyskać więcej informacji, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Wstawianie tekstu w okienku Akcje w zakładki w dokumencie  
  
1.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń **addText** przycisku.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  W języku C# należy dodać obsługi zdarzenia kliknięcia przycisku. Możesz umieścić ten kod w `InsertTextControl` Konstruktor po wywołaniu `IntializeComponent`. Aby uzyskać informacje dotyczące tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="add-code-to-show-the-actions-pane"></a>Dodaj kod, aby wyświetlić w okienku Akcje  
 Aby wyświetlić w okienku Akcje, Dodaj formant, który został utworzony do kolekcji formantów.  
  
### <a name="to-show-the-actions-pane"></a>Aby wyświetlić w okienku Akcje  
  
1.  Tworzenie nowego wystąpienia kontrolki okienka akcji w `ThisDocument` klasy.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Dodaj następujący kod do <xref:Microsoft.Office.Tools.Word.Document.Startup> obsługi zdarzeń `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Przetestuj dokumencie, aby sprawdzić, czy w okienku Akcje otwiera po otwarciu dokumentu i że tekstu pisanego w polach tekstowych są wstawiane do zakładki, po kliknięciu przycisku.  
  
### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz **F5** do uruchomienia projektu.  
  
2.  Upewnij się, że widoczne jest okienko akcji.  
  
3.  Wpisz nazwę i adres do pól tekstowych w okienku Akcje, a następnie kliknij przycisk **Wstaw**.  
  
## <a name="next-steps"></a>Następne kroki  
 Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Utwórz okienko akcji w programie Excel. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie okienek akcji ze skoroszytami programu Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Powiązanie danych z kontrolkami w okienku Akcje. Aby uzyskać więcej informacji, zobacz [wskazówki: wiązanie danych do kontrolek okienku akcji programu Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Porady: Dodawanie okienek akcji do dokumentów programu Word lub skoroszyty programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Porady: Dodawanie okienek akcji do skoroszytów programu Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [Porady: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [BOOKMARK, formant:](../vsto/bookmark-control.md)  
  
  