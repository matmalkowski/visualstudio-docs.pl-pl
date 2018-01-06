---
title: Obiekty hosta i informacje o formantach hosta | Dokumentacja firmy Microsoft
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
- host controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- host items [Office development in Visual Studio]
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], listed
- Excel [Office development in Visual Studio], host items
- host controls [Office Development in Visual Stuio], naming
- host controls [Office development in Visual Studio]
- host controls [Office development in Visual Studio], about host controls
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host items [Office development in Visual Studio], about host items
- host items [Office development in Visual Studio], listed
- documents [Office development in Visual Studio], host items
- data binding [Office development in Visual Studio], host controls
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], deleting
ms.assetid: 0601fed9-1a5b-4504-95ed-c6a2ddb710d9
caps.latest.revision: "100"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0a85f69ce67afdb4e1138c75b7c939be3980453f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="host-items-and-host-controls-overview"></a>Przegląd obiektów hosta i kontrolek hosta
  Obiekty hosta i formantów hosta są typy, które pomagają modelu programowania rozwiązań pakietu Office, które są tworzone za pomocą narzędzi programowania pakietu Office w Visual Studio. Obiekty hosta i formantów hosta upewnij się, interakcji z modeli obiektów Microsoft Office Word i Microsoft Office Excel, które są oparte na modelu COM, więcej takich jak interakcji z obiektów zarządzanych, takich jak formanty formularzy systemu Windows.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="host-items"></a>Obiekty hosta  
 Obiekty hosta są typy, które znajdowały się u góry hierarchii modelu obiektów w projektach pakietu Office. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Definiuje następujące elementy hosta dla programu Word i Excel rozwiązań:  
  
-   <xref:Microsoft.Office.Tools.Word.Document>  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 Rozszerza każdego typu obiektu, który istnieje w sposób macierzysty w modelu obiektów programu Word i Excel, nazywany *obiekt natywny Office*. Na przykład <xref:Microsoft.Office.Tools.Word.Document> rozszerza element hosta <xref:Microsoft.Office.Interop.Word.Document> obiektu, który jest zdefiniowany w podstawowego zestawu międzyoperacyjnego dla programu Word.  
  
 Obiekty hosta zazwyczaj mają te same funkcje podstawowe jako odpowiednich obiektów pakietu Office, ale jest rozszerzona o następujące funkcje:  
  
-   Zdolność do obsługi zarządzane formanty, w tym formanty hosta i formantów formularzy systemu Windows.  
  
-   Bardziej rozbudowane modele zdarzeń. Niektóre zdarzenia dokumentów, skoroszytów i arkuszy w macierzystym modele obiektów programu Word i Excel pojawienia się tylko na poziomie aplikacji. Obiekty hosta Podaj te zdarzenia na poziomie dokumentu, dzięki czemu możliwe jest łatwiejsze do obsługi zdarzeń dla określonego dokumentu.  
  
