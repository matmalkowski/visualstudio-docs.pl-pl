---
title: "Wskazówka: Synchronizacja niestandardowego okienka zadań z przyciskiem wstążki | Dokumentacja firmy Microsoft"
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
- custom task panes [Office development in Visual Studio], showing and hiding
- showing custom task panes
- Ribbon [Office development in Visual Studio], custom task panes
- toggle buttons [Office development in Visual Studio]
- custom task panes [Office development in Visual Studio], synchronizing with Ribbon button
- user interfaces [Office development in Visual Studio], custom task panes
- synchronization [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], showing and hiding
- custom task panes [Office development in Visual Studio], creating
- hiding custom task panes
- task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio], synchronizing with Ribbon button
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7368c580d2f00d929bdeefd11665e9f579af17f7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button"></a>Wskazówka: synchronizacja niestandardowego okienka zadań z przyciskiem wstążki
  Ten przewodnik przedstawia sposób tworzenia niestandardowego okienka zadań użytkowników można ukryć lub wyświetlić, klikając przycisk przełącznika na Wstążce. Należy zawsze tworzyć elementu interfejsu użytkownika, takie jak przycisk, które można kliknąć, aby wyświetlić lub ukryć niestandardowego okienka zadań, ponieważ aplikacje Microsoft Office nie umożliwiają domyślne użytkownikom na wyświetlanie lub ukrywanie niestandardowych okienek zadań.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Mimo że w tym przewodniku zastosowano programu Excel w szczególności, pojęcia dowodzą wskazówki mają zastosowanie do aplikacji, które są wymienione powyżej.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Projektowanie interfejsu użytkownika z niestandardowego okienka zadań.  
  
-   Dodawanie przycisku przełącznika do wstążki.  
  
-   Synchronizowanie przycisk przełącznika z niestandardowego okienka zadań.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Excel lub Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)].  
  
## <a name="creating-the-add-in-project"></a>Tworzenie projektu w  
 W tym kroku utworzysz projektów dodatku VSTO dla programu Excel.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Utwórz projekt dodatku programu Excel o nazwie **SynchronizeTaskPaneAndRibbon**, za pomocą szablonu projektu dodatek programu Excel. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Otwiera **ThisAddIn.cs** lub **ThisAddIn.vb** pliku kodu i dodaje **SynchronizeTaskPaneAndRibbon** projektu do **Eksplorator rozwiązań**.  
  
## <a name="adding-a-toggle-button-to-the-ribbon"></a>Dodawanie przycisku przełącznika do wstążki  
 Jednym z wytycznymi projektowania aplikacji pakietu Office jest użytkowników powinien zawsze mieć formantu interfejsu użytkownika aplikacji pakietu Office. Umożliwienie użytkownikom kontrolowania niestandardowego okienka zadań, można dodać przycisk przełączania wstążki, który pokazuje i ukrywa ją w okienku zadań. Aby utworzyć przycisk przełącznika, dodać **wstążki (projektanta wizualnego)** elementu do projektu. Projektant pomaga Dodaj formanty pozycji, ustaw właściwości kontrolki i obsługę zdarzeń formantu. Aby uzyskać więcej informacji, zobacz [projektanta wstążki](../vsto/ribbon-designer.md).  
  
#### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Aby dodać przycisk przełączania do wstążki  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **wstążki (projektanta wizualnego)**.  
  
3.  Zmień nazwę nowego wstążki do **ManageTaskPaneRibbon**i kliknij przycisk **Dodaj**.  
  
     **ManageTaskPaneRibbon.cs** lub **ManageTaskPaneRibbon.vb** plik zostanie otwarty w Projektancie Wstążki i wyświetla kartę domyślne i grupy.  
  
4.  W Projektancie Wstążki kliknij **grupa1**.  
  
5.  W **właściwości** ustaw **etykiety** właściwości **Menedżera okienka zadań**.  
  
6.  Z **formantów wstążki pakietu Office** karcie **przybornika**, przeciągnij **ToggleButton** na **Menedżera okienka zadań** grupy.  
  
7.  Kliknij przycisk **toggleButton1**.  
  
8.  W **właściwości** ustaw **etykiety** właściwości **Pokaż okienko zadań**.  
  
## <a name="designing-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań  
 Nie ma wizualnego projektanta dla niestandardowych okienek zadań, ale można zaprojektować kontrolkę użytkownika z układem, który ma. W dalszej części tego przewodnika kontrolki użytkownika zostaną dodane do niestandardowego okienka zadań.  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj kontrolkę użytkownika**.  
  
2.  W **Dodaj nowy element** okno dialogowe Zmień nazwę formantu użytkownika do **TaskPaneControl**i kliknij przycisk **Dodaj**.  
  
     Kontrola użytkownika zostanie otwarty w projektancie.  
  
3.  Z **formanty standardowe** karcie **przybornika**, przeciągnij **pole tekstowe** formantu do kontrolki użytkownika.  
  
