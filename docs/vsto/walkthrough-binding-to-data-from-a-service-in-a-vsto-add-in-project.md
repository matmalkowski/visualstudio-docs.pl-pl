---
title: 'Wskazówki: Powiązanie z danymi z usług w VSTO dodatku projektu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a89b9455051031b3faa0a44102f2fe97dca97d89
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project"></a>Wskazówki: Powiązanie z danymi z usług w projekcie dodatku narzędzi VSTO
  Dane można powiązać z formanty hosta w projektów dodatku VSTO. W tym przewodniku pokazano, jak dodawanie formantów do dokumentu programu Microsoft Office Word, powiązanie formantów danych pobranych z usługi zawartość w witrynie MSDN i reagowania na zdarzenia w czasie wykonywania.  
  
 **Dotyczy:** informacje w tym temacie dotyczą projektów na poziomie aplikacji dla programu Word 2010. Aby uzyskać więcej informacji, zobacz [dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie <xref:Microsoft.Office.Tools.Word.RichTextContentControl> sterowania na dokument w czasie wykonywania.  
  
-   Powiązanie <xref:Microsoft.Office.Tools.Word.RichTextContentControl> formantu danych z usługi sieci Web.  
  
-   Odpowiada na żądania <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> zdarzenie <xref:Microsoft.Office.Tools.Word.RichTextContentControl> formantu.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-a-new-project"></a>Tworzenie nowego projektu  
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO programu Word.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektów dodatku VSTO programu Word o nazwie **usługi zawartość MTPS**, za pomocą Visual Basic lub C#.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otworzy `ThisAddIn.vb` lub `ThisAddIn.cs` plików i dodaje projekt do **Eksploratora rozwiązań**.  
  
## <a name="adding-a-web-service"></a>Dodawanie usługi sieci Web  
 Użyj usługi sieci Web o nazwie usługi zawartość MTPS w ramach tego przewodnika. Ta usługa sieci Web zwraca informacje z określonym artykuł w witrynie MSDN w postaci ciągu XML lub zwykłego tekstu. Nowsze kroku przedstawiono sposób wyświetlania zwróconych informacji w formancie zawartości.  
  
#### <a name="to-add-the-mtps-content-service-to-the-project"></a>Aby dodać usługę zawartość MTPS do projektu  
  
1.  Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.  
  
2.  W **Kreator konfiguracji źródła danych**, kliknij przycisk **usługi**, a następnie kliknij przycisk **dalej**.  
  
3.  W **adres** wpisz następujący adres URL:  
  
     **http://services.msdn.microsoft.com/ContentServices/ContentService.asmx**  
  
4.  Kliknij przycisk **Przejdź**.  
  
5.  W **Namespace** wpisz **ContentService**i kliknij przycisk **OK**.  
  
6.  W **Kreatora dodawania odwołania** okno dialogowe, kliknij przycisk **Zakończ**.  
  
## <a name="adding-a-content-control-and-binding-to-data-at-run-time"></a>Dodawanie zawartości formantu i powiązania danych w czasie wykonywania  
 W dodatku VSTO projektów Dodaj i powiązanie formantów w czasie wykonywania. W ramach tego przewodnika skonfiguruj formantu zawartości do pobierania danych z usługi sieci Web, gdy użytkownik kliknie wewnątrz formantu.  
  
#### <a name="to-add-a-content-control-and-bind-to-data"></a>Aby dodać kontrolkę zawartości i powiązanie z danymi  
  
1.  W `ThisAddIn` klasy, Zadeklaruj zmienne dla usługi zawartości MTPS, formantu zawartości i powiązania danych.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]  
  
2.  Dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda tworzy formantu zawartości na początku aktywny dokument.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]  
  
3.  Dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda inicjuje obiektów niezbędnych do utworzenia i Wyślij żądanie do usługi sieci Web.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]  
  
4.  Utwórz program obsługi zdarzeń do pobrania dokumentu biblioteki MSDN Library o zawartości kontrolki, gdy użytkownik kliknie wewnątrz zawartości kontroli i powiązać dane do formantu zawartości.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]  
  
5.  Wywołanie `AddRichTextControlAtRange` i `InitializeServiceObjects` metody `ThisAddIn_Startup` metody. Dla programistów C# Dodaj program obsługi zdarzeń.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]  
  
## <a name="testing-the-add-in"></a>Testowanie dodatku  
 Po otwarciu programu Word, <xref:Microsoft.Office.Tools.Word.RichTextContentControl> formant jest widoczny. Tekst w kontroli zmieni się po kliknięciu wewnątrz niej.  
  
#### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO  
  
1.  Naciśnij klawisz **F5**.  
  
2.  Kliknij wewnątrz formantu zawartości.  
  
     Informacje są pobierane z usługi zawartości MTPS i wyświetlany w formancie zawartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  