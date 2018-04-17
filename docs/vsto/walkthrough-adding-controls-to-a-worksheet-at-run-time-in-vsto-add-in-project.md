---
title: 'Wskazówki: Dodawanie formantów do arkusza w czasie wykonywania w VSTO dodatku projektu | Dokumentacja firmy Microsoft'
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
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47c647e2b3af6941f7b4a4d6f28eccfac2b31e2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>Przewodnik: dodawanie kontrolek do arkusza w czasie wykonywania w projekcie dodatku narzędzi VSTO
  Formanty można dodać do dowolnego Otwórz arkusz przy użyciu dodatku VSTO programu Excel. W tym przewodniku pokazano, jak korzystanie ze Wstążki, aby umożliwić użytkownikom dodawanie <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange>, a <xref:Microsoft.Office.Tools.Excel.ListObject> do arkusza. Aby uzyskać informacje, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **Dotyczy:** informacje w tym temacie dotyczą projektów dodatku VSTO dla programu Excel. Aby uzyskać więcej informacji, zobacz [dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Udostępnia interfejs użytkownika (UI) do dodawania formantów do arkusza.  
  
-   Dodawanie formantów do arkusza.  
  
-   Usuwanie kontrolek z arkusza.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## <a name="creating-a-new-excel-vsto-add-in-project"></a>Tworzenie nowego programu Excel VSTO dodatku projektu  
 Rozpocznij od utworzenia projektu dodatku VSTO programu Excel.  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO programu Excel  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], tworzenie projektów dodatku VSTO programu Excel o nazwie **ExcelDynamicControls**. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Dodaj odwołanie do **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** zestawu. To odwołanie jest wymagane do programowego dodawania kontrolki formularza systemu Windows do arkusza w dalszej części tego przewodnika.  
  
## <a name="providing-a-ui-to-add-controls-to-a-worksheet"></a>Udostępnia interfejs użytkownika do dodawania formantów do arkusza  
 Dodawanie kart niestandardowych do Wstążki programu Excel. Użytkownicy mogą wybrać pola wyboru na karcie do dodawania formantów do arkusza.  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Aby zapewnić interfejsu użytkownika do dodawania formantów do arkusza  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **wstążki (projektanta wizualnego)**, a następnie kliknij przycisk **Dodaj**.  
  
     Plik o nazwie **Ribbon1.cs** lub **Ribbon1.vb** zostanie otwarty w Projektancie Wstążki i wyświetla kartę domyślne i grupy.  
  
3.  Z **formantów wstążki pakietu Office** karcie **przybornika**, przeciągnij formant wyboru na **grupa1**.  
  
4.  Kliknij przycisk **pole wyboru 1** aby go wybrać.  
  
5.  W **właściwości** okna, Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**Przycisk**|  
    |**Etykieta**|**Przycisk**|  
  
6.  Drugie pole wyboru, aby dodać **grupa1**, a następnie Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**NamedRange**|  
    |**Etykieta**|**NamedRange**|  
  
7.  Trzecie pole wyboru, aby dodać **grupa1**, a następnie Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**ListObject**|  
    |**Etykieta**|**ListObject**|  
  
## <a name="adding-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza  
 Zarządzane formanty można dodać tylko do elementów hosta, które działają jak kontenery. Ponieważ projektów dodatku VSTO pracować z dowolnego otwartego skoroszytu, to dodatku VSTO konwertuje element hosta arkusza lub pobiera istniejący element hosta, przed dodaniem formantu. Dodawanie kodu do obsługi zdarzeń kliknięcia każdego formantu można wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> elementu hosta, który jest oparty na otwieranie arkusza. Następnie należy dodać <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange>, a <xref:Microsoft.Office.Tools.Excel.ListObject> na bieżące zaznaczenie w arkuszu.  
  
#### <a name="to-add-controls-to-a-worksheet"></a>Do dodawania formantów do arkusza  
  
1.  Projektant wstążki, kliknij dwukrotnie **przycisk**.  
  
     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Obsługi zdarzeń **przycisk** pola wyboru zostanie otwarty w edytorze kodu.  
  
2.  Zastąp `Button_Click` obsługi zdarzeń z następującym kodem.  
  
     Ten kod zawiera `GetVstoObject` metodę, aby pobrać element hosta, który reprezentuje pierwszego arkusza w skoroszycie, a następnie dodaje <xref:Microsoft.Office.Tools.Excel.Controls.Button> formant aktualnie zaznaczonej komórce.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]  
  
