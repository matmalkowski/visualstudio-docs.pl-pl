---
title: 'Wskazówki: Dodawanie formantów do dokumentów w czasie wykonywania w dodatku VSTO'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 74a136bfecf20fd496f97bedc2d871de041fe65b
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767355"
---
# <a name="walkthrough-add-controls-to-a-document-at-runtime-in-a-vsto-add-in"></a>Wskazówki: Dodawanie formantów do dokumentów w czasie wykonywania w dodatku VSTO
  Formanty można dodać do dowolnego otwartego dokumentu Microsoft Office Word za pomocą dodatku VSTO. W tym przewodniku pokazano, jak korzystanie ze Wstążki, aby umożliwić użytkownikom dodawanie <xref:Microsoft.Office.Tools.Word.Controls.Button> lub <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do dokumentu.  
  
 **Dotyczy:** informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla programu Word 2010. Aby uzyskać więcej informacji, zobacz [dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie nowego projektu dodatku VSTO programu Word.  
  
-   Udostępnia interfejs użytkownika (UI), aby dodać kontrolki do dokumentu.  
  
-   Dodawanie formantów do dokumentów w czasie wykonywania.  
  
-   Usuwanie kontrolek z dokumentu.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-a-new-word-add-in-project"></a>Utwórz nowy projekt dodatku programu Word  
 Rozpocznij od utworzenia projektu dodatku VSTO programu Word.  
  
### <a name="to-create-a-new-word-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO programu Word  
  
1.  Tworzenie projektów dodatku VSTO dla programu Word o nazwie **WordDynamicControls**. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Dodaj odwołanie do **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** zestawu. To odwołanie jest wymagane do programowane Dodawanie formantu formularzy systemu Windows do dokumentu w dalszej części tego przewodnika.  
  
## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Udostępniają interfejs użytkownika do dodawania formantów do dokumentu  
 Dodaj niestandardowy kartę na Wstążce w programie Word. Użytkownicy mogą wybrać pola wyboru na karcie do dodawania formantów do dokumentu.  
  
### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Aby zapewnić interfejsu użytkownika do dodawania formantów do dokumentu  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **wstążki (projektanta wizualnego)**.  
  
3.  Zmień nazwę nowego wstążki do **MyRibbon**i kliknij przycisk **Dodaj**.  
  
     **MyRibbon.cs** lub **MyRibbon.vb** plik zostanie otwarty w Projektancie Wstążki i wyświetla kartę domyślne i grupy.  
  
4.  W Projektancie Wstążki kliknij **grupa1** grupy.  
  
5.  W **właściwości** Zmień **etykiety** właściwość **grupa1** do **Dodaj formanty**.  
  
6.  Z **formantów wstążki pakietu Office** karcie **przybornika**, przeciągnij **wyboru** kontrolować na **grupa1**.  
  
7.  Kliknij przycisk **pole wyboru 1** aby go wybrać.  
  
8.  W **właściwości** okna, Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**addButtonCheckBox**|  
    |**Etykieta**|**Dodawanie przycisku**|  
  
9. Drugie pole wyboru, aby dodać **grupa1**, a następnie Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**addRichTextCheckBox**|  
    |**Etykieta**|**Dodawanie tekstu Rich Text formantu**|  
  
10. Projektant wstążki, kliknij dwukrotnie **Dodawanie przycisku**.  
  
     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Obsługi zdarzeń **Dodawanie przycisku** pola wyboru zostanie otwarty w edytorze kodu.  
  
11. Powrót do projektanta wstążki, a następnie kliknij dwukrotnie **Dodaj formant tekstu sformatowanego**.  
  
     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Obsługi zdarzeń **Dodaj formant tekstu sformatowanego** pola wyboru zostanie otwarty w edytorze kodu.  
  
 W dalszej części tego przewodnika zostaną dodane kodu do tych programów obsługi zdarzeń do dodawania i usuwania formantów w aktywnym dokumencie.  
  
## <a name="add-and-remove-controls-on-the-active-document"></a>Dodawanie i usuwanie kontrolek w aktywnym dokumencie  
 W kodzie dodatku VSTO muszą być konwertowane do aktywnego dokumentu <xref:Microsoft.Office.Tools.Word.Document> *element hosta* przed dodaniem formantu. Zarządzane formanty można dodać tylko do elementów hosta, które działają jak kontenery dla formantów w rozwiązaniach pakietu Office. W przypadku projektów dodatku VSTO obiekty hosta można utworzyć w czasie wykonywania za pomocą `GetVstoObject` metody.  
  
 Dodaj metody `ThisAddIn` klasy, który można wywołać, aby dodać lub usunąć <xref:Microsoft.Office.Tools.Word.Controls.Button> lub <xref:Microsoft.Office.Tools.Word.RichTextContentControl> w aktywnym dokumencie. W dalszej części tego przewodnika, należy wywołać tych metod z <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> programów obsługi zdarzeń pola wyboru na Wstążce.  
  
### <a name="to-add-and-remove-controls-on-the-active-document"></a>Dodawanie i usuwanie kontrolek w aktywnym dokumencie  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie *ThisAddIn.cs* lub *ThisAddIn.vb* można otworzyć pliku w edytorze kodu.  
  
2.  Dodaj następujący kod do `ThisAddIn` klasy. Ten kod deklaruje <xref:Microsoft.Office.Tools.Word.Controls.Button> i <xref:Microsoft.Office.Tools.Word.RichTextContentControl> obiektów, które reprezentują formantów, które zostaną dodane do dokumentu.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]  
  
