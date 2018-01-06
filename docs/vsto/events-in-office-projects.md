---
title: Zdarzenia w projektach pakietu Office | Dokumentacja firmy Microsoft
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
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
ms.assetid: 666d7f23-ef85-4f2e-9cd3-258df5bdc6fd
caps.latest.revision: "51"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 87d1fe708d4090fc6d2dd9509a04d13e7a21e079
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="events-in-office-projects"></a>Zdarzenia w projektach pakietu Office
  Każdy szablon projektu pakietu Office automatycznie generuje kilka programów obsługi zdarzeń. Programy obsługi zdarzeń dla dostosowań na poziome dokumentu są nieco inne niż programy obsługi zdarzeń dla dodatków VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="document-level-projects"></a>Projektów na poziomie dokumentu  
 Program Visual Studio udostępnia wygenerowanego kodu nowych lub istniejących dokumentów lub arkuszy w dostosowaniach na poziomie dokumentu. Ten kod wywołuje dwóch różnych zdarzeń: **uruchamiania** i **zamknięcia**.  
  
### <a name="startup-event"></a>Startup — zdarzenie  
 **Uruchamiania** zdarzenie jest wywoływane dla każdego z elementów hosta (dokument, skoroszyt lub arkusz) po dokumentu jest uruchomiona, a cały kod inicjowania w zestawie zostało uruchomione. Jest to ostateczność do uruchamiania w konstruktorze klasy działający w kodzie. Aby uzyskać informacje o obiektach hosta, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
 Podczas tworzenia projektu poziomie dokumentu programu Visual Studio tworzy programy obsługi zdarzeń dla **uruchamiania** zdarzenia w plikach wygenerowanego kodu:  
  
-   Microsoft Office Word projektów, nosi nazwę programu obsługi zdarzeń `ThisDocument_Startup`.  
  
-   Dla projektów programu Microsoft Office Excel obsługi zdarzeń mają następujące nazwy:  
  
    -   `Sheet1_Startup`  
  
    -   `Sheet2_Startup`  
  
    -   `Sheet3_Startup`  
  
    -   `ThisWorkbook_Startup`  
  
### <a name="shutdown-event"></a>Shutdown — zdarzenie  
 **Zamknięcia** zdarzenie jest wywoływane dla każdego z elementów hosta (dokument lub arkusz) gdy domena aplikacji, kodu załadowanego w ma zwolnienia. Jest ostatnim etapem można wywołać w klasie, ponieważ zwalnia.  
  
 Podczas tworzenia projektu poziomie dokumentu programu Visual Studio tworzy programy obsługi zdarzeń dla **zamknięcia** zdarzenia w plikach wygenerowanego kodu:  
  
-   Microsoft Office Word projektów, nosi nazwę programu obsługi zdarzeń `ThisDocument_Shutdown`.  
  
-   Dla projektów programu Microsoft Office Excel obsługi zdarzeń mają następujące nazwy:  
  
    -   `Sheet1_Shutdown`  
  
    -   `Sheet2_Shutdown`  
  
    -   `Sheet3_Shutdown`  
  
    -   `ThisWorkbook_Shutdown`  
  
> [!NOTE]  
>  Nie usuwaj programowo formantów w trakcie **zamknięcia** obsługi zdarzeń dokumentu. Elementy interfejsu użytkownika dokumentu nie będą dostępne podczas **zamknięcia** zdarzenie. Jeśli chcesz usunąć formanty przed zamknięciem aplikacji, Dodaj swój kod do innego programu obsługi zdarzeń, takich jak **BeforeClose** lub **BeforeSave**.  
  
### <a name="event-handler-method-declarations"></a>Deklaracje metody obsługi zdarzeń  
 Co deklaracja metody obsługi zdarzeń ma te same argumenty przekazane do niego: *nadawcy* i *e*. W programie Excel *nadawcy* argument odwołuje się do arkusza, takich jak `Sheet1` lub `Sheet2`; w Word *nadawcy* argument odwołuje się do dokumentu. *e* argument odwołuje się do standardowych argumenty dla zdarzenia, które nie są używane w tym przypadku.  
  
 Poniższy przykład kodu pokazuje domyślne obsługi zdarzeń w projektach na poziomie dokumentu dla programu Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]  
  
 Poniższy przykład kodu pokazuje domyślne obsługi zdarzeń w projektach na poziomie dokumentu dla programu Excel.  
  
> [!NOTE]  
>  Poniższy przykład kodu pokazuje obsługi zdarzeń w `Sheet1` klasy. Nazwy programów obsługi zdarzeń w innych klas pozycji hosta odpowiadają nazwę klasy. Na przykład w `Sheet2` klasy **uruchamiania** nosi nazwę obsługi zdarzeń `Sheet2_Startup`. W `ThisWorkbook` klasy **uruchamiania** nosi nazwę obsługi zdarzeń `ThisWorkbook_Startup`.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]  
  
