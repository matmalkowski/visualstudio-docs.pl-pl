---
title: "Wskazówki: Wyświetlanie niestandardowych okienek zadań z wiadomościami E-Mail w programie Outlook | Dokumentacja firmy Microsoft"
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
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
ms.assetid: 04943967-a7ef-4876-9584-84ada427e3f3
caps.latest.revision: "59"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b788a66eb95db5e46464048e134ab803d273d1ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook"></a>Wskazówki: wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook
  W tym przewodniku pokazano, jak wyświetlić unikatowego wystąpienia niestandardowego okienka zadań z każdej wiadomości e-mail, który jest tworzony i otwierany. Użytkownicy, można wyświetlić lub ukryć niestandardowego okienka zadań za pomocą przycisku na Wstążce każdej wiadomości e-mail.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Aby wyświetlić niestandardowego okienka zadań z wielu Eksploratora lub Inspektora systemu windows, należy utworzyć wystąpienia niestandardowego okienka zadań dla każdego okna, który jest otwarty. Aby uzyskać więcej informacji o zachowaniu niestandardowych okienek zadań w programie Outlook w systemie windows, temacie [niestandardowych okienek zadań](../vsto/custom-task-panes.md).  
  
> [!NOTE]  
>  Ten przewodnik przedstawia informacje o kodu w dodatku VSTO w sekcjach mała, aby ułatwić omówienia logiki kod.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Projektowanie interfejsu użytkownika (UI) niestandardowego okienka zadań.  
  
-   Tworzenie niestandardowego interfejsu użytkownika wstążki.  
  
-   Wyświetlanie niestandardowy interfejs użytkownika wstążki z wiadomościami e-mail.  
  
-   Tworzenie klasy do zarządzania systemu windows inspektora i niestandardowych okienek zadań.  
  
-   Inicjowanie i oczyszczanie zasobów używanych przez dodatku VSTO.  
  
