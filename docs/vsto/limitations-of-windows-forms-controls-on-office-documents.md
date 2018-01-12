---
title: Formanty w dokumentach pakietu Office formularzy ograniczenia systemu Windows | Dokumentacja firmy Microsoft
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
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2c8795b643afff2cc02d507a1764871aa0e0e181
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Ograniczenia formantów formularzy Windows w dokumentach pakietu Office
  Istnieją pewne różnice między formanty formularzy systemu Windows, które są dodawane do dokumentów pakietu Microsoft Office Word lub arkuszy programu Microsoft Office Excel i formanty formularzy systemu Windows, które są dodawane do formularzy systemu Windows. Na przykład podczas dodawania <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolować dokument, właściwości, takie jak <xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>, <xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A>, i <xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A> nie działają zgodnie z oczekiwaniami może.  
  
 Wiele z tych różnic są powodowane przez sposób tego formularzy systemu Windows znajdują się formanty w dokumentach. Po dodaniu formantu formularzy systemu Windows w dokumencie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] osadzenie formantu ActiveX, następnie obsługującego kontrolki formularza systemu Windows w dokumencie. Formant formularzy systemu Windows nie jest zagnieżdżony bezpośrednio w dokumencie.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Ograniczenia metody i właściwości formantów formularzy systemu Windows  
 Istnieje wiele metod i właściwości formantów formularzy systemu Windows, które nie działają tak samo w dokumencie na formularzu systemu Windows, a w związku z tym zaleca się, że nie być stosowane. Na przykład, takie jak ustawienie właściwości `Dock` i `Anchor` wpływa tylko na pozycji kontroli względem kontenera formantu ActiveX, zamiast dokumentu. Poniżej przedstawiono listę nieobsługiwanej metody i właściwości formantów formularzy systemu Windows dla programu Word i Excel:  
  
-   Nieobsługiwanej metody i właściwości formantów programu Excel:  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   Nieobsługiwanej metody i właściwości formantów Word:  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 Ponadto nie można ustawić `Left` lub `Top` właściwości formantów formularzy systemu Windows, które są zgodne z tekstu do dokumentu programu Word. Formanty formularzy systemu Windows są dodawane z tekstu w następujących przypadkach:  
  
-   Programowe Dodawanie formantu do dokumentu programu Word i użyć metody, która określa zakres dla lokalizacji.  
  
-   Formant formularzy systemu Windows zostanie dodany do dokumentu programu Word w czasie projektowania. Można to zmienić, modyfikując formantu w projektancie.  
  
## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Różnice w formantach formularzy systemu Windows w dokumentach pakietu Office  
 Formanty formularzy systemu Windows mają zwykle takie samo zachowanie w dokumencie pakietu Office jak na formularzu systemu Windows, ale istnieją pewne różnice. W poniższej tabeli opisano różnice, które istnieją w formantach formularzy systemu Windows w dokumentach pakietu Office.  
  