### <a name="understanding-host-items-in-document-level-projects"></a>Opis elementów hosta w projektach na poziomie dokumentu  
 W projektach na poziomie dokumentu elementy hosta podaj punkt wejścia dla kodu i mają projektantów ułatwiające opracowanie rozwiązania.  
  
 <xref:Microsoft.Office.Tools.Word.Document> i <xref:Microsoft.Office.Tools.Excel.Worksheet> elementy hosta skojarzony projektantów, które są wizualną reprezentację dokument lub arkusz, takich jak projektant formularzy systemu Windows. Ten Projektant służy do zmiany zawartości dokumentu lub arkusz bezpośrednio w Word czy Excel i przeciągnij formanty na powierzchnię projektu. Aby uzyskać więcej informacji, zobacz [element hosta dokumentu](../vsto/document-host-item.md) i [element hosta arkusza](../vsto/worksheet-host-item.md).  
  
 <xref:Microsoft.Office.Tools.Excel.Workbook> Element hosta nie działa jako kontener dla formantów interfejsu użytkownika. Zamiast tego projektanta dla tego elementu hosta działa jako składnik na pasku zadań, co pozwala na przeciągnij składnik, takich jak <xref:System.Data.DataSet>, na jego powierzchnię projektu. Aby uzyskać więcej informacji, zobacz [element hosta skoroszytu](../vsto/workbook-host-item.md).  
  
 Obiekty hosta nie można utworzyć programowo w projektach na poziomie dokumentu. Zamiast tego należy użyć `ThisDocument`, `ThisWorkbook`, lub `Sheet`  *n*  klasy, które Visual Studio automatycznie generuje w projekcie w czasie projektowania. Te wygenerowane klasy pochodzi od elementów hosta i stanowią punkt wejścia kodu. Aby uzyskać więcej informacji, zobacz [programowe ograniczenia elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="understanding-host-items-in-vsto-add-in-projects"></a>Opis elementów hosta w projektów dodatku VSTO  
 Podczas tworzenia dodatku VSTO, nie masz dostępu do żadnych elementów hosta domyślnie. Jednak możesz wygenerować <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, i <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementów w programach Word i dodatków VSTO programu Excel w czasie wykonywania.  
  
 Po wygenerowaniu elementu hosta mogą wykonywać zadania, takie jak dodawanie formantów do dokumentów. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="host-controls"></a>Formanty hosta  
 Formanty hosta rozszerzyć różnych obiektów interfejsu użytkownika w programach Word i Excel modele obiektów, takich jak Microsoft.Office.Interop.Word.ContentControl i <xref:Microsoft.Office.Interop.Excel.Range> obiektów.  
  
 Projekty programu Excel dostępne są następujące kontrolki hosta:  
  
-   [Kontrolka wykresu](../vsto/chart-control.md)  
  
-   [ListObject, kontrolka](../vsto/listobject-control.md)  
  
-   [NamedRange, kontrolka](../vsto/namedrange-control.md)  
  
-   [XmlMappedRange, kontrolka](../vsto/xmlmappedrange-control.md)  
  
 Projekty programu Word dostępne są następujące kontrolki hosta:  
  
-   [Bookmark, kontrolka](../vsto/bookmark-control.md)  
  
-   [Kontrolki zawartości](../vsto/content-controls.md)  
  
-   [XMLNode, kontrolka](../vsto/xmlnode-control.md)  
  
-   [XMLNodes, kontrolka](../vsto/xmlnodes-control.md)  
  
 Formanty hosta, które są dodawane do dokumentów pakietu Office przypominają natywny obiektów pakietu Office; Formanty hosta jednak dodatkowe funkcje, w tym zdarzenia oraz funkcje do wiązania danych. Na przykład, kiedy zachodzi potrzeba przechwytywania zdarzeń natywny <xref:Microsoft.Office.Interop.Excel.Range> obiektów w programie Excel, najpierw musi obsługiwać zdarzenia zmiany arkusza. Następnie należy określić, czy zmiana została wprowadzona w <xref:Microsoft.Office.Interop.Excel.Range>. Z kolei <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli hosta ma <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> zdarzenie, które można obsługiwać bezpośrednio.  
  
 Relacja między elementem hosta i formantów hosta jest bardzo podobna do relacji między formantami formularza systemu Windows i formularze systemu Windows. Tak jak będzie umieścić polu tekstowym na formularzu systemu Windows, umieść <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolować na <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta. Na poniższej ilustracji przedstawiono relacje między elementami hosta i formantów hosta.  
  
 ![Relacja między elementami hosta i formantów hosta](../vsto/media/hostitemscontrols.png "relacji między elementami hosta i formantów hosta")  
  
 Umożliwia także formanty formularzy systemu Windows w ramach rozwiązań pakietu Office przez dodanie ich bezpośrednio do powierzchni dokument programu Word i Excel. Aby uzyskać więcej informacji, zobacz [formantów formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
> [!NOTE]  
>  Dodawanie formantów hosta lub formanty formularzy systemu Windows do dokumentu programu Word nie jest obsługiwane.  
  
### <a name="adding-host-controls-to-your-documents"></a>Dodawanie hosta formantów do dokumentów  
 W projektach na poziomie dokumentu można dodać hosta formantów do dokumentów programu Word lub arkuszy programu Excel w czasie projektowania w następujący sposób:  
  
-   Dodaj formanty hosta do dokumentu w czasie projektowania w taki sam sposób należy dodać obiekt natywny.  
  
-   Przeciągnij formanty hosta z **przybornika** na dokumentów i arkuszy. Formanty hosta programu Excel są dostępne w **formanty Excel** kartę Projekty programu Excel i Word hosta formanty są dostępne w **formanty Word** WE projekty programu Word.  
  
-   Przeciągnij formanty hosta z **źródeł danych** okna na dokumentów i arkuszy. Umożliwia dodawanie formantów, które są już powiązane z danymi. Aby uzyskać więcej informacji, zobacz [wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 W poziomie dokumentu i projektów dodatku VSTO można również dodać niektóre formanty hosta do dokumentów w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Aby uzyskać więcej informacji o sposobie dodawania hosta formantów do dokumentów zobacz następujące tematy:  
  
-   [Instrukcje: Dodawanie kontrolek wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)  
  
-   [Instrukcje: Dodawanie kontrolek ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)  
  
-   [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  
  
-   [Instrukcje: Dodawanie kontrolek XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)  
  
-   [Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  
  
-   [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)  
  
-   [Instrukcje: Dodawanie kontrolek XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)  
  
-   [Instrukcje: Dodawanie kontrolek XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)  
  
### <a name="naming-host-controls"></a>Formanty hosta nazewnictwa  
 Przeciągnięcie kontrolką hosta z **przybornika** do dokumentu, kontrolka jest automatycznie o nazwie przy użyciu typu formantu z numeru przyrostowej na końcu. Na przykład, są nazywane zakładki **bookmark1**, **bookmark2**i tak dalej. Jeśli używasz funkcji natywnego programu Word czy Excel można dodać formantu, możesz zapewnić go określonej nazwy w momencie jego tworzenia. Formanty można również zmienić, zmieniając wartość **nazwa** właściwości w **właściwości** okna.  
  
> [!NOTE]  
>  Nie można użyć słowa zastrzeżone do nazwy hosta formantów. Na przykład, jeśli dodasz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli do arkusza i Zmień nazwę, aby **systemu**, wystąpią błędy podczas kompilowania projektu.  
  
### <a name="deleting-host-controls"></a>Usuwanie kontrolek hosta  
 W projektach na poziomie dokumentu można usunąć formanty hosta w czasie projektowania, wybierając kontrolki w arkuszu programu Excel lub dokumentu programu Word i naciskając klawisz Delete. Jednak należy użyć **Definiowanie nazwy** okno dialogowe w programie Excel, aby usunąć <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki.  
  
 Jeśli formant host zostanie dodany do dokumentu w czasie projektowania, nie należy usuwać ją programowo w czasie wykonywania, ponieważ podczas kolejnej próby użycia formantu w kodzie, jest zgłaszany wyjątek. `Delete` Metody kontroli hosta spowoduje usunięcie tylko formanty hosta, które są dodawane do dokumentu w czasie wykonywania. Jeśli należy wywołać `Delete` metody kontroli hosta, który został utworzony w czasie projektowania, jest zgłaszany wyjątek.  
  
 Na przykład <xref:Microsoft.Office.Tools.Excel.NamedRange.Delete%2A> metody <xref:Microsoft.Office.Tools.Excel.NamedRange> usuwa tylko pomyślnie <xref:Microsoft.Office.Tools.Excel.NamedRange> jeśli programowo został dodany do arkusza, znany jako dynamicznie tworzenie kontrolki hosta. Formanty hosta utworzony dynamicznie może zostać także usunięty przez przekazanie nazwa formantu do `Remove` metody <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> lub <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Jeśli użytkownicy końcowi Usuń kontroli hosta z dokumentu w czasie wykonywania, rozwiązanie może zakończyć się niepowodzeniem w nieoczekiwany sposób. Funkcje ochrony dokumentu programu Word i Excel umożliwia ochronę przed usunięciem kontrolki hosta. Aby uzyskać więcej informacji, zobacz [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md).  
  
> [!NOTE]  
>  Nie usuwaj programowo formantów w trakcie `Shutdown` obsługi zdarzeń w dokumencie lub arkusz. Elementy interfejsu użytkownika nie będą dostępne podczas `Shutdown` zdarzenie. Jeśli chcesz usunąć formanty przed zamknięciem aplikacji, Dodaj swój kod do innego programu obsługi zdarzeń takich jak `BeforeClose` lub `BeforeSave`.  
  
### <a name="programming-against-host-control-events"></a>Programowanie w odniesieniu do zdarzeń dotyczących formantów hosta  
 Dodawanie zdarzeń jest jeden sposób, że kontrolki hosta rozszerzyć obiektów pakietu Office. Na przykład <xref:Microsoft.Office.Interop.Excel.Range> obiektu w programie Excel i <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu w programie Word nie mają zdarzeń, ale [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rozszerza tych obiektów przez dodanie programowalny zdarzenia. Masz dostęp i kodu w odniesieniu do tych zdarzeń taki sam sposób uzyskać dostępu do zdarzeń formantów na formularzach systemu Windows: za pomocą listy rozwijanej zdarzeń w Visual Basic i strony właściwości zdarzeń w języku C#. Aby uzyskać więcej informacji, zobacz [wskazówki: Programowanie przed zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
> [!NOTE]  
>  Nie należy ustawiać <xref:Microsoft.Office.Interop.Excel._Application.EnableEvents%2A> właściwość <xref:Microsoft.Office.Interop.Excel.Application> obiektu w programie Excel, aby **false**. Ustawienie tej właściwości na **false** uniemożliwia wywoływanie żadnych zdarzeń, w tym zdarzenia formanty hosta programu Excel.  
  
## <a name="see-also"></a>Zobacz też  
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programowania dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Powiązywanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  