-   Synchronizowanie przycisk przełączania wstążki z niestandardowego okienka zadań.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] lub programu Microsoft Outlook 2010.  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: Użyj okienka zadań w programie Outlook?](http://go.microsoft.com/fwlink/?LinkID=130309).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Niestandardowe okienka zadań są implementowane w dodatkach VSTO. Rozpocznij od utworzenia projektu dodatku VSTO dla programu Outlook.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Utwórz **dodatek programu Outlook** projektu o nazwie **OutlookMailItemTaskPane**. Użyj **dodatek programu Outlook** szablonu projektu. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Otwiera **ThisAddIn.cs** lub **ThisAddIn.vb** pliku kodu i dodaje **OutlookMailItemTaskPane** projektu do **Eksploratora rozwiązań**.  
  
## <a name="designing-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań  
 Nie jest wizualnego projektanta dla niestandardowych okienek zadań, ale można zaprojektować kontrolkę użytkownika przy użyciu interfejsu użytkownika ma. Niestandardowego okienka zadań w tym dodatku VSTO ma prosty interfejs użytkownika, który zawiera <xref:System.Windows.Forms.TextBox> formantu. W dalszej części tego przewodnika kontrolki użytkownika zostaną dodane do niestandardowego okienka zadań.  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań  
  
1.  W **Eksploratora rozwiązań**, kliknij przycisk **OutlookMailItemTaskPane** projektu.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj kontrolkę użytkownika**.  
  
3.  W **Dodaj nowy element** okno dialogowe Zmień nazwę formantu użytkownika do **TaskPaneControl**, a następnie kliknij przycisk **Dodaj**.  
  
     Kontrola użytkownika zostanie otwarty w projektancie.  
  
4.  Z **formanty standardowe** karcie **przybornika**, przeciągnij **pole tekstowe** formantu do kontrolki użytkownika.  
  
## <a name="designing-the-user-interface-of-the-ribbon"></a>Projektowanie interfejsu użytkownika wstążki  
 Jest jednym z celów tego dodatku VSTO umożliwić użytkownikom sposób, aby ukryć lub wyświetlić niestandardowego okienka zadań na Wstążce każdej wiadomości e-mail. Zapewnia interfejs użytkownika, należy utworzyć niestandardowego interfejsu użytkownika wstążki, który przedstawia przycisk przełącznika, który można kliknąć, aby wyświetlić lub ukryć niestandardowego okienka zadań.  
  
#### <a name="to-create-a-custom-ribbon-ui"></a>Aby utworzyć niestandardowy interfejs użytkownika wstążki  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **wstążki (projektanta wizualnego)**.  
  
3.  Zmień nazwę nowego wstążki do **ManageTaskPaneRibbon**i kliknij przycisk **Dodaj**.  
  
     **ManageTaskPaneRibbon.cs** lub **ManageTaskPaneRibbon.vb** plik zostanie otwarty w Projektancie Wstążki i wyświetla kartę domyślne i grupy.  
  
4.  W Projektancie Wstążki kliknij **grupa1**.  
  
5.  W **właściwości** ustaw **etykiety** właściwości **Menedżera okienka zadań**.  
  
6.  Z **formantów wstążki pakietu Office** karcie **przybornika**, przeciągnij formant ToggleButton na **Menedżera okienka zadań** grupy.  
  
7.  Kliknij przycisk **toggleButton1**.  
  
8.  W **właściwości** ustaw **etykiety** właściwości **Pokaż okienko zadań**.  
  
## <a name="display-the-custom-ribbon-user-interface-with-e-mail-messages"></a>Wyświetlanie interfejsu użytkownika niestandardowa Wstążka z wiadomościami E-Mail  
 Niestandardowego okienka zadań utworzone w tym przewodniku zaprojektowano w celu pojawiają się tylko z Inspektora systemu windows, które zawierają wiadomości e-mail. W związku z tym można ustawić właściwości, aby wyświetlić niestandardowego interfejsu użytkownika wstążki tylko z tych okien.  
  
#### <a name="to-display-the-custom-ribbon-ui-with-e-mail-messages"></a>Aby wyświetlić niestandardowy interfejs użytkownika wstążki z wiadomościami e-mail  
  
1.  W Projektancie Wstążki kliknij **ManageTaskPaneRibbon** wstążki.  
  
2.  W **właściwości** okna, kliknij przycisk Dalej, aby wyświetlić listę listy rozwijanej **RibbonType**i wybierz **Microsoft.Outlook.Mail.Compose** i  **Microsoft.Outlook.Mail.Read**.  
  
## <a name="creating-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Tworzenie klasy do zarządzania systemu Windows inspektora i niestandardowych okienek zadań  
 Istnieje kilka przypadków, w których dodatku VSTO musi zidentyfikować które niestandardowego okienka zadań jest skojarzony z określonym wiadomości. Te przypadki są następujące:  
  
-   Gdy użytkownik zamyka wiadomości e-mail. W takim przypadku dodatku VSTO należy usunąć odpowiednie niestandardowego okienka zadań do zapewnienia, że zasoby używane przez dodatku VSTO oczyścić poprawnie.  
  
-   Gdy użytkownik zamyka niestandardowego okienka zadań. W takim przypadku dodatku VSTO należy zaktualizować stan przycisku przełącznika na Wstążce w wiadomości e-mail.  
  
-   Gdy użytkownik kliknie przycisk przełączania na Wstążce. W takim przypadku dodatku VSTO musi ukryć lub wyświetlić odpowiedniego okienka zadań.  
  
 Aby włączyć dodatku VSTO do śledzenia które niestandardowego okienka zadań jest skojarzony z każdej wiadomości e-mail otwarte, tworzenie niestandardowej klasy, która opakowuje pary <xref:Microsoft.Office.Interop.Outlook.Inspector> i <xref:Microsoft.Office.Tools.CustomTaskPane> obiektów. Ta klasa tworzy nowy obiekt w okienku zadania niestandardowego dla każdej wiadomości e-mail, a następnie usuwa niestandardowego okienka zadań, gdy odpowiednia wiadomość e-mail jest zamknięty.  
  
#### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Aby utworzyć klasę do zarządzania systemu windows inspektora i niestandardowych okienek zadań  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisAddIn.cs** lub **ThisAddIn.vb** pliku, a następnie kliknij przycisk **kod widoku**.  
  
2.  Dodaj następujące instrukcje na początku pliku.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]  
  
3.  Dodaj następujący kod do **ThisAddIn.cs** lub **ThisAddIn.vb** pliku poza `ThisAddIn` klasy (Visual C#, Dodaj ten kod wewnątrz `OutlookMailItemTaskPane` przestrzeni nazw). `InspectorWrapper` Klasa zarządza para <xref:Microsoft.Office.Interop.Outlook.Inspector> i <xref:Microsoft.Office.Tools.CustomTaskPane> obiektów. Definicja tej klasy w poniższych krokach zostanie ukończona.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]  
  
4.  Dodaj następujący Konstruktor po kodzie dodanym w poprzednim kroku. Ten konstruktor tworzy i inicjuje nowego niestandardowego okienka zadań skojarzonego z <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, który jest przekazywany w. W języku C# konstruktora dołącza również procedury obsługi zdarzeń do <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> zdarzenie <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektu i <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzenie <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]  
  
5.  Dodaj następującą metodę po kodzie dodanym w poprzednim kroku. Ta metoda jest program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzenie <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu, który jest zawarty w `InspectorWrapper` klasy. Ten kod aktualizuje stan przycisku przełącznika zawsze, gdy użytkownik otwiera lub zamyka niestandardowego okienka zadań.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]  
  
