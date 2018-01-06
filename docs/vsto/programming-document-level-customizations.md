---
title: "Programowanie dostosowań na poziome dokumentu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
ms.assetid: 6c421055-7bea-4db4-a4c9-539b8c78d4ee
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 68d0cfbc96b72208eee26f3cc75dd9a19d1b63fc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="programming-document-level-customizations"></a>Programowanie dostosowań na poziome dokumentu
  Rozszerzając program Microsoft Office Word i Microsoft Office Excel za pomocą dostosowania na poziomie dokumentu, można wykonywać następujące zadania:  
  
-   Automatyczne stosowanie przy użyciu jego object model.  
  
-   Dodawanie formantów do powierzchni dokumentu.  
  
-   Wywołania języka Visual Basic dla kodu aplikacji (VBA) w dokumencie z zestawu dostosowania.  
  
-   Wywoływanie kodu w zestawie dostosowania z języka VBA.  
  
-   Zarządzanie niektórych aspektów dokumentu, gdy znajduje się na serwerze, który nie ma zainstalowanych w Microsoft Office.  
  
-   Dostosowywanie interfejsu użytkownika (UI) aplikacji.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Niektóre aspekty pisanie kodu w projektach na poziomie dokumentu różnią się od innych typów projektów programu Visual Studio. Wiele z tych różnic przyczyną są sposobem Office modele obiektów są widoczne dla kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md).  
  
 Aby uzyskać ogólne informacje o poziomie dokumentu i innych typów rozwiązań, można utworzyć za pomocą narzędzi programowania pakietu Office w Visual Studio, zobacz [rozwój rozwiązań Office ― omówienie &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="using-the-generated-classes-in-document-level-projects"></a>Przy użyciu wygenerowane klasy w projektach na poziomie dokumentu  
 Podczas tworzenia projektu poziomie dokumentu programu Visual Studio automatycznie generuje klasę w projekcie, który można użyć, aby rozpocząć pisanie kodu. Program Visual Studio generuje różnych klas dla programu Word i Excel:  
  
-   W projektach na poziomie dokumentu dla programu Word, nosi nazwę klasy `ThisDocument` domyślnie.  
  
-   Wiele wygenerowane klasy mają projektów na poziomie dokumentu dla programu Excel: jeden dla skoroszytem i jeden dla każdego arkusza. Domyślnie te klasy mają następujące nazwy:  
  
    -   `ThisWorkbook`  
  
    -   `Sheet1`  
  
    -   `Sheet2`  
  
    -   `Sheet3`  
  
 Wygenerowana klasa zawiera procedury obsługi zdarzeń, które są wywoływane, gdy dokument jest otwarty lub zamknięty. Aby uruchomić kod po otwarciu dokumentu, Dodaj kod, aby `Startup` obsługi zdarzeń. Aby uruchomić kod bezpośrednio przed zamknięciem dokumentu, Dodaj kod, aby `Shutdown` obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
### <a name="understanding-the-design-of-the-generated-classes"></a>Opis projektu wygenerowane klasy  
 W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], typy elementów hosta w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] są interfejsy, więc wygenerowane klasy nie może pochodzić ich realizacji z nich. Zamiast tego wygenerowane klasy dziedziczyć większość ich elementy członkowskie następujących klas podstawowych:  
  
-   `ThisDocument`: pochodną <xref:Microsoft.Office.Tools.Word.DocumentBase>.  
  
-   `ThisWorkbook`: pochodną <xref:Microsoft.Office.Tools.Excel.WorkbookBase>.  
  
-   `Sheet` *n* : pochodną <xref:Microsoft.Office.Tools.Excel.WorksheetBase>.  
  
 Te klasy podstawowej przekierować wszystkie wywołania ich elementy członkowskie do wewnętrznej implementacji interfejsów odpowiedniego elementu hosta w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Na przykład, jeśli wywołujesz <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> metody `ThisDocument` klasy <xref:Microsoft.Office.Tools.Word.DocumentBase> klasy przekierowuje tego wywołania do wewnętrznej implementacji <xref:Microsoft.Office.Tools.Word.Document> interfejsu w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="accessing-the-object-model-of-the-host-application"></a>Uzyskiwanie dostępu do modelu obiektów w aplikacji hosta  
 Dostępu do obiektu modelu aplikacji hosta, należy użyć członków wygenerowanej klasy w projekcie. Każda z tych klas odnosi się do obiektu w modelu obiektów programu Excel lub Word i zawierają większość tych samych właściwości, metod i zdarzeń. Na przykład `ThisDocument` klasy w projektach na poziomie dokumentu dla programu Word zawiera większość tych samych elementów członkowskich jako <xref:Microsoft.Office.Interop.Word.Document> obiektu w modelu obiektów programu Word.  
  
 Poniższy przykład kodu pokazuje, jak można użyć modelu obiektów programu Word można zapisać dokumentu, który jest częścią dostosowanie poziomie dokumentu dla programu Word. W tym przykładzie jest przeznaczona do uruchamiania z `ThisDocument` klasy.  
  
