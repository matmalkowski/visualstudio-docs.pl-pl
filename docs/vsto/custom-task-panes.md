---
title: Niestandardowe okienka zadań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: acbe91b0a7150ac3a04f9a0b33c8b95d371caf53
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="custom-task-panes"></a>Niestandardowe okienka zadań
  Okienka zadań są panele interfejsu użytkownika, które są zazwyczaj zadokowane po jednej stronie okna w aplikacji pakietu Microsoft Office. Niestandardowe okienka zadań zapewniają sposób utworzyć własny okienka zadań i użytkownikom interfejs znany dostęp do funkcji tego rozwiązania. Na przykład interfejs może zawierać kontrolki, których uruchamianie kodu w celu modyfikowania dokumentów ani nie wyświetlają danych ze źródła danych.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Niestandardowego okienka zadań różni się w okienku Akcje. W okienku Akcje jest częścią dostosowań na poziomie dokumentu dla programu Microsoft Office Word i Microsoft Office Excel. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).  
  
## <a name="benefits-of-custom-task-panes"></a>Korzyści wynikające z niestandardowych okienek zadań  
 Niestandardowe okienka zadań umożliwiają integrowanie funkcje interfejsu użytkownika znane. Niestandardowego okienka zadań można szybko utworzyć za pomocą narzędzi Visual Studio.  
  
### <a name="familiar-user-interface"></a>Interfejs użytkownika znanych  
 Użytkownicy aplikacji w pakiecie Microsoft Office system znają już przy użyciu okienka zadań, takich jak **style i formatowanie** okienka zadań w programie Word. Niestandardowe okienka zadań zachowują się podobnie jak inne okienka zadań w systemie Microsoft Office. Użytkownicy mogą dock niestandardowych okienek zadań na różnych stronach w oknie aplikacji lub ich przeciągnij niestandardowych okienek zadań w dowolnej lokalizacji w oknie. Można utworzyć dodatku VSTO, która wyświetla wiele niestandardowych okienek zadań w tym samym czasie, a użytkownicy mogą kontrolować osobno każdy okienka zadań.  
  
### <a name="windows-forms-support"></a>Obsługa formularzy systemu Windows  
 Interfejs użytkownika niestandardowego okienka zadań utworzonej za pomocą narzędzi programowania pakietu Office w Visual Studio jest oparta na formanty formularzy systemu Windows. Znanych Projektant formularzy systemu Windows umożliwia projektowanie interfejsu użytkownika dla niestandardowego okienka zadań. Umożliwia także obsługę powiązania danych w formularzach systemu Windows można powiązać źródła danych z kontrolkami w okienku zadań.  
  
## <a name="creating-a-custom-task-pane"></a>Tworzenie niestandardowego okienka zadań  
 Podstawowe niestandardowego okienka zadań można tworzyć w dwóch krokach:  
  
1.  Tworzenie interfejsu użytkownika dla niestandardowego okienka zadań, dodając formanty formularzy systemu Windows do <xref:System.Windows.Forms.UserControl> obiektu.  
  
2.  Przez przekazanie kontrolki użytkownika, aby utworzyć wystąpienia niestandardowego okienka zadań <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> obiektu w Twojej dodatku VSTO. Ta kolekcja zwraca nową <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt, który służy do modyfikowania wyglądu w okienku zadań zdarzeń i reagowanie na użytkownika.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="creating-the-user-interface"></a>Tworzenie interfejsu użytkownika  
 Zawiera wszystkie niestandardowe okienka zadań, które są tworzone za pomocą narzędzi programowania pakietu Office w Visual Studio <xref:System.Windows.Forms.UserControl> obiektu. Ten formant użytkownika udostępnia interfejs użytkownika z niestandardowego okienka zadań. Formant użytkownika można utworzyć w czasie projektowania lub w czasie wykonywania. W przypadku utworzenia kontrolki użytkownika w czasie projektowania, można użyć projektanta formularzy systemu Windows do konstruowania interfejsu użytkownika okienka zadań.  
  
### <a name="instantiating-the-custom-task-pane"></a>Utworzenie wystąpienia niestandardowego okienka zadań  
 Po utworzeniu kontrolkę użytkownika, który zawiera interfejs użytkownika niestandardowego okienka zadań, należy utworzyć wystąpienia <xref:Microsoft.Office.Tools.CustomTaskPane>. W tym celu należy przekazać do kontrolki użytkownika <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> w Twojej dodatku VSTO przez wywoływanie jednej z <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody. Ta kolekcja jest ujawniona jako `CustomTaskPanes` pole `ThisAddIn` klasy. Poniższy przykładowy kod jest przeznaczona do uruchamiania z `ThisAddIn` klasy.  
  
 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> Metody zwracają nowe <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu. Ten obiekt służy do modyfikowania wyglądu w okienku zadań i reagowania na zdarzenia użytkownika.  
  
