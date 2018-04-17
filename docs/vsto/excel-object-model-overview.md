---
title: Przegląd modelu obiektów w programie Excel | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6b700d3834cf432ff9af2ec17e1daa3011763cac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="excel-object-model-overview"></a>Model obiektu Excel ― Omówienie
  Umożliwiające tworzenie rozwiązań, które używają programu Microsoft Office Excel, możesz użyć obiektów dostarczanych przez model obiektów programu Excel. W tym temacie przedstawiono najważniejsze obiektów:  
  
-   <xref:Microsoft.Office.Interop.Excel.Application>  
  
-   <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Interop.Excel.Range>  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Model obiektu jest ściśle zgodna interfejsu użytkownika. <xref:Microsoft.Office.Interop.Excel.Application> Obiekt reprezentuje całej aplikacji, a każdy <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu zawiera kolekcję `Worksheet` obiektów. Dostępne jest głównych abstrakcji, który reprezentuje komórek <xref:Microsoft.Office.Interop.Excel.Range> obiektu, który umożliwia pracę z pojedynczych komórek lub grupy komórek.  
  
 Oprócz modelu obiektów programu Excel, podaj projektów pakietu Office w Visual Studio *hosta elementów* i *hostowania formantów* który rozszerzać niektórych obiektów w modelu obiektów programu Excel. Obiekty hosta i formantów hosta przypominają obiektami programu Excel, które rozszerzają, ale ma także dodatkowe funkcje, takie jak możliwości wiązania danych oraz dodatkowe zdarzenia. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md) i [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
 Ten temat zawiera krótki przegląd modelu obiektów programu Excel. Dla zasobów można znaleźć więcej informacji na temat całego modelu obiektów programu Excel, zobacz [przy użyciu dokumentacji modelu obiektów programu Excel](#ExcelOMDocumentation).  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: Użyj obsługi zdarzeń w programie Excel 2007 dodatek?](http://go.microsoft.com/fwlink/?LinkID=130291), i [jak czy I: Użyj kształty, aby utworzyć wykres bąbelkowy w programie Excel? ](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## <a name="accessing-objects-in-an-excel-project"></a>Uzyskiwanie dostępu do obiektów w projekcie programu Excel  
 Podczas tworzenia nowego projektu dodatku VSTO dla programu Excel, programu Visual Studio automatycznie tworzy ThisAddIn.vb lub ThisAddIn.cs pliku kodu. Dostęp do obiektu aplikacji przy użyciu `Me.Application` lub `this.Application`.  
  
 Podczas tworzenia nowego projektu poziomie dokumentu dla programu Excel, istnieje możliwość tworzenia nowego projektu skoroszyt programu Excel lub szablon programu Excel. Visual Studio automatycznie tworzy następujące pliki kodu w nowego projektu programu Excel dla projektów zarówno skoroszyt i szablonu.  
  
|Visual Basic|C#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.VB|Sheet1.CS|  
|Sheet2.VB|Sheet2.CS|  
|Sheet3.VB|Sheet3.CS|  
  
 Można użyć `Globals` klasy w projekcie, aby uzyskać dostęp do `ThisWorkbook`, `Sheet1`, `Sheet2`, lub `Sheet3` z poza odpowiedniej klasy. Aby uzyskać więcej informacji, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md). Następujące przykładowe wywołania <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metody `Sheet1` niezależnie od tego, czy kod jest umieszczony w jednym z `Sheet` *n* klasy lub `ThisWorkbook` klasy.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]  
  
 Ponieważ dane w dokumencie programu Excel jest zaawansowaną strukturę, model obiektów jest hierarchicznej i prostego. Excel oferuje setki obiektów, z którymi warto interakcji, ale można uzyskać dobry początek w modelu obiektu koncentrujących się na bardzo małego podzbioru dostępnych obiektów. Te obiekty obejmują następujące cztery:  
  
-   Aplikacja  
  
-   skoroszyt  
  
-   arkusz  
  
-   Zakres  
  
 Większość pracy przy użyciu programu Excel koncentruje się wokół tych czterech obiektów i ich elementy członkowskie.  
  
### <a name="application-object"></a>Obiekt aplikacji  
 Excel <xref:Microsoft.Office.Interop.Excel.Application> obiekt reprezentuje sama aplikacja programu Excel. <xref:Microsoft.Office.Interop.Excel.Application> Obiekt ujawnia dużą ilość informacji o uruchomionych aplikacji, opcje zastosowane do tego wystąpienia, a następnie otwórz obiekty użytkownika w ramach wystąpienia.  
  
> [!NOTE]  
>  Nie należy ustawiać <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> właściwość <xref:Microsoft.Office.Interop.Excel.Application> obiektu w programie Excel, aby **false**. Ustawienie tej właściwości na wartość false zapobiega wywoływanie żadnych zdarzeń, w tym zdarzenia formanty hosta programu Excel.  
  
### <a name="workbook-object"></a>Obiekt skoroszytu  
 <xref:Microsoft.Office.Interop.Excel.Workbook> Obiekt reprezentuje pojedynczy skoroszytu w aplikacji Excel.  
  
 Narzędzia Office development w Visual Studio rozszerza <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu podając <xref:Microsoft.Office.Tools.Excel.Workbook> typu. Tego typu umożliwia dostęp do wszystkich funkcji <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu. Aby uzyskać więcej informacji, zobacz [element hosta skoroszytu](../vsto/workbook-host-item.md).  
  