|Funkcja|Różnica|  
|-------------------|----------------|  
|Kolejność tabulacji formantu|Nie można przełączać się między formanty umieszczone na arkuszu programu Excel lub dokumentu programu Word.|  
|Grupowanie formantu|Nie można użyć <xref:System.Windows.Forms.GroupBox> formantu zawierają inne formanty na dokumentu pakietu Office. Po dodaniu wielokrotnych przycisków radiowych bezpośrednio do dokumentu przycisków radiowych nie wykluczają. Można napisać kod, aby przyciski radiowe wykluczają się wzajemnie; Jednak to preferowane rozwiązanie jest dodawanie przycisków radiowych do formantu użytkownika, a następnie dodaj kontrolkę użytkownika do dokumentu. Aby uzyskać więcej informacji, zobacz próbka formantów programu Word lub próbki formanty programu Excel w [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md).|  
|Typ formantu|Formanty formularzy systemu Windows używane w dokumentach są ujęte w klasie pochodzącymi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zapewniającą formantów dodatkowe funkcje specyficzne dla arkuszu programu Excel lub dokumentu programu Word. Na przykład, jeśli masz `Button` kontrolować w arkuszu programu Excel, należy określić typ jako <xref:Microsoft.Office.Tools.Excel.Controls.Button> zamiast <xref:System.Windows.Forms.Button> odwołuje się do lub Rzutowanie obiektu.|  
|Formant położenia i rozmiaru|Rozmiar i położenie formantu jest określana przez właściwości, które są częścią kontenera formantu ActiveX. Właściwości formantu ActiveX przyjmować wartości innej niż równoważne właściwości formantu formularzy systemu Windows. Podczas ustawiania `Top`, `Left`, `Height`, lub `Width` właściwości formantu, jest on mierzony w punktów zamiast pikseli.|  
|Położenie kontrolki na dokumenty programu Word|Jeśli dodasz formanty oparte na układ pamiętać, że kontrolki będą przepływać z zawartością wraz ze zmianą zawartości. Nie można zakotwiczyć formant akapitu podczas przeciągania go z **przybornika** ponieważ formant został dodany do dokumentu programu Word z tekstu. Jeśli używasz innej metody do Dodaj formant, takich jak dwukrotnie kontrolki, zgodnie z opcją programu Word, ustawione przez wstawianie obrazów wstawiany jest formant.<br /><br /> Nie można ustawić `Left` lub `Top` właściwości formantu, który jest wbudowany z tekstem.<br /><br /> Nie można umieścić kontrolek, w nagłówku lub stopce strony lub wewnątrz podrzędnego.|  
|Zdarzenia formantów|Po wybraniu kontrolka wywołuje zdarzeń w następującej kolejności:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Gdy formant nie jest zaznaczona, zgłasza zdarzeń w następującej kolejności:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|Skalowanie formantu|Jeśli zmienisz ustawienie powiększenia dokumentu na inny niż 100% formanty są wyłączone, mimo że pojawią się one do skalowania w dokumencie. Na przykład kliknięcie przycisku, gdy dokument jest na powiększenia 130% go wyświetli komunikat że formant został wyłączony do momentu powiększenia ustawiono wartość 100%. Formanty będzie działać prawidłowo po zmianie powiększenie do 100%.|  
|Wartości właściwości formantu|Mimo że właściwości formantów w formularzu systemu Windows są ustawione na wartość całkowitą, są ustawione jeden dla formantów w dokumencie programu Word. W programie Excel wartości właściwości formantów są ustawione na wartość typu double. Jeśli `Height` i `Width` właściwości formantu w arkuszu przekracza rozmiar arkusza lub ekranu, wartość zostanie obcięta.|  
|Zmiana rozmiaru formantu|Jeśli rozmiar formantu w dokumencie przy użyciu jednej z uchwytów osiem zmiany rozmiaru, nowe kontrolki wymiary nie są uwzględniane w **właściwości** okna do czasu formantu jest wybierane ponownie.|  
|Zachowanie kontroli|Formanty w arkuszu programu Excel może nieprzewidywalne zachowanie, gdy okno arkusza dzieli się. Na przykład uzyskać dostęp do <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> w arkuszu może być dostępny tylko w jednej z systemu windows.|  
|Nazwy formantów|Nie można użyć słowa zastrzeżone do formantów nazwy. Na przykład, jeśli dodasz <xref:Microsoft.Office.Tools.Excel.Controls.Button> do arkusza i Zmień nazwę, aby **systemu**, wystąpią błędy podczas kompilowania projektu.|  
|Programowe dodawanie formantów|Aby dodać kontrolkę do dokumentu w czasie wykonywania nie należy używać formantu konstruktora. Zamiast tego należy użyć metody pomocnika udostępniane przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Na przykład użyć <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> metody w celu dodania przycisku do arkusza. Jeśli chcesz dodać kontrolkę, która nie jest obsługiwana przez te metody pomocnicze, można użyć metody AddControl. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).|  
|Kopiowanie formantów|Jeśli kopiowanie formantu formularzy systemu Windows i wklej go do dokumentu w czasie wykonywania, pusty kontener formantu ActiveX zostanie wklejona do dokumentu. Formant formularzy systemu Windows nie jest wyświetlany w nowej lokalizacji, a kod związany z oryginalnego formantu nie jest kopiowany do kontenera formantu ActiveX.|  
  