```vb  
Me.Save()  
```  
  
```csharp  
this.Save();  
```  
  
 Aby zrobić to samo z poza `ThisDocument` klasy, należy użyć `Globals` do dostępu do obiektu `ThisDocument` klasy. Na przykład dodaniem ten kod do pliku kodu w okienku Akcje, jeśli chcesz dołączyć **zapisać** przycisku w okienku Akcje interfejsu użytkownika.  
  
```vb  
Globals.ThisDocument.Save()  
```  
  
```csharp  
Globals.ThisDocument.Save();  
```  
  
 Ponieważ `ThisDocument` klas uzyskuje większość jego elementów członkowskich z <xref:Microsoft.Office.Tools.Word.Document> element hosta `Save` metodę, która jest wywoływana w tym kodzie to naprawdę <xref:Microsoft.Office.Tools.Word.Document.Save%2A> metody <xref:Microsoft.Office.Tools.Word.Document> element hosta. Ta metoda odpowiada <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metody <xref:Microsoft.Office.Interop.Word.Document> obiektu w modelu obiektów programu Word.  
  
 Aby uzyskać więcej informacji na temat używania modeli obiektów programu Word i Excel, zobacz [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md) i [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).  
  
 Aby uzyskać więcej informacji na temat `Globals` obiektów, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="adding-controls-to-documents"></a>Dodawanie formantów do dokumentów  
 Aby dostosować interfejsu użytkownika dokumentu, można dodać formanty formularzy systemu Windows lub *hostowania formantów* powierzchnię dokumentu. Łącząc różne zestawy formantów i pisanie kodu, formanty można powiązać z danymi, zbiera informacje o użytkowniku i odpowiadania na działania użytkownika.  
  
 Formanty hosta są klas, które rozszerzają niektórych obiektów w modelu obiektów programu Word i Excel. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli hosta zawiera wszystkie funkcje <xref:Microsoft.Office.Interop.Excel.ListObject> w programie Excel. Jednak <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli hosta ma również dodatkowe zdarzenia oraz funkcje powiązania danych.  
  
 Aby uzyskać więcej informacji, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md) i [formantów formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="combining-vba-and-document-level-customizations"></a>Łączenie VBA i dostosowywanie na poziomie dokumentu  
 Kod VBA można użyć w dokumencie, który jest częścią dostosowania poziomie dokumentu. Kod VBA w dokumencie można wywołać z zestawu dostosowania, a projekt, aby włączyć kod VBA w dokumencie, aby wywoływać kod w zestawie dostosowania można również skonfigurować.  
  
 Aby uzyskać więcej informacji, zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="managing-documents-on-a-server"></a>Zarządzanie dokumentami na serwerze  
 Można zarządzać kilka różnych aspektów dostosowań na poziome dokumentu na serwerze, który nie ma programu Microsoft Office Word lub zainstalowany program Microsoft Office Excel. Można na przykład dostępu i modyfikowanie danych w pamięci podręcznej danych dokumentu. Można również zarządzać zestawu dostosowania, który jest skojarzony z dokumentem. Na przykład można programistycznie usunąć zestawu z dokumentu, aby dokument już nie uruchamia kod lub zestawu programowo można dołączyć do dokumentu.  
  
 Aby uzyskać więcej informacji, zobacz [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).  
  
## <a name="customizing-the-user-interface-of-microsoft-office-applications"></a>Dostosowywanie interfejsu użytkownika aplikacji pakietu Microsoft Office  
 Za pomocą dostosowania na poziomie dokumentu, można dostosować interfejsu użytkownika programu Word i Excel w następujący sposób:  
  
-   Dodaj formanty hosta lub formanty formularzy systemu Windows do powierzchni dokumentu.  
  
     Aby uzyskać więcej informacji, zobacz [automatyzacji programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md), [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md), i [formantów formularzy Windows w dokumentach pakietu Office ― omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Dodawanie okienek akcji do dokumentu.  
  
     Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).  
  
-   Dodaj niestandardowe karty do wstążki.  
  
     Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
-   Dodawanie niestandardowych grup wbudowanych kartę na Wstążce.  
  
     Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md).  
  
 Aby uzyskać więcej informacji dotyczących dostosowywania aplikacji interfejsu użytkownika pakietu Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
