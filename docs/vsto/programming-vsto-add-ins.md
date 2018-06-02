---
title: Program dodatków VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 52297a90f562ac534d0087c273cde05f021711af
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692876"
---
# <a name="program-vsto-add-ins"></a>Program dodatków VSTO
  Rozszerzając przez utworzenie dodatków VSTO aplikacji pakietu Microsoft Office, można napisać kod bezpośrednio przed `ThisAddIn` klasy w projekcie. Ta klasa służy do wykonywania zadań takich jak uzyskiwanie dostępu do modelu obiektów programu Microsoft Office aplikacji hosta, dostosowywanie interfejsu użytkownika (UI), aplikacji i udostępnianie obiektów w Twojej dodatku VSTO do innych rozwiązań pakietu Office.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Niektóre aspekty pisanie kodu w dodatku VSTO projektów różnią się od innych typów projektów programu Visual Studio. Wiele z tych różnic przyczyną są sposobem Office modele obiektów są widoczne dla kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [napisać kod w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).  
  
 Aby uzyskać ogólne informacje dotyczące dodatków narzędzi VSTO i innych typów rozwiązań można utworzyć za pomocą narzędzi programowania pakietu Office w Visual Studio, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="use-the-thisaddin-class"></a>Thisaddin — klasa  
 Można uruchomić pisania kodu dodatku VSTO w `ThisAddIn` klasy. Visual Studio automatycznie generuje tej klasy w *ThisAddIn.vb* (w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) lub *ThisAddIn.cs* (w języku C#) code pliku w projekcie dodatku VSTO. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Automatycznie tworzy tej klasy, podczas ładowania dodatku VSTO z aplikacji Microsoft Office.  
  
 Istnieją dwie domyślne obsługi zdarzeń w `ThisAddIn` klasy. Aby uruchomić kod po dodatku VSTO załadowaniu, Dodaj kod, aby `ThisAddIn_Startup` obsługi zdarzeń. Aby uruchomić kod przed dodatku VSTO zostanie zwolniona, Dodaj kod, aby `ThisAddIn_Shutdown` obsługi zdarzeń. Aby uzyskać więcej informacji o tych programów obsługi zdarzeń, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  W programie Outlook, domyślnie `ThisAddIn_Shutdown` program obsługi zdarzeń nie jest zawsze wywoływany po dodatku VSTO zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
### <a name="access-the-object-model-of-the-host-application"></a>Dostęp do modelu obiektów w aplikacji hosta  
 Aby uzyskać dostęp do modelu obiektów w aplikacji hosta, należy użyć `Application` pole `ThisAddIn` klasy. To pole zwraca obiekt reprezentujący bieżące wystąpienie aplikacji hosta. W poniższej tabeli wymieniono typ wartości zwracanej przez `Application` w każdym projekcie dodatku VSTO.  
  
|Host aplikacji|Zwracany typ wartości|  
|----------------------|-----------------------|  
|Program Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|  
|Program Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|  
|Program Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|  
|Microsoft Office PowerPoint|<xref:Microsoft.Office.Interop.PowerPoint.Application>|  
|Program Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|  
|Program Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|  
|Program Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|  
  
 Poniższy przykładowy kod przedstawia sposób użycia `Application` pola, aby utworzyć nowy skoroszyt w dodatku VSTO dla programu Microsoft Office Excel. W tym przykładzie jest przeznaczona do uruchamiania z `ThisAddIn` klasy.  
  
```vb  
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Aby zrobić to samo z poza `ThisAddIn` klasy, należy użyć `Globals` do dostępu do obiektu `ThisAddIn` klasy. Aby uzyskać więcej informacji na temat `Globals` obiektów, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
```vb  
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Aby uzyskać więcej informacji na temat modeli obiektów określonych aplikacji pakietu Microsoft Office zobacz następujące tematy:  
  
-   [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)  
  
-   [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md)  
  
-   [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath — rozwiązania](../vsto/infopath-solutions.md)  
  
-   [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md)  
  
-   [Rozwiązania projektu](../vsto/project-solutions.md)  
  
-   [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)  
  
###  <a name="AccessingDocuments"></a> Dostęp do dokumentu, podczas uruchamiania aplikacji pakietu Office  
 Nie wszystkie [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikacje automatycznie otworzyć dokument podczas uruchamiania ich i żaden [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aplikacji otworzyć dokument, po ponownym uruchomieniu. W związku z tym nie należy dodawać kod w `ThisAdd-In_Startup` obsługi zdarzeń, jeśli kod wymaga dokument jest otwarty. Zamiast tego należy dodać kodu na zdarzenie, który wywołuje aplikacji pakietu Office, gdy użytkownik tworzy lub otwiera dokument. W ten sposób można zagwarantować dokument jest otwarty, zanim kod działa na nim operacji.  
  
 Poniższy przykładowy kod działa z dokumentu programu Word, tylko wtedy, gdy użytkownik tworzy dokument lub otwiera istniejący dokument.  
  
 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]  
  
### <a name="thisaddin-members-to-use-for-other-tasks"></a>Elementy członkowskie klasy ThisAddIn dla innych zadań  
 W poniższej tabeli opisano inne typowe zadania i pokazuje, którzy członkowie `ThisAddIn` klasa służy do wykonywania zadań.  
  
|Zadanie|Elementu członkowskiego do użycia|  
|----------|-------------------|  
|Uruchom kod, aby zainicjować dodatku VSTO, gdy jest ładowany dodatku VSTO.|Dodaj kod, aby `ThisAddIn_Startup` metody. Jest to domyślny program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.AddInBase.Startup> zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).|  
|Uruchamianie kodu, aby wyczyścić zasoby używane przez dodatku VSTO, zanim zostanie usunięty z pamięci dodatku VSTO.|Dodaj kod, aby `ThisAddIn_Shutdown` metody. Jest to domyślny program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.AddInBase.Shutdown> zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md). **Uwaga:** w programie Outlook, domyślnie `ThisAddIn_Startup` program obsługi zdarzeń nie jest zawsze wywoływany po dodatku VSTO zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).|  
|Wyświetlanie niestandardowego okienka zadań.|Użyj `CustomTaskPanes` pola. Aby uzyskać więcej informacji, zobacz [niestandardowego okienka zadań](../vsto/custom-task-panes.md).|  
|Uwidacznia obiekty użytkownika dodatku VSTO do innych rozwiązań Microsoft Office.|Zastąpienie <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metody. Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|  
|Dostosowywanie funkcji pakietu Microsoft Office system zaimplementowanie interfejsu rozszerzalności.|Zastąpienie <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> sposób zwrócenia wystąpienia klasy, która implementuje interfejs. Aby uzyskać więcej informacji, zobacz [dostosowywanie funkcji interfejsu użytkownika korzystając z rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Uwaga:** do dostosowywania wstążki interfejsu użytkownika, możesz też przesłonić <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> metody.|  
  
### <a name="understand-the-design-of-the-thisaddin-class"></a>Zrozumienie konstrukcji thisaddin — klasa  
 W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], <xref:Microsoft.Office.Tools.AddIn> jest interfejsem. `ThisAddIn` Pochodną klasy <xref:Microsoft.Office.Tools.AddInBase> klasy. Ta klasa podstawowa przekierowuje wszystkie wywołania do jego elementów członkowskich do wewnętrznego implementacja <xref:Microsoft.Office.Tools.AddIn> interfejsu w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 W przypadku projektów dodatku VSTO dla programu Outlook `ThisAddIn` pochodną klasy `Microsoft.Office.Tools.Outlook.OutlookAddIn` klasy w projektach przeznaczonych dla programu .NET Framework 3.5 oraz z <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Te klasy podstawowej podać kilka dodatkowych funkcji do obsługi regionów formularzy. Aby uzyskać więcej informacji na temat regionów formularzy, zobacz [regionów formularzy Outlook utwórz](../vsto/creating-outlook-form-regions.md).  
  
## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Dostosowywanie interfejsu użytkownika aplikacji pakietu Microsoft Office  
 Aplikacje interfejsu użytkownika pakietu Microsoft Office można dostosować programowo przy użyciu dodatku VSTO. Można na przykład dostosowywania wstążki, wyświetlić niestandardowego okienka zadań lub utworzyć regionu formularza niestandardowych w programie Outlook. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
 Program Visual Studio oferuje projektantom i klasy, które służy do tworzenia niestandardowych okienek zadań, dostosowań Wstążki i regionów formularzy programu Outlook. Te klasy projektantów i pomóc w celu uproszczenia procesu dostosowywania tych funkcji. Aby uzyskać więcej informacji, zobacz [niestandardowego okienka zadań](../vsto/custom-task-panes.md), [projektanta wstążki](../vsto/ribbon-designer.md), i [regionów formularzy Outlook utwórz](../vsto/creating-outlook-form-regions.md).  
  
 Jeśli chcesz dostosować jeden z tych funkcji w taki sposób, który nie jest obsługiwany przez klasy i projektantów, można również dostosować te funkcje, implementując *rozszerzalności interfejsu* w Twojej dodatku VSTO. Aby uzyskać więcej informacji, zobacz [dostosowywanie funkcji interfejsu użytkownika korzystając z rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
 Ponadto można zmodyfikować dokumentów interfejsu użytkownika programu Word i skoroszytów programu Excel przez generowanie elementy hosta rozszerzających zachowanie dokumentów i skoroszytów. Umożliwia dodawanie formantów zarządzanego do dokumentów i arkuszy. Aby uzyskać więcej informacji, zobacz [dokumentów rozszerzania programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Wywoływanie kodu w dodatkach VSTO z innych rozwiązań  
 Obiekty można ujawnić w Twojej dodatku VSTO do innych rozwiązań, łącznie z innych rozwiązań pakietu Office. Jest to przydatne, jeśli dodatek VSTO udostępnia usługi, który chcesz włączyć innych rozwiązań do użycia. Na przykład jeśli masz dodatku VSTO dla programu Microsoft Office Excel wykonuje obliczenia na danych finansowych z usługi sieci web, inne rozwiązania można wykonać tych obliczeń przez wywołanie dodatku VSTO programu Excel w czasie wykonywania.  
  
 Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Wskazówki: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Dostosowywanie funkcji interfejsu użytkownika korzystając z rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)  
  
  