## <a name="limitations-in-document-level-projects"></a>Ograniczenia w projektach na poziomie dokumentu  
 Niektóre ograniczenia za pomocą formantów formularzy systemu Windows w dokumentach są unikatowe dla projektów na poziomie dokumentu.  
  
### <a name="control-support-at-design-time"></a>Obsługi formantów w czasie projektowania  
 Niektóre formanty formularzy systemu Windows są usuwane z **przybornika** po arkuszu programu Excel lub dokumentu programu Word jest otwarty w projektancie programu Visual Studio. Jest to spowodowane ograniczenia techniczne lub ponieważ ta funkcja jest już dostępne w ramach programu Word i Excel. Projekty programu Excel i Word obsługują wszystkie formanty formularzy systemu Windows i innymi składnikami, które są widoczne w **przybornika** gdy dokument ma fokus i można również dodawać formanty innych firm do arkusza lub dokumentu.  
  
> [!NOTE]  
>  Wszystkie formanty są usuwane z **przybornika** gdy dokument jest chroniony. Uzyskać informacji na temat ochrony dokumentu, zobacz [ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md).  
  
> [!NOTE]  
>  Formanty innej firmy musi mieć <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawić atrybutu **true** , aby można używać w rozwiązaniach pakietu Office.  
  
 Następujące formanty i składniki nie są dostępne w **przybornika**:  
  
-   <xref:System.Windows.Forms.BindingNavigator>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.DataGrid>  
  
-   <xref:System.DirectoryServices.DirectoryEntry>  
  
-   <xref:System.DirectoryServices.DirectorySearcher>  
  
-   <xref:System.Windows.Forms.ErrorProvider>  
  
-   <xref:System.Diagnostics.EventLog>  
  
-   <xref:System.IO.FileSystemWatcher>  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel>  
  
-   <xref:System.Windows.Forms.GroupBox>  
  
-   <xref:System.Windows.Forms.MainMenu>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Messaging.MessageQueue>  
  
-   <xref:System.Windows.Forms.NotifyIcon>  
  
-   <xref:System.Windows.Forms.PageSetupDialog>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Diagnostics.PerformanceCounter>  
  
-   <xref:System.Windows.Forms.PrintDialog>  
  
-   <xref:System.Drawing.Printing.PrintDocument>  
  
-   <xref:System.Windows.Forms.PrintPreviewControl>  
  
-   <xref:System.Diagnostics.Process>  
  
-   <xref:System.Windows.Forms.RichTextBox>  
  
-   <xref:System.IO.Ports.SerialPort>  
  
-   <xref:System.ServiceProcess.ServiceController>  
  
-   <xref:System.Windows.Forms.SplitContainer>  
  
-   <xref:System.Windows.Forms.Splitter>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TableLayoutPanel>  
  
-   <xref:System.Timers.Timer>  
  
-   <xref:System.Windows.Forms.Timer>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer>  
  
-   <xref:System.Windows.Forms.ToolStripDropDown>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownMenu>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>  
  
### <a name="support-for-legacy-activex-controls"></a>Obsługa starszych formantów ActiveX  
 Jeśli utworzysz poziomie dokumentu Office project używa istniejącego dokumentu programu Word lub skoroszytu programu Excel, który zawiera formanty ActiveX funkcji formantów ActiveX nie zostaną utracone; ponieważ nie ma nie obsługuje dodawania nowych formantów ActiveX do dokumentów z poziomu programu Visual Studio. Na przykład, jeśli dokument programu Word znajduje się przycisk z **kontroli** przybornika uruchomioną makra Visual Basic for Applications (VBA), będzie Uruchom makro po dokument został użyty w projektach pakietu Office. Jednak zalecane jest, Usuń formantów ActiveX i makra VBA i zastąpić je formanty formularzy systemu Windows i kod zarządzany.  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Formanty formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Instrukcje: Dodawanie kontrolek Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  