## <a name="getting-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Pobieranie obiektów rozszerzonych obiektów Office macierzystego w dostosowaniach na poziomie dokumentu  
 Wiele programy obsługi zdarzeń dla zdarzenia Office otrzymywać obiekt Office macierzystego, który reprezentuje skoroszytu, arkusza lub dokument, który wywołał zdarzenie. W niektórych przypadkach można uruchomić kod tylko wtedy, gdy skoroszyt lub dokumentu na poziomie dokumentu dostosowanie zgłoszone zdarzenie. Na przykład w dostosowanie poziomie dokumentu dla programu Excel, możesz uruchomić kodu, gdy użytkownik aktywuje jednego z arkuszy w skoroszycie dostosowane, ale nie w przypadku, gdy użytkownik aktywuje arkusza w innym skoroszycie stanie się być otwarty w tym samym czasie.  
  
 Gdy macierzysty obiekt pakietu Office, można sprawdzić, czy ten obiekt został rozszerzony do *element hosta* lub *kontrolki hosta* w dostosowaniu poziomie dokumentu. Elementów hosta i formantów hosta dostarczone przez typy są [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dodaje funkcjonalność do obiektów, które natywnie istnieje w modelach obiektu Word czy Excel (nazywane *natywny obiektów pakietu Office*). Zbiorczo elementów hosta i formantów hosta są również nazywane *obiektów rozszerzonych*. Aby uzyskać więcej informacji na temat elementów hosta i formantów hosta, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="understanding-the-getvstoobject-and-hasvstoobject-methods"></a>Opis GetVstoObject i HasVstoObject metody  
 Aby przetestować macierzysty obiekt pakietu Office, należy użyć metody HasVstoObject i GetVstoObject w projekcie:  
  
-   Jeśli chcesz określić, czy obiekt natywny Office rozszerzonej obiektu w dostosowaniu, należy użyć metody HasVstoObject. Ta metoda zwraca **true** Jeśli obiekt natywny Office ma obiekt rozszerzone i **false** inaczej.  
  
-   Użyj metody GetVstoObject, jeśli chcesz pobrać rozszerzonej obiekt natywny obiektów pakietu Office. Ta metoda zwraca <xref:Microsoft.Office.Tools.Excel.ListObject>, <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, lub <xref:Microsoft.Office.Tools.Word.Document> obiekt, jeśli określony obiekt natywny Office ma jeden. W przeciwnym razie zwraca GetVstoObject **null**. Na przykład metoda GetVstoObject zwraca <xref:Microsoft.Office.Tools.Word.Document> Jeśli określonego <xref:Microsoft.Office.Interop.Word.Document> jest obiektu źródłowego dla dokumentu w projekcie dokument programu Word.  
  
 W projektach na poziomie dokumentu, nie można użyć GetVstoObject — metoda, aby utworzyć nową <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, lub <xref:Microsoft.Office.Tools.Word.Document> element hosta w czasie wykonywania. Ta metoda służy do istniejących elementów hosta, które są generowane w projekcie w czasie projektowania. Jeśli chcesz utworzyć nowe elementy hosta w czasie wykonywania, należy utworzyć projektów dodatku VSTO. Aby uzyskać więcej informacji, zobacz [programowe ograniczenia elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) i [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="using-the-getvstoobject-and-hasvstoobject-methods"></a>Przy użyciu metody HasVstoObject i GetVstoObject  
 Aby wywołać metodę HasVstoObject i GetVstoObject, użyj metody Globals.Factory.GetVstoObject lub Globals.Factory.HasVstoObject i podaj obiekt natywny Word czy Excel (takie jak <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Worksheet>), który ma zostać przetestowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)   
 [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)  
  
  