## <a name="creating-the-custom-task-pane"></a>Tworzenie niestandardowego okienka zadań  
 Do uruchomienia dodatku VSTO, należy utworzyć niestandardowego okienka zadań, Dodaj kontrolkę użytkownika do okienka zadań w <xref:Microsoft.Office.Tools.AddIn.Startup> obsługi zdarzeń dodatku VSTO. Domyślnie niestandardowego okienka zadań nie będą widoczne. W dalszej części tego przewodnika należy dodać kodu, który będzie wyświetlanie lub ukrywanie okienka zadań, gdy użytkownik kliknie przycisk przełącznika dodanego do wstążki.  
  
#### <a name="to-create-the-custom-task-pane"></a>Aby utworzyć niestandardowego okienka zadań  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **Excel**.  
  
2.  Kliknij prawym przyciskiem myszy **ThisAddIn.cs** lub **ThisAddIn.vb** i kliknij przycisk **kod widoku**.  
  
3.  Dodaj następujący kod do `ThisAddIn` klasy. Ten kod deklaruje wystąpienia `TaskPaneControl` jako element członkowski `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]  
  
4.  Zastąp `ThisAddIn_Startup` obsługi zdarzeń z następującym kodem. Ten kod dodaje `TaskPaneControl` do obiektu `CustomTaskPanes` pola, ale nie są wyświetlane niestandardowego okienka zadań (domyślnie <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> właściwość <xref:Microsoft.Office.Tools.CustomTaskPane> jest klasa **false**). Kod Visual C# również dołącza program obsługi zdarzeń do <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzeń.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]  
  
5.  Dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda obsługuje <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzeń. Gdy użytkownik zamyka w okienku zadań, klikając **Zamknij** przycisk (X), tej aktualizacji metody stan przełącznik znajdującego się na Wstążce.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]  
  
6.  Dodaj następujące właściwości do `ThisAddIn` klasy. Ta właściwość opisuje prywatna `myCustomTaskPane1` obiektu do innych grup. W dalszej części tego przewodnika, można dodać kod `MyRibbon` klasy, która używa tej właściwości.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]  
  
## <a name="hiding-and-showing-the-custom-task-pane-by-using-the-toggle-button"></a>Wyświetlanie i ukrywanie niestandardowego okienka zadań za pomocą przycisku przełącznika  
 Ostatnim krokiem jest Dodaj kod, który wyświetla lub ukrywa niestandardowego okienka zadań, gdy użytkownik kliknie przycisk przełączania na Wstążce.  
  
#### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>Aby wyświetlić lub ukryć niestandardowego okienka zadań za pomocą przycisku przełącznika  
  
1.  Projektant wstążki, kliknij dwukrotnie **Pokaż okienko zadań** przycisk przełącznika.  
  
     Visual Studio automatycznie generuje program obsługi zdarzeń o nazwie `toggleButton1_Click`, która obsługuje <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> zdarzeń przycisk przełącznika. Visual Studio zostanie otwarte także **MyRibbon.cs** lub **MyRibbon.vb** plik w edytorze kodu.  
  
2.  Zastąp `toggleButton1_Click` obsługi zdarzeń z następującym kodem. Gdy użytkownik kliknie przycisk przełącznika, ten kod wyświetla lub ukrywa niestandardowego okienka zadań, w zależności od tego, czy naciśnięcie lub nie został naciśnięty przycisk przełącznika.  
  
     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]  
  
## <a name="testing-the-add-in"></a>Testowanie dodatku  
 Po uruchomieniu projekt zostanie otwarty bez wyświetlania niestandardowego okienka zadań. Przycisk przełączania na Wstążce, aby przetestować kod.  
  
#### <a name="to-test-your-vsto-add-in"></a>Aby przetestować użytkownika dodatku narzędzi VSTO  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
     Upewnij się, że, zostanie otwarty i **Add-Ins** zostanie wyświetlona karta na Wstążce.  
  
2.  Kliknij przycisk **Add-Ins** kartę na Wstążce.  
  
3.  W **Menedżera okienka zadań** kliknij przycisk **Pokaż okienko zadań** przycisk przełącznika.  
  
     Sprawdź w okienku zadań jest również wyświetlana, a ukryte po kliknięciu przycisku przełączania.  
  
4.  Gdy w okienku zadania jest widoczny, kliknij przycisk **Zamknij** przycisku (X) w rogu okienka zadań.  
  
     Sprawdź, czy przycisk przełącznika wydaje się nie być naciśnięty.  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz można dowiedzieć się więcej o sposobie tworzenia niestandardowych okienek zadań z tych tematów:  
  
-   Tworzenie niestandardowego okienka zadań w dodatku VSTO dla różnych aplikacji. Aby uzyskać więcej informacji o aplikacji, które obsługują niestandardowych okienek zadań, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).  
  
-   Automatyzowanie aplikacji z niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [wskazówki: automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Tworzenie niestandardowego okienka zadań dla każdej wiadomości e-mail, który jest otwarty w programie Outlook. Aby uzyskać więcej informacji, zobacz [wskazówki: wyświetlanie okienka niestandardowych zadań z wiadomościami E-Mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)   
 [Porady: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Wskazówki: Automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Wskazówki: Wyświetlanie niestandardowych okienek zadań z wiadomościami E-Mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)   
 [Wstążka — omówienie](../vsto/ribbon-overview.md)  
  
  