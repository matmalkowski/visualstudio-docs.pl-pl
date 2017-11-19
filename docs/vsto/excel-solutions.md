---
title: "W programie Excel rozwiązania | Dokumentacja firmy Microsoft"
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
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
ms.assetid: 34444d54-d7b6-479a-b5b7-a946267081e9
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 46f484bc9dc597bc43ea4e7e2474d5b7efcb1f3c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="excel-solutions"></a>Rozwiązania programu Excel
  Program Visual Studio udostępnia szablony projektów, które służy do tworzenia Dostosowywanie na poziomie dokumentu i dodatków narzędzi VSTO dla programu Microsoft Office Excel. Te rozwiązania umożliwia automatyzowanie programu Excel, rozszerzanie funkcji programu Excel i dostosowanie interfejsu użytkownika (UI) programu Excel. Aby uzyskać więcej informacji na temat różnic między Dostosowywanie na poziomie dokumentu i dodatków VSTO zobacz [rozwój rozwiązań Office ― omówienie &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
 Ten temat zawiera następujące informacje:  
  
-   [Automatyzowanie programu Excel](#automating).  
  
-   [Tworzenie dostosowań na poziomie dokumentu dla programu Excel](#doclevel).  
  
-   [Tworzenie dodatków narzędzi VSTO dla programu Excel](#applevel).  
  
-   [Dostosowywanie interfejsu użytkownika programu Excel](#UI).  
  
##  <a name="automating"></a>Automatyzowanie programu Excel  
 Model obiektów programu Excel udostępnia wiele typów, które służą do automatyzacji programu Excel. Na przykład możesz można programowo Tworzenie wykresów, formatowania arkuszy i ustaw wartości zakresów i komórek. Aby uzyskać więcej informacji, zobacz [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).  
  
 Podczas tworzenia rozwiązania programu Excel w programie Visual Studio, można również użyć *hosta elementów* i *hostowania formantów* w ramach rozwiązań. Są to obiekty, które rozszerzają niektórych obiektów często używane w modelu obiektów programu Excel, takich jak <xref:Microsoft.Office.Interop.Excel.Worksheet> i <xref:Microsoft.Office.Interop.Excel.Range> obiektów. Obiekty rozszerzone przypominają obiektami programu Excel, które są oparte na, ale Dodaj dodatkowe zdarzenia oraz funkcje powiązania danych do obiektów. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a>Tworzenie dostosowań na poziomie dokumentu dla programu Excel  
 Dostosowanie poziomie dokumentu dla programu Microsoft Office Excel składa się z zestawu, który jest skojarzony z określonym skoroszytu. Zestaw zazwyczaj rozszerza skoroszyt, dostosowując interfejsu użytkownika i dzięki automatyzacji programu Excel. W odróżnieniu od VSTO dodatku, który jest skojarzony z programu Excel samego, funkcje, które implementuje w dostosowaniu jest dostępna tylko wtedy, gdy skojarzony skoroszyt jest otwarty w programie Excel.  
  
 Aby utworzyć projekt dostosowania na poziomie dokumentu dla programu Excel, korzystania z szablonów projektu skoroszyt programu Excel lub szablon programu Excel w **nowy projekt** okno dialogowe programu Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Aby uzyskać więcej informacji na temat dostosowania jak dokument na poziomie, zobacz [architektura poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="excel-customization-programming-model"></a>Model programowania dostosowania programu Excel  
 Podczas tworzenia projektu poziomie dokumentu dla programu Excel, programu Visual Studio generuje kilka klas, które są podstawę rozwiązania: `ThisWorkbook`, `Sheet1`, `Sheet2`, i `Sheet3`. Te klasy reprezentujące skoroszytu i arkuszy, które są skojarzone z rozwiązania i stanowią punkt początkowy pisania kodu.  
  
 Aby uzyskać więcej informacji o tych wygenerowane klasy i innych funkcji można użyć w projekcie poziomie dokumentu zobacz [programowania dostosowań na poziome dokumentu](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a>Tworzenie dodatków narzędzi VSTO dla programu Excel  
 Dodatku VSTO dla programu Microsoft Office Excel składa się z zestawu, który jest ładowany przez program Microsoft Excel. Zestaw zazwyczaj rozszerza programu Excel, dostosowując interfejsu użytkownika i dzięki automatyzacji programu Excel. W przeciwieństwie do dostosowania na poziomie dokumentu, który jest skojarzony z określonym skoroszytu, funkcje, które implementuje w dodatku VSTO nie jest ograniczone do dowolnego pojedynczego skoroszytu.  
  
 Aby utworzyć projekt dodatku VSTO dla programu Excel, korzystania z szablonów projektu skoroszyt programu Excel lub szablon programu Excel w **nowy projekt** okno dialogowe programu Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Aby uzyskać ogólne informacje na temat działania dodatków VSTO, zobacz [dodatki architektura VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: automatyzacji programu PowerPoint z dodatek programu Excel?](http://go.microsoft.com/fwlink/?LinkID=130300).  
  
### <a name="excel-add-in-programming-model"></a>Dodatek modelu programowania w programie Excel  
 Podczas tworzenia projektów dodatku VSTO programu Excel, programu Visual Studio wygeneruje klasy o nazwie `ThisAddIn`, która stanowi podstawę rozwiązania. Ta klasa stanowi punkt wyjścia do pisania kodu, a także przedstawia model obiektów programu Excel do Twojej dodatku VSTO.  
  
 Aby uzyskać więcej informacji na temat `ThisAddIn` klasy i inne funkcje programu Visual Studio można używać w dodatku VSTO, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a>Dostosowywanie interfejsu użytkownika programu Excel  
 Istnieją różne sposoby dostosowania interfejsu użytkownika programu Excel. Niektóre opcje są dostępne dla wszystkich typów projektów i inne opcje są dostępne tylko dla dodatków VSTO lub dostosowywanie na poziomie dokumentu.  
  
### <a name="options-for-all-project-types"></a>Opcje dla wszystkich typów projektów  
 W poniższej tabeli wymieniono opcje dostosowywania dostępne do dostosowania na poziomie dokumentu i dodatków VSTO.  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Dostosowywanie Wstążki.|[Wstążka ― omówienie](../vsto/ribbon-overview.md)|  
|Dodaj formanty formularzy systemu Windows lub formanty rozszerzone programu Excel do arkusza w skoroszycie dostosowane do dostosowania poziomie dokumentu lub w dowolnym otwarty skoroszyt dodatku VSTO.|[Porady: dodawanie formantów do dokumentów pakietu Office formularzy systemu Windows](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Porady: dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Porady: dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Porady: dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-document-level-customizations"></a>Opcje na poziomie dokumentu  
 W poniższej tabeli wymieniono opcje dostosowania, które są dostępne tylko na poziomie dokumentu.  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Dodawanie okienek akcji do skoroszytu.|[Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)<br /><br /> [Porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Dodaj formanty rozszerzone zakresu, które są mapowane do węzłów XML do arkusza.|[Porady: dodawanie formantów XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Opcje dotyczące dodatków narzędzi VSTO  
 W poniższej tabeli wymieniono opcje dostosowania, które są dostępne tylko dla dodatków VSTO.  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Tworzenie niestandardowego okienka zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)|Zawiera omówienie głównych typów dostarczonych przez model obiektów programu Excel.|  
|[Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)|Zawiera informacje o rozszerzonych obiektów (dostarczonych przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) używanego w rozwiązania programu Excel.|  
|[Globalizacja i lokalizacja rozwiązania programu Excel](../vsto/globalization-and-localization-of-excel-solutions.md)|Zawiera informacje o uwagi dotyczące rozwiązania programu Excel, które będą uruchamiane na komputerach z systemem innym niż angielski ustawienia dla systemu Windows.|  
|[Formanty formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|W tym artykule opisano, jak dodać formanty formularzy systemu Windows w arkuszach programu Excel.|  
|[Wskazówki: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Przedstawia sposób tworzenia podstawowego dostosowywania poziomie dokumentu dla programu Excel.|  
|[Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)|Pokazuje, jak utworzyć podstawowy dodatku VSTO dla programu Excel.|  
|[Wskazówki: Dodawanie formantów do arkusza w czasie wykonywania w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)|Pokazuje, jak dodawanie przycisku formularzy systemu Windows, <xref:Microsoft.Office.Tools.Excel.NamedRange>, a <xref:Microsoft.Office.Tools.Excel.ListObject> do arkusza w czasie wykonywania za pomocą dodatku VSTO.|
|[Opis współtworzenia i dodatki](./understanding-coauthoring-and-addins.md)|W tym artykule opisano zmiany może być konieczne dokonanie rozwiązań do uwzględnienia współtworzenia.|  
|[Excel 2010 w programowanie Office](http://go.microsoft.com/fwlink/?LinkId=199011)|Zawiera łącza do artykułów i dokumentacji informacje o opracowywaniu rozwiązań programu Excel. Nie są specyficzne dla programowanie Office w programie Visual Studio.|  
  
  