### <a name="worksheet-object"></a>Obiekt arkusza  
 <xref:Microsoft.Office.Interop.Excel.Worksheet> Obiektu jest elementem członkowskim <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekcji. Wiele właściwości, metod i zdarzeń <xref:Microsoft.Office.Interop.Excel.Worksheet> identyczne lub podobne do elementów członkowskich udostępniane przez <xref:Microsoft.Office.Interop.Excel.Application> lub <xref:Microsoft.Office.Interop.Excel.Workbook> obiektów.  
  
 Program Excel oferuje <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji jako właściwość <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu. Każdy element członkowski <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji jest <xref:Microsoft.Office.Interop.Excel.Worksheet> lub <xref:Microsoft.Office.Interop.Excel.Chart> obiektu.  
  
 Rozszerzanie narzędzi programowania pakietu Office w Visual Studio <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu podając <xref:Microsoft.Office.Tools.Excel.Worksheet> typu. Tego typu umożliwia dostęp do wszystkich funkcji <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu, a także nowe funkcje, takie jak możliwość hosta zarządzanego kontrolki i obsługę nowych zdarzeń. Aby uzyskać więcej informacji, zobacz [element hosta arkusza](../vsto/worksheet-host-item.md).  
  
### <a name="range-object"></a>Obiekt zakresu  
 <xref:Microsoft.Office.Interop.Excel.Range> Obiekt jest obiektem użyje większość w aplikacjach programu Excel. Zanim można manipulować dowolny region w programie Excel, należy go jako express <xref:Microsoft.Office.Interop.Excel.Range> obiektu i pracować z metody i właściwości tego zakresu. A <xref:Microsoft.Office.Interop.Excel.Range> obiekt reprezentuje komórkę, wiersz, kolumny, zaznaczonych komórek, który zawiera jeden lub więcej bloków komórek, które może być może nie mieć postać ciągłą lub nawet grupę komórek na wiele arkuszy.  
  
 Visual Studio rozszerza <xref:Microsoft.Office.Interop.Excel.Range> obiektu podając <xref:Microsoft.Office.Tools.Excel.NamedRange> i <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> typów. Te typy mają te same funkcje co większość <xref:Microsoft.Office.Interop.Excel.Range> obiektu, a także nowe funkcje, takie jak możliwość powiązania danych i nowych zdarzeń. Aby uzyskać więcej informacji, zobacz [namedrange — formant](../vsto/namedrange-control.md) i [xmlmappedrange — formant](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a> Korzystając z dokumentacji modelu obiektów programu Excel  
 Aby uzyskać pełne informacje o modelu obiektów programu Excel mogą odwoływać się do odwołania podstawowego zestawu międzyoperacyjnego (PIA) programu Excel i odwołanie modelu obiektu języka VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Odwołanie do podstawowego zestawu międzyoperacyjnego  
 Dokumentacja odwołania Excel PIA opisano typy w podstawowego zestawu międzyoperacyjnego dla programu Excel. Niniejsza dokumentacja jest dostępna z następującej lokalizacji: [odwołanie do programu Excel 2010 podstawowego zestawu Interop](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
 Aby uzyskać więcej informacji dotyczących projektu PIA programu Excel, takie jak różnice między klasy i interfejsy PIA i implementowania zdarzeń w PIA, zobacz [Przegląd klasy i interfejsy Office podstawowe zestawy międzyoperacyjne](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>Odwołania do modelu obiektu VBA  
 Odwołania do modelu obiektu VBA dokumentów modelu obiektów programu Excel, jak jest narażony na język Visual Basic dla kodu aplikacji (VBA). Aby uzyskać więcej informacji, zobacz [odwołania do modelu obiektu programu Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 Wszystkie obiekty i elementów członkowskich w odwołania do modelu obiektu VBA odpowiadają typy i składniki w PIA programu Excel. Na przykład obiekt arkusza w odwołania do modelu obiektu VBA odpowiada <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu w PIA programu Excel. Odwołania do modelu obiektu VBA zapewnia przykłady kodu dla większości właściwości, metod i zdarzeń, jednak należy translacji kod VBA w niniejszej dokumentacji Visual Basic lub Visual C#, jeśli chcesz używać ich w projekcie programu Excel, który utworzono przy użyciu programu Visual Studio.  
  
### <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Rozwiązania programu Excel](../vsto/excel-solutions.md)|Wyjaśnia sposób tworzenia Dostosowywanie na poziomie dokumentu i dodatków narzędzi VSTO dla programu Microsoft Office Excel.|  
|[Praca z zakresami](../vsto/working-with-ranges.md)|Przykłady, które przedstawiają sposób wykonywania typowych zadań z zakresami.|  
|[Praca z arkuszami](../vsto/working-with-worksheets.md)|Przykłady, które przedstawiają sposób wykonywania typowych zadań z arkuszami.|  
|[Praca ze skoroszytami](../vsto/working-with-workbooks.md)|Przykłady, które przedstawiają sposób wykonywania typowych zadań ze skoroszytami.|  
  
  