6.  Dodaj następującą metodę po kodzie dodanym w poprzednim kroku. Ta metoda jest program obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> zdarzenie <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, który zawiera do bieżącej wiadomości e-mail. Program obsługi zdarzeń zwalnia zasoby, gdy wiadomość e-mail jest zamknięty. Program obsługi zdarzeń spowoduje również usunięcie bieżącego niestandardowego okienka zadań z `CustomTaskPanes` kolekcji. Pomaga to zapobiec wielu wystąpień niestandardowego okienka zadań, po otwarciu dalej wiadomości e-mail.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]  
  
7.  Dodaj następujący kod po kodzie dodanym w poprzednim kroku. W dalszej części tego przewodnika ta właściwość będzie wywoływać z metody niestandardowego interfejsu użytkownika wstążki, aby wyświetlić lub ukryć niestandardowego okienka zadań.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]  
  
## <a name="initializing-and-cleaning-up-resources-used-by-the-add-in"></a>Inicjowanie i oczyszczanie zasobów używanych przez dodatek  
 Dodaj kod, aby `ThisAddIn` klasy zainicjować dodatku VSTO po załadowaniu go, a także aby wyczyścić zasoby używane przez dodatku VSTO, gdy jest zwolniony. Należy zainicjować dodatku VSTO poprzez ustawienie programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzeń i przekazując wszystkie istniejące wiadomości e-mail, aby ten program obsługi zdarzeń. Gdy dodatku VSTO jest zwolniony, odłącz programu obsługi zdarzeń, a następnie wyczyścić obiektów używanych przez dodatku VSTO.  
  
#### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>Inicjowanie i oczyszczanie zasobów używanych przez dodatku narzędzi VSTO  
  
1.  W **ThisAddIn.cs** lub **ThisAddIn.vb** plików, zlokalizować definicji `ThisAddIn` klasy.  
  
2.  Dodaj następujące deklaracje `ThisAddIn` klasy:  
  
    -   `inspectorWrappersValue` Pole zawiera wszystkie <xref:Microsoft.Office.Interop.Outlook.Inspector> i `InspectorWrapper` obiektów, które są zarządzane przez dodatku VSTO.  
  
    -   `inspectors` Pola obsługuje odwołania do kolekcji inspektora windows w bieżącym wystąpieniu programu Outlook. To odwołanie uniemożliwia zwolnić pamięć, który zawiera program obsługi zdarzeń dla modułu zbierającego elementy bezużyteczne <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzenie, które będą zadeklarować w następnym kroku.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]  
  
3.  Zastąp `ThisAddIn_Startup` metodę z następującym kodem. Ten kod dołącza program obsługi zdarzeń do <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzenia i przekazuje co istniejące <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt do obsługi zdarzeń. Jeśli użytkownik załaduje dodatku VSTO po Outlook jest już uruchomiona, w dodatku VSTO używa tych informacji do tworzenia niestandardowych okienek zadań dla wszystkich wiadomości e-mail, które są już otwarte.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]
     [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]  
  
4.  Zastąp `ThisAddIn_ShutDown` metodę z następującym kodem. Ten kod odłącza <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> obsługi zdarzeń i czyści obiektów używanych przez dodatku VSTO.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]
     [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]  
  
5.  Dodaj następujące <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> program obsługi zdarzeń do `ThisAddIn` klasy. Jeśli nowy <xref:Microsoft.Office.Interop.Outlook.Inspector> zawiera wiadomości e-mail, ta metoda tworzy wystąpienie nowego `InspectorWrapper` obiektu relacji między wiadomości e-mail i odpowiednie okienka zadań zarządzania.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]
     [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]  
  