### <a name="controlling-the-task-pane-in-multiple-windows"></a>Kontrolowanie w okienku zadań w wielu okien  
 Niestandardowe okienka zadań skojarzonych z okno ramowe dokumentu, który przedstawia widok dokumentu lub elementu dla użytkownika. W okienku zadań jest widoczny tylko wtedy, gdy skojarzone okno jest widoczne.  
  
 Aby określić, które okno wyświetla niestandardowego okienka zadań, użyj odpowiedniej <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> przeciążenie metody tworzenia okienka zadań:  
  
-   Aby skojarzyć w okienku zadań w aktywnym oknie, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody.  
  
-   Aby skojarzyć okienka zadań z dokumentu, który jest hostowana przez określone okno, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody.  
  
 Niektóre aplikacje pakietu Office wymaga jawnego instrukcje dotyczące kiedy należy utworzyć lub wyświetlić z okienka zadań, gdy więcej niż jedno okno jest otwarty. Dzięki temu należy rozważyć, gdzie można utworzyć wystąpienia niestandardowego okienka zadań w kodzie, aby zapewnić odpowiednie dokumenty lub elementy w aplikacji okienka zadań. Aby uzyskać więcej informacji, zobacz [Zarządzanie okienka zadań niestandardowe w aplikacji systemu Windows](#Managing).  
  
## <a name="accessing-the-application-from-the-task-pane"></a>Uzyskiwanie dostępu do aplikacji z poziomu okienka zadań  
 Jeśli chcesz zautomatyzować aplikacji z formantu użytkownika, możesz bezpośrednio uzyskać dostęp model obiektów przy użyciu `Globals.ThisAddIn.Application` w kodzie. Statycznych `Globals` klasy zapewnia dostęp do `ThisAddIn` obiektu. `Application` Pole tego obiektu jest punktem wejścia do modelu obiektu aplikacji.  
  
 Aby uzyskać więcej informacji na temat `Application` pole `ThisAddIn` obiektów, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). Aby uzyskać wskazówki, który demonstruje sposób automatyzowania aplikacji z niestandardowego okienka zadań, zobacz [wskazówki: automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Aby uzyskać więcej informacji na temat `Globals` , zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="managing-the-user-interface-of-the-task-pane"></a>Zarządzanie interfejs użytkownika okienka zadań  
 Po utworzeniu w okienku zadań można użyć właściwości i zdarzenia <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt do kontrolowania interfejsu użytkownika w okienku zadań i odpowiadać, gdy użytkownik zmieni się w okienku zadań.  
  
### <a name="making-the-custom-task-pane-visible"></a>Zapewnienie widoczności niestandardowego okienka zadań  
 Domyślnie w okienku zadań nie jest widoczne. Aby wyświetlić w okienku zadań, należy ustawić <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> właściwości **true**.  
  
 Użytkownicy mogą zamknąć okienka zadań w dowolnym momencie, klikając **zamknąć** przycisku (X) w rogu okienka zadań. Ponieważ nie ma żadnym domyślny dla użytkowników ponownie otworzyć niestandardowego okienka zadań. Jeśli użytkownik zamyka niestandardowego okienka zadań, ten użytkownik nie można wyświetlić niestandardowego okienka zadań ponownie dopiero po podaniu sposób, aby go wyświetlić.  
  
 W dodatku VSTO programu w przypadku utworzenia niestandardowego okienka zadań, należy także utworzyć elementu interfejsu użytkownika, takie jak przycisk, które użytkownik może kliknąć, aby wyświetlić lub ukryć niestandardowego okienka zadań. W przypadku utworzenia niestandardowego okienka zadań w aplikacji pakietu Microsoft Office, który obsługuje Dostosowywanie Wstążki, można dodać grupę formantów na Wstążce przycisk, który wyświetla lub ukrywa niestandardowego okienka zadań. Aby uzyskać wskazówki, które pokazuje, jak to zrobić, zobacz [wskazówki: synchronizacja niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
 Jeśli w aplikacji pakietu Microsoft Office, która nie obsługuje dostosowywania wstążki tworzenia niestandardowego okienka zadań, możesz dodać <xref:Microsoft.Office.Core.CommandBarButton> która wyświetla lub ukrywa niestandardowego okienka zadań.  
  
### <a name="modifying-the-appearance-of-the-task-pane"></a>Modyfikowanie wyglądu okienka zadań  
 Rozmiar i położenie niestandardowego okienka zadań można kontrolować przy użyciu właściwości <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu. Inne zmiany mogą nawiązać wygląd niestandardowego okienka zadań przy użyciu właściwości <xref:System.Windows.Forms.UserControl> obiektu, który jest zawarty w niestandardowego okienka zadań. Na przykład obraz tła dla niestandardowego okienka zadań można określić za pomocą <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości kontrolki użytkownika.  
  
 W poniższej tabeli wymieniono zmiany można wprowadzać niestandardowego okienka zadań przy użyciu <xref:Microsoft.Office.Tools.CustomTaskPane> właściwości.  
  
|Zadanie|Właściwość|  
|----------|--------------|  
|Aby zmienić rozmiar okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|  
|Aby zmienić lokalizację okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|  
|Aby ukryć okienko zadań lub widoczny|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|  
|Aby uniemożliwić użytkownikowi zmienianie lokalizacji okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|  
  
### <a name="programming-custom-task-pane-events"></a>Programowanie niestandardowych zadań okienko zdarzenia  
 Możesz z dodatku VSTO odpowiadać, gdy użytkownik modyfikuje niestandardowego okienka zadań. Na przykład jeśli użytkownik zmieni orientację okienka z pionowego na poziome, można zmienić położenie kontrolki.  
  
 W poniższej tabeli wymieniono zdarzenia, które może obsłużyć do reagowania na zmiany wprowadzone przez użytkownika do niestandardowego okienka zadań.  
  
|Zadanie|Zdarzenie|  
|----------|-----------|  
|Aby odpowiedzieć, gdy użytkownik zmienia lokalizację, w okienku zadań.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|  
|Odpowiadać, gdy użytkownik ukrywa w okienku zadań lub ułatwia widoczne.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|  
  
## <a name="cleaning-up-resources-used-by-the-task-pane"></a>Oczyszczanie zasobów używanych przez okienka zadań  
 Po utworzeniu niestandardowego okienka zadań, <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu pozostaje w pamięci, dopóki jest uruchomiony z dodatku VSTO. Obiekt pozostaje w pamięci, nawet po kliknięciu **Zamknij** przycisku (X) w rogu okienka zadań.  
  
 Aby wyczyścić zasoby używane przez w okienku zadań podczas dodatku VSTO nadal działa, należy użyć <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> lub <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> metody. Te metody usunąć określonego <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt z `CustomTaskPanes` kolekcji, a ich wywołać <xref:Microsoft.Office.Tools.CustomTaskPane.Dispose%2A> metody obiektu.  
  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Automatycznie oczyszcza zasoby używane przez niestandardowego okienka zadań, gdy dodatku VSTO zostanie zwolniona. Nie wywołuj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> lub <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> metod w `ThisAddIn_Shutdown` obsługi zdarzeń w projekcie. Te metody spowoduje zgłoszenie <xref:System.ObjectDisposedException>, ponieważ [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] czyści zasoby wykorzystywane przez <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt przed `ThisAddIn_Shutdown` jest wywoływana. Aby uzyskać więcej informacji na temat `ThisAddIn_Shutdown`, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md)  
  
##  <a name="Managing"></a> Zarządzanie niestandardowych okienek zadań w wiele okien aplikacji  
 Podczas tworzenia niestandardowego okienka zadań w aplikacji, która używa wielu okien w celu wyświetlania dokumentów i innych elementów, należy wykonać dodatkowe czynności, aby upewnić się, że w okienku zadań jest widoczny, gdy użytkownik oczekuje.  
  
 Niestandardowe okienka zadań we wszystkich aplikacjach są skojarzone z okno ramowe dokumentu, który przedstawia widok dokumentu lub elementu dla użytkownika. W okienku zadań jest widoczny tylko wtedy, gdy skojarzone okno jest widoczne. Jednak nie wszystkie aplikacje używać okien ramowych dokumentu taki sam sposób.  
  
 Następujące grupy aplikacji mają różne programowanie wymagania:  
  
-   [Program Outlook](#Outlook)  
  
-   [Word, InfoPath i PowerPoint](#WordAndInfoPath)  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: Zarządzanie okienka zadań w dodatkach VSTO programu Word?](http://go.microsoft.com/fwlink/?LinkId=136781).  
  
##  <a name="Outlook"></a> Program Outlook  
 Podczas tworzenia niestandardowego okienka zadań dla programu Outlook, niestandardowego okienka zadań jest skojarzony z określonym okno Eksploratora lub Inspektora. Eksploratorów są systemu windows, które wyświetlanie zawartości folderu i inspektorzy są okna, które wyświetlania elementu, takie jak wiadomości e-mail lub zadania.  
  
 Jeśli chcesz wyświetlić niestandardowego okienka zadań z wielu Eksploratora lub Inspektora systemu windows, musisz utworzyć nowe wystąpienie klasy niestandardowego okienka zadań, po otwarciu okna Eksploratora lub Inspektora. W tym celu należy obsługiwać zdarzenie jest zgłaszane, gdy stworzono okno Eksploratora lub Inspektora, a następnie utwórz w okienku zadań w obsłudze zdarzeń. Można również obsługiwać zdarzenia Eksploratora i inspektora do ukrywania lub okienka zadań wyświetlana w zależności od tego, które okno jest widoczne.  
  
 Aby skojarzyć okienka zadań z określonym Eksploratora lub Inspektora, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody do tworzenia w okienku zadań i przekazać <xref:Microsoft.Office.Interop.Outlook.Explorer> lub <xref:Microsoft.Office.Interop.Outlook.Inspector> do obiektu *okna* parametru. Aby uzyskać więcej informacji na temat tworzenia niestandardowych okienek zadań, zobacz [niestandardowych Omówienie okienka zadań](../vsto/custom-task-panes.md).  
  
 Aby uzyskać wskazówki, który demonstruje sposób tworzenia okienka zadań dla każdej wiadomości e-mail, która jest otwarta, zobacz [wskazówki: wyświetlanie okienka niestandardowych zadań z wiadomościami E-Mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
### <a name="outlook-events"></a>Zdarzenia programu Outlook  
 Aby monitorować stan programu Eksplorator windows, można obsługiwać następujące zdarzenia związane z Eksploratora:  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>  
  
 Aby monitorować stan inspektora systemu windows, może obsługiwać następujące zdarzenia związane z Inspektora:  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>  
  
### <a name="preventing-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Zapobieganie wielu wystąpień niestandardowego okienka zadań w programie Outlook  
 Aby zapobiec wyświetlaniu wielu wystąpień niestandardowego okienka zadań systemu windows programu Outlook, jawnie usunąć niestandardowego okienka zadań z `CustomTaskPanes` Kolekcja `ThisAddIn` klasy po zamknięciu każdego okna. Wywołanie <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> metody w zdarzenie jest zgłaszane, gdy okno jest zamknięty, takich jak <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> lub <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>.  
  
 Outlook windows niestandardowego okienka zadań nie zostaną jawnie usunięte, może zawierać wiele wystąpień niestandardowego okienka zadań. Outlook jest czasami odtwarzana systemu windows i windows odtwarzania zachowywanie odwołań do żadnych niestandardowych okienek zadań, które zostały dołączone do nich.  
  
##  <a name="WordAndInfoPath"></a> Word, InfoPath i PowerPoint  
 Okno ramowe innego dokumentu wyświetlania każdego dokumentu programu Word, InfoPath i programu PowerPoint. Podczas tworzenia niestandardowego okienka zadań dla tych aplikacji niestandardowego okienka zadań są skojarzone tylko z określonego dokumentu. Jeśli użytkownik otwiera innego dokumentu, niestandardowego okienka zadań jest ukryta do momentu wyświetlenia dokumentu wcześniejszych ponownie.  
  
 Jeśli chcesz wyświetlić niestandardowego okienka zadań z wielu dokumentów, Utwórz nowe wystąpienie klasy niestandardowego okienka zadań, gdy użytkownik tworzy nowy dokument lub otwiera istniejący dokument. Aby to zrobić, obsługi zdarzeń, które są wywoływane, gdy dokument zostanie utworzone lub otwarte, a następnie utwórz w okienku zadań w obsłudze zdarzeń. Można również obsługiwać zdarzeń dokumentów, aby ukryć lub okienka zadań wyświetlana w zależności od tego, który dokument jest widoczny.  
  
 Aby skojarzyć okienka zadań z okna określonego dokumentu, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody do tworzenia w okienku zadań i przekazać <xref:Microsoft.Office.Interop.Word.Window> (dla programu Word), <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (dla programu InfoPath), lub <xref:Microsoft.Office.Interop.PowerPoint.DocumentWindow> (dla programu PowerPoint) do *okna*parametru.  
  
### <a name="word-events"></a>Zdarzenia programu Word  
 Aby monitorować stan okna dokumentów programu Word, może obsługiwać następujące zdarzenia:  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>  
  
### <a name="infopath-events"></a>Zdarzenia InfoPath  
 Aby monitorować stan okna dokumentów w InfoPath, może obsługiwać następujące zdarzenia:  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>  
  
### <a name="powerpoint-events"></a>Zdarzenia programu PowerPoint  
 Aby monitorować stan okna dokumentów w programie PowerPoint, może obsługiwać następujące zdarzenia:  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterNewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.NewPresentation>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationOpen>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowDeactivate>  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Wskazówki: Automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Wskazówka: Synchronizacja niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