### <a name="order-of-events-in-document-level-excel-projects"></a>Kolejność zdarzeń w projektach na poziomie dokumentu programu Excel  
 **Uruchamiania** są wywoływane programy obsługi zdarzeń w projektach programu Excel, w następującej kolejności:  
  
1.  `ThisWorkbook_Startup`.,  
  
2.  `Sheet1_Startup`.,  
  
3.  `Sheet2_Startup`.,  
  
4.  `Sheet3_Startup`.,  
  
5.  Inne arkuszy w kolejności.  
  
 **Zamknięcia** są wywoływane programy obsługi zdarzeń w rozwiązaniu skoroszytu, w następującej kolejności:  
  
1.  `ThisWorkbook_Shutdown`.,  
  
2.  `Sheet1_Shutdown`.,  
  
3.  `Sheet2_Shutdown`.,  
  
4.  `Sheet3_Shutdown`.,  
  
5.  Inne arkuszy w kolejności.  
  
 Kolejność jest określana podczas kompilowania projektu. Jeśli użytkownik zmienia arkuszy w czasie wykonywania, nie powoduje zmiany kolejności, że zdarzenia są wywoływane przy następnym skoroszyt jest otwarty lub zamknięty.  
  
## <a name="vsto-add-in-projects"></a>Projektów dodatku VSTO  
 Program Visual Studio udostępnia wygenerowanego kodu w dodatkach VSTO. Ten kod wywołuje dwóch różnych zdarzeń: <xref:Microsoft.Office.Tools.AddInBase.Startup> i <xref:Microsoft.Office.Tools.AddInBase.Shutdown>.  
  
### <a name="startup-event"></a>Startup — zdarzenie  
 <xref:Microsoft.Office.Tools.AddIn.Startup> Zdarzenie jest wywoływane po dodatku VSTO jest załadowane, a cały kod inicjowania w zestawie zostało uruchomione. To zdarzenie jest obsługiwane przez `ThisAddIn_Startup` metody w wygenerowanym pliku kodu.  
  
 Kod w `ThisAddIn_Startup` procedura obsługi zdarzeń jest pierwszy kod użytkownika, aby uruchomić, chyba że dodatek VSTO zastępuje <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metody. W takim przypadku `ThisAddIn_Startup` program obsługi zdarzeń jest wywoływana po wykonaniu <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.  
  
 Nie dodawaj kod w `ThisAdd-In_Startup` obsługi zdarzeń, jeśli kod wymaga dokument jest otwarty. Zamiast tego należy dodać kodu na zdarzenie, który wywołuje aplikacji pakietu Office, gdy użytkownik tworzy lub otwiera dokument. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do dokumentów pakietu Office aplikacji uruchamia](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Aby uzyskać więcej informacji na temat uruchamiania dodatków VSTO zobacz [dodatki architektura VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="shutdown-event"></a>Shutdown — zdarzenie  
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> Zdarzenie jest zgłaszane, gdy ładowany w kodzie domeny aplikacji ma zostać zwolniony. To zdarzenie jest obsługiwane przez `ThisAddIn_Shutdown` metody w wygenerowanym pliku kodu. Ten program obsługi zdarzeń jest kod ostatniego użytkownika do uruchomienia, gdy jest zwalniany dodatku VSTO.  
  
#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Shutdown — zdarzenie w programie Outlook VSTO dodatki  
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> Zdarzenie jest wywoływane tylko wtedy, gdy użytkownik wyłącza dodatku VSTO za pomocą okna dialogowego Dodatki COM w programie Outlook. Nie jest wywoływane po zamknięciu programu Outlook. Jeśli masz kod, który musi działać po zamknięciu programu Outlook, obsługiwać jeden z następujących zdarzeń:  
  
-   <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> Zdarzenie <xref:Microsoft.Office.Interop.Outlook.Application> obiektu.  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> Zdarzenie <xref:Microsoft.Office.Interop.Outlook.Explorer> obiektu.  
  
> [!NOTE]  
>  Możesz wymusić programu Outlook, aby podnieść <xref:Microsoft.Office.Tools.AddInBase.Shutdown> zdarzeń po wydaniu przez modyfikację rejestru. Jednak jeśli administrator przekształcenia to ustawienie, żadnego kodu dodanie do `ThisAddIn_Shutdown` metoda nie jest uruchamiana po zamknięciu programu Outlook. Aby uzyskać więcej informacji, zobacz [zamykania zmian dla programu Outlook 2010](http://go.microsoft.com/fwlink/?LinkID=184614).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programowania dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)  
  
  