6.  Dodaj następujące właściwości do `ThisAddIn` klasy. Ta właściwość opisuje prywatna `inspectorWrappersValue` pole dla kodu poza `ThisAddIn` klasy.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]
     [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 Skompiluj projekt, aby upewnić się, że skompilowany bez błędów.  
  
#### <a name="to-build-your-project"></a>Aby utworzyć projekt  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **OutlookMailItemTaskPane** projektu, a następnie kliknij przycisk **kompilacji**. Upewnij się, że projekt skompiluje się bez błędów.  
  
## <a name="synchronizing-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Synchronizowanie przycisk przełączania wstążki z niestandardowego okienka zadań  
 Przycisk przełączania będzie wyświetlana jest wciśnięty, gdy jest widoczny w okienku zadań i pojawiał się być nie wciśnięty, gdy w okienku zadań jest ukryta. Aby zsynchronizować stan przycisku z niestandardowego okienka zadań, należy zmodyfikować <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> obsługi zdarzeń przycisk przełącznika.  
  
#### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Aby zsynchronizować niestandardowego okienka zadań z przycisku przełącznika  
  
1.  Projektant wstążki, kliknij dwukrotnie **Pokaż okienko zadań** przycisk przełącznika.  
  
     Visual Studio automatycznie generuje program obsługi zdarzeń o nazwie `toggleButton1_Click`, która obsługuje <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> zdarzeń przycisk przełącznika. Visual Studio zostanie otwarte także **ManageTaskPaneRibbon.cs** lub **ManageTaskPaneRibbon.vb** plik w edytorze kodu.  
  
2.  Dodaj następujące instrukcje na początku **ManageTaskPaneRibbon.cs** lub **ManageTaskPaneRibbon.vb** pliku.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]  
  
3.  Zastąp `toggleButton1_Click` obsługi zdarzeń z następującym kodem. Gdy użytkownik kliknie przycisk przełącznika, ta metoda ukrywa lub wyświetla niestandardowego okienka zadań, która jest skojarzona z bieżącym oknie Inspektora.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]  
  
## <a name="testing-the-project"></a>Testowanie projektu  
 Po rozpoczęciu debugowania projektu, zostanie otwarty program Outlook i dodatku VSTO został załadowany. Dodatku VSTO Wyświetla unikatowego wystąpienia niestandardowego okienka zadań z każdej wiadomości e-mail, który jest otwarty. Utwórz kilka nowych wiadomości e-mail do testowania kodu.  
  
#### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO  
  
1.  Naciśnij F5.  
  
2.  W programie Outlook, kliknij przycisk **nowy** można utworzyć nowej wiadomości e-mail.  
  
3.  Na Wstążce wiadomości e-mail, kliknij przycisk **Add-Ins** , a następnie kliknij pozycję **Pokaż okienko zadań** przycisku.  
  
     Upewnij się, że okienka zadań z tytułem **okienko zadań** zostanie wyświetlony z wiadomości e-mail.  
  
4.  W okienku zadań wpisz **pierwszego okienka zadań** w polu tekstowym.  
  
5.  Zamknij w okienku zadań.  
  
     Sprawdź, czy stan **Pokaż okienko zadań** przycisku zmienia się tak, aby nie jest wciśnięty.  
  
6.  Kliknij przycisk **Pokaż okienko zadań** przycisk ponownie.  
  
     Sprawdź, czy w okienku zadań otwiera i pola tekstowego będzie nadal zawiera ciąg **pierwszego okienka zadań**.  
  
7.  W programie Outlook, kliknij przycisk **nowy** utworzyć drugi wiadomości e-mail.  
  
8.  Na Wstążce wiadomości e-mail, kliknij przycisk **Add-Ins** , a następnie kliknij pozycję **Pokaż okienko zadań** przycisku.  
  
     Upewnij się, że okienka zadań z tytułem **okienko zadań** zostanie wyświetlony z wiadomości e-mail, a pole tekstowe, w tym okienku zadania jest pusty.  
  
9. W okienku zadań wpisz **drugi okienka zadań** w polu tekstowym.  
  
10. Zmień fokus do pierwszej wiadomości e-mail.  
  
     Sprawdź, czy w okienku zadań, który jest skojarzony z tym wiadomości e-mail, nadal wyświetlany **pierwszego okienka zadań** w polu tekstowym.  
  
 Ten dodatek VSTO obsługuje także więcej zaawansowanych scenariuszy, których można spróbować. Na przykład przetestować zachowanie podczas wyświetlania wiadomości e-mail przy użyciu **następnego elementu** i **poprzedniego elementu** przycisków. Można także przetestować zachowanie, gdy zwolnienie dodatku VSTO, otwórz kilka wiadomości e-mail, a następnie ponowne załadowanie dodatku VSTO.  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz można dowiedzieć się więcej o sposobie tworzenia niestandardowych okienek zadań z tych tematów:  
  
-   Tworzenie niestandardowego okienka zadań w dodatku VSTO dla różnych aplikacji. Aby uzyskać więcej informacji o aplikacji, które obsługują niestandardowych okienek zadań, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).  
  
-   Automatyzowanie aplikacji pakietu Microsoft Office przy użyciu niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [wskazówki: automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Utwórz przycisk na Wstążce w programie Excel, który może służyć do Ukryj lub Wyświetl niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [wskazówki: synchronizacja niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)   
 [Porady: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Wskazówki: Automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Wskazówka: Synchronizacja niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)   
 [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  