3.  W **Eksploratora rozwiązań**, wybierz Ribbon1.cs lub Ribbon1.vb.  
  
4.  Na **widoku** menu, kliknij przycisk **projektanta**.  
  
5.  Projektant wstążki, kliknij dwukrotnie **NamedRange**.  
  
6.  Zastąp `NamedRange_Click` obsługi zdarzeń z następującym kodem.  
  
     Ten kod zawiera `GetVstoObject` metodę, aby pobrać element hosta, który reprezentuje pierwszego arkusza w skoroszycie, a następnie definiuje <xref:Microsoft.Office.Tools.Excel.NamedRange> formant aktualnie zaznaczonej komórce lub komórek.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]  
  
7.  Projektant wstążki, kliknij dwukrotnie **ListObject**.  
  
8.  Zastąp `ListObject_Click` obsługi zdarzeń z następującym kodem.  
  
     Ten kod zawiera `GetVstoObject` metodę, aby pobrać element hosta, który reprezentuje pierwszego arkusza w skoroszycie, a następnie definiuje <xref:Microsoft.Office.Tools.Excel.ListObject> aktualnie zaznaczonej komórce lub komórek.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]  
  
9. Dodaj następujące instrukcje na początku pliku kodu wstążki.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]  
  
## <a name="removing-controls-from-the-worksheet"></a>Usuwanie kontrolek z arkusza  
 Formanty nie są zachowywane po zapisaniu i zamknięciu arkusza. Przed arkusz jest zapisywany lub konturu kontrolka będzie wyglądała ponownie otworzyć skoroszytu programowo należy usunąć wszystkie wygenerowanego formanty formularzy systemu Windows. Dodaj kod, aby <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzenie, które usuwa formanty formularzy systemu Windows z kolekcji formantów elementu wygenerowanego hosta. Aby uzyskać więcej informacji, zobacz [przechowywanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
#### <a name="to-remove-controls-from-the-worksheet"></a>Aby usunąć formantów z arkusza  
  
1.  W **Eksploratora rozwiązań**, wybierz ThisAddIn.cs lub ThisAddIn.vb.  
  
2.  Na **widoku** menu, kliknij przycisk **kod**.  
  
3.  Dodaj następującą metodę do klasy thisaddin —. Ten kod pobiera pierwszego arkusza w skoroszycie, a następnie używa `HasVstoObject` metodę, aby sprawdzić, czy arkusz ma obiekt arkusza wygenerowany. Jeśli obiekt arkusza wygenerowanego ma formantów, kod pobiera ten obiekt arkusza i iteruje po kolekcji formantów, usuwanie kontrolek.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]  
  
4.  W języku C#, należy utworzyć programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzeń. Możesz umieścić ten kod w `ThisAddIn_Startup` metody. Aby uzyskać więcej informacji o tworzeniu procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md). Zastąp `ThisAddIn_Startup` metodę z następującym kodem.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]  
  
## <a name="testing-the-solution"></a>Testowanie rozwiązania  
 Dodawanie formantów do arkusza, wybierając je z kart niestandardowych na Wstążce. Po zapisaniu arkusza tych kontrolek są usuwane.  
  
#### <a name="to-test-the-solution"></a>Aby przetestować rozwiązania.  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Wybierz dowolną komórkę w arkuszu 1.  
  
3.  Kliknij przycisk **Add-Ins** kartę.  
  
4.  W **grupa1** kliknij przycisk **przycisk**.  
  
     Przycisk pojawia się w zaznaczonej komórce.  
  
5.  Wybierz inną komórkę w arkuszu 1.  
  
6.  W **grupa1** kliknij przycisk **NamedRange**.  
  
     Nazwany zakres jest zdefiniowany dla wybranej komórki.  
  
7.  Wybierz serię komórek w arkuszu 1.  
  
8.  W **grupa1** kliknij przycisk **ListObject**.  
  
     Obiekt listy jest dodawany do zaznaczonych komórek.  
  
9. Zapisać arkusza.  
  
     Formanty dodane do Sheet1 — nie są wyświetlane.  
  
## <a name="next-steps"></a>Następne kroki  
 Użytkownik może dowiedzieć się więcej o formantów w projektów dodatku VSTO programu Excel z tego tematu:  
  
-   Aby dowiedzieć się więcej na temat zapisywania formantów do arkusza, zobacz VSTO programu Excel dodatku dynamicznej kontroli próbki w [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania programu Excel](../vsto/excel-solutions.md)   
 [Formanty formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [ListObject, kontrolka](../vsto/listobject-control.md)  
  
  