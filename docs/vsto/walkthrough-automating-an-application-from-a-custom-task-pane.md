---
title: 'Wskazówki: Zautomatyzować aplikacji z niestandardowego okienka zadań'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7af399ca55c1fc2355da508662fe67314a519070
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768082"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Wskazówki: Zautomatyzować aplikacji z niestandardowego okienka zadań
  Ten przewodnik przedstawia sposób tworzenia niestandardowego okienka zadań który automatyzuje programu PowerPoint. Niestandardowego okienka zadań wstawia daty do slajdu, gdy użytkownik kliknie <xref:System.Windows.Forms.MonthCalendar> formant, który znajduje się na niestandardowego okienka zadań.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Mimo że w tym przewodniku zastosowano PowerPoint, w szczególności, pojęcia dowodzą przewodnika mają zastosowanie do aplikacji, które są wymienione powyżej.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Projektowanie interfejsu użytkownika niestandardowego okienka zadań.  
  
-   Automatyzowanie programu PowerPoint z niestandardowego okienka zadań.  
  
-   Wyświetlanie niestandardowego okienka zadań w programie PowerPoint.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft PowerPoint 2010 lub [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].  
  
## <a name="create-the-add-in-project"></a>Utwórz projekt dodatku  
 Pierwszym krokiem jest do tworzenia projektów dodatku VSTO dla programu PowerPoint.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektów dodatku VSTO dla programu PowerPoint o nazwie **MyAddIn**, za pomocą szablonu projektu dodatku programu PowerPoint. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera **ThisAddIn.cs** lub **ThisAddIn.vb** pliku kodu i dodaje **MyAddIn** projektu do **Eksploratora rozwiązań**.  
  
## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań  
 Nie ma wizualnego projektanta dla niestandardowych okienek zadań, ale można zaprojektować kontrolkę użytkownika z układem, który ma. W dalszej części tego przewodnika kontrolki użytkownika zostaną dodane do niestandardowego okienka zadań.  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj kontrolkę użytkownika**.  
  
2.  W **Dodaj nowy element** okno dialogowe Zmień nazwę formantu użytkownika do **MyUserControl**i kliknij przycisk **Dodaj**.  
  
     Kontrola użytkownika zostanie otwarty w projektancie.  
  
3.  Z **formanty standardowe** karcie **przybornika**, przeciągnij **MonthCalendar** formantu do kontrolki użytkownika.  
  
     Jeśli **MonthCalendar** formantu jest większy niż powierzchnię projektu kontrolki użytkownika, rozmiar formantu użytkownika w celu dopasowania **MonthCalendar** formantu.  
  
## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Automatyzowanie programu PowerPoint z niestandardowego okienka zadań  
 Celem dodatku VSTO jest zawiesić wybrana data pierwszego slajdu aktywnej prezentacji. Użyj <xref:System.Windows.Forms.MonthCalendar.DateChanged> zdarzeń formantu, aby dodać wybrana data on zmianie.  
  
### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Aby zautomatyzować PowerPoint z niestandardowego okienka zadań  
  
1.  W projektancie, kliknij dwukrotnie <xref:System.Windows.Forms.MonthCalendar> formantu.  
  
     **MyUserControl.cs** lub **MyUserControl.vb** plik zostanie otwarta, a program obsługi zdarzeń dla <xref:System.Windows.Forms.MonthCalendar.DateChanged> jest tworzone zdarzenie.  
  
2.  Dodaj następujący kod na początku pliku. Ten kod tworzy aliasów <xref:Microsoft.Office.Core> i <xref:Microsoft.Office.Interop.PowerPoint> przestrzeni nazw.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]  
  
3.  Dodaj następujący kod do `MyUserControl` klasy. Ten kod deklaruje <xref:Microsoft.Office.Interop.PowerPoint.Shape> obiektu jako element członkowski `MyUserControl`. W następnym kroku zostanie ona użyta <xref:Microsoft.Office.Interop.PowerPoint.Shape> można dodać pola tekstowego slajd w aktywnej prezentacji.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]  
  
4.  Zastąp `monthCalendar1_DateChanged` obsługi zdarzeń z następującym kodem. Ten kod dodaje pole tekstowe do pierwszego slajdu aktywnej prezentacji, a następnie dodanie aktualnie zaznaczona data w polu tekstowym. Ten kod zawiera `Globals.ThisAddIn` obiekt dostępu do modelu obiektu programu PowerPoint.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]  
  
5.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyAddIn** projektu, a następnie kliknij przycisk **kompilacji**. Upewnij się, że projekt tworzy się bez błędów.  
  
## <a name="display-the-custom-task-pane"></a>Wyświetlanie niestandardowego okienka zadań  
 Aby wyświetlić niestandardowego okienka zadań uruchomienia dodatku VSTO, Dodaj kontrolkę użytkownika do okienka zadań w <xref:Microsoft.Office.Tools.AddIn.Startup> obsługi zdarzeń dodatku VSTO.  
  
### <a name="to-display-the-custom-task-pane"></a>Aby wyświetlić niestandardowego okienka zadań  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **PowerPoint**.  
  
2.  Kliknij prawym przyciskiem myszy **ThisAddIn.cs** lub **ThisAddIn.vb** i kliknij przycisk **kod widoku**.  
  
3.  Dodaj następujący kod do `ThisAddIn` klasy. Ten kod deklaruje wystąpienia `MyUserControl` i <xref:Microsoft.Office.Tools.CustomTaskPane> jako elementy członkowskie `ThisAddIn` klasy.  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]  
  
4.  Zastąp `ThisAddIn_Startup` obsługi zdarzeń z następującym kodem. Ten kod tworzy nową <xref:Microsoft.Office.Tools.CustomTaskPane> przez dodanie `MyUserControl` do obiektu `CustomTaskPanes` kolekcji. Kod są również wyświetlane w okienku zadań.  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]  
  
## <a name="test-the-add-in"></a>Testowanie dodatku  
 Po uruchomieniu projektu, otwierania i dodatku VSTO Wyświetla niestandardowego okienka zadań. Kliknij przycisk <xref:System.Windows.Forms.MonthCalendar> formantu do testowania kodu.  
  
### <a name="to-test-your-vsto-add-in"></a>Aby przetestować użytkownika dodatku narzędzi VSTO  
  
1.  Naciśnij klawisz **F5** do uruchomienia projektu.  
  
2.  Upewnij się, że niestandardowego okienka zadań jest widoczny.  
  
3.  Kliknij datę w <xref:System.Windows.Forms.MonthCalendar> formantu w okienku zadań.  
  
     Daty są wstawiane do pierwszego slajdu aktywnej prezentacji.  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz można dowiedzieć się więcej o sposobie tworzenia niestandardowych okienek zadań z tych tematów:  
  
-   Tworzenie niestandardowego okienka zadań w dodatku VSTO dla różnych aplikacji. Aby uzyskać więcej informacji o aplikacji, które obsługują niestandardowych okienek zadań, zobacz [niestandardowego okienka zadań](../vsto/custom-task-panes.md).  
  
-   Utwórz przycisk wstążki, który może służyć do Ukryj lub Wyświetl niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [wskazówki: Synchronizowanie niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
-   Tworzenie niestandardowego okienka zadań dla każdej wiadomości e-mail, który jest otwarty w programie Outlook. Aby uzyskać więcej informacji, zobacz [wskazówki: wyświetlanie niestandardowych okienek zadań z wiadomości e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)   
 [Porady: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Wskazówki: Synchronizowanie niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Wskazówki: Wyświetlanie niestandardowych okienek zadań z wiadomości e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  