3.  Dodaj następującą metodę do `ThisAddIn` klasy. Po kliknięciu przez użytkownika **Dodawanie przycisku** pole wyboru na Wstążce, ta metoda dodaje <xref:Microsoft.Office.Tools.Word.Controls.Button> do bieżącego zaznaczenia w dokumencie, jeśli pole wyboru jest zaznaczone lub usuwa <xref:Microsoft.Office.Tools.Word.Controls.Button> Jeśli pole wyboru jest wyczyszczone.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]  
  
4.  Dodaj następującą metodę do `ThisAddIn` klasy. Po kliknięciu przez użytkownika **Dodaj formant tekstu sformatowanego** pole wyboru na Wstążce, ta metoda dodaje <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do bieżącego zaznaczenia w dokumencie, jeśli pole wyboru jest zaznaczone lub usuwa <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Jeśli pole wyboru jest wyczyszczone.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]  
  
## <a name="remove-the-button-control-when-the-document-is-saved"></a>Usuwanie formantu przycisku po zapisaniu dokumentu  
 Formanty formularzy systemu Windows nie są zachowywane podczas dokumentu jest zapisane, a następnie zamknięte. Jednak otoki ActiveX dla każdego formantu pozostaje w dokumencie i obramowania tej otoki mogą być widoczne dla użytkowników końcowych, po otwarciu dokumentu. Istnieje kilka sposobów, aby wyczyścić utworzony dynamicznie formanty formularzy systemu Windows w dodatkach VSTO. W tym przewodniku można programistycznie usunąć <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolować po zapisaniu dokumentu.  
  
### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Aby usunąć formantu przycisku po zapisaniu dokumentu  
  
1.  W *ThisAddIn.cs* lub *ThisAddIn.vb* kodu pliku, dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda jest program obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeń. Jeśli został zapisany dokument <xref:Microsoft.Office.Tools.Word.Document> elementu hosta, który jest skojarzony z nim programu obsługi zdarzeń pobiera element hosta i usuwa <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolować, jeśli istnieje.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]  
  
2.  W języku C#, Dodaj następujący kod do `ThisAddIn_Startup` obsługi zdarzeń. Ten kod jest wymagany w języku C# do połączenia `Application_DocumentBeforeSave` obsługi zdarzeń z <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeń.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]  
  
## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Dodawanie i usuwanie formantów, gdy użytkownik kliknie pola wyboru na Wstążce  
 Na koniec zmodyfikuj <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> procedury obsługi zdarzeń pola wyboru dodane na Wstążce, aby dodać lub usunąć formanty w dokumencie.  
  
### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Aby dodać lub usunąć Określa, kiedy użytkownik kliknie pola wyboru na Wstążce  
  
1.  W *MyRibbon.cs* lub *MyRibbon.vb* kodu pliku, Zastąp wygenerowany `addButtonCheckBox_Click` i `addRichTextCheckBox_Click` procedury obsługi zdarzeń z następującym kodem. Ten kod ponownie definiuje te programy obsługi zdarzeń, aby wywołać `ToggleButtonOnDocument` i `ToggleRichTextControlOnDocument` metod, które zostały dodane do `ThisAddIn` klasa we wcześniejszej części tego przewodnika.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]  
  
## <a name="test-the-solution"></a>Testowanie rozwiązania  
 Dodawanie formantów do dokumentu, wybierając je z niestandardowych kartę na Wstążce. Podczas zapisywania dokumentu, <xref:Microsoft.Office.Tools.Word.Controls.Button> formantu zostanie usunięty.  
  
### <a name="to-test-the-solution"></a>Aby przetestować rozwiązania.  
  
1.  Naciśnij klawisz **F5** do uruchomienia projektu.  
  
2.  W aktywnym dokumencie, naciśnij klawisz **Enter** kilka razy, aby dodać nowe puste akapitów do dokumentu.  
  
3.  Wybierz pierwszym akapicie.  
  
4.  Kliknij przycisk **Add-Ins** kartę.  
  
5.  W **Dodaj formanty** kliknij przycisk **Dodawanie przycisku**.  
  
     Przycisk pojawia się w pierwszym akapicie.  
  
6.  Wybierz ostatni akapit.  
  
7.  W **Dodaj formanty** kliknij przycisk **Dodaj formant tekstu sformatowanego**.  
  
     Formant zawartości tekstu sformatowanego jest dodawana do ostatniego akapitu.  
  
8.  Zapisz dokument.  
  
     Przycisk zostanie usunięty z dokumentu.  
  
## <a name="next-steps"></a>Następne kroki  
 Dodatkowe informacje na informacje o formantach w dodatkach VSTO z tych tematów:  
  
-   Dla przykładu, który pokazuje, jak dodać wiele typów formantów do dokumentów w czasie wykonywania i Utwórz ponownie formantów, po otwarciu dokumentu, zobacz Word dodatku dynamicznej kontroli próbki w [Office development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md).  
  
-   Aby uzyskać wskazówki, który demonstruje sposób dodawanie formantów do arkusza za pomocą dodatku VSTO dla programu Excel, zobacz [wskazówki: dodawanie formantów do arkusza w czasie wykonywania w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwiązania programu Word](../vsto/word-solutions.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Utrwalanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Porady: dodawanie formantów formularzy systemu Windows do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Porady: dodawanie formantów zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  