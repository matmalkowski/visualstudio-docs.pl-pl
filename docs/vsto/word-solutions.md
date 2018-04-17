---
title: Word rozwiązania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44cd5633d7cc03fb78c6508c24a117a0500fa142
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="word-solutions"></a>Rozwiązania programu Word
  Program Visual Studio udostępnia szablony projektów, które służy do tworzenia Dostosowywanie na poziomie dokumentu i dodatków narzędzi VSTO dla programu Microsoft Office Word. Te rozwiązania umożliwia automatyzowanie programu Word, rozszerzania funkcji programu Word i dostosowywanie interfejsu użytkownika (UI) programu Word. Aby uzyskać więcej informacji na temat różnic między Dostosowywanie na poziomie dokumentu i dodatków VSTO zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
 Ten temat zawiera następujące informacje:  
  
-   [Automatyzowanie programu Word](#automating).  
  
-   [Tworzenie, dostosowywanie na poziomie dokumentu dla programu Word](#doclevel).  
  
-   [Tworzenie dodatków narzędzi VSTO dla programu Word](#applevel).  
  
-   [Dostosowywanie interfejsu użytkownika programu Word](#UI).  
  
##  <a name="automating"></a> Automatyzowanie programu Word  
 Model obiektów programu Word udostępnia wiele typów, które służą do automatyzacji programu Word. Na przykład można programowo Tworzenie tabel, format dokumentów i ustawianie tekstu w zakresach i akapitów. Aby uzyskać więcej informacji, zobacz [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md).  
  
 Podczas tworzenia rozwiązania programu Word w Visual Studio, można również użyć *hosta elementów* i *hostowania formantów* w ramach rozwiązań. Są to obiekty rozszerzających niektóre często używane obiekty w modelu obiektów programu Word, takich jak <xref:Microsoft.Office.Interop.Word.Document> i <xref:Microsoft.Office.Interop.Word.ContentControl> obiektów. Obiekty rozszerzone przypominają obiektów programu Word, które są oparte na, ale Dodaj dodatkowe zdarzenia oraz funkcje powiązania danych do obiektów. Aby uzyskać więcej informacji, zobacz [automatyzacji programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Tworzenie, dostosowywanie na poziomie dokumentu dla programu Word  
 Dostosowanie poziomie dokumentu dla programu Microsoft Office Word składa się z zestawu, który jest skojarzony z określonego dokumentu. Zestaw zazwyczaj rozszerza dokumentu przez dostosowywanie interfejsu użytkownika i automatyzowanie programu Word. W odróżnieniu od VSTO dodatku, który jest skojarzony z programu Word samego, funkcje, które implementuje w dostosowaniu jest dostępna tylko wtedy, gdy skojarzonego dokumentu jest otwarty w programie Word.  
  
 Aby utworzyć projekt dostosowania na poziomie dokumentu dla programu Word, korzystania z szablonów projektu dokument programu Word lub szablon programu Word w **nowy projekt** okno dialogowe programu Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Aby uzyskać więcej informacji o pracy dostosowania jak poziom dokumentu [architektura poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="word-customization-programming-model"></a>Model programowania dostosowania programu Word  
 Podczas tworzenia projektu poziomie dokumentu dla programu Word, Visual Studio wygeneruje klasy o nazwie `ThisDocument`, która stanowi podstawę rozwiązania. Ta klasa reprezentuje dokument, który jest skojarzony z rozwiązania, a jego stanowi punkt wyjścia do pisania kodu.  
  
 Aby uzyskać więcej informacji na temat `ThisDocument` klasy i innych funkcji można użyć w projekcie poziomie dokumentu, zobacz [programowania dostosowań na poziome dokumentu](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Tworzenie dodatków narzędzi VSTO dla programu Word  
 Dodatku VSTO dla programu Microsoft Office Word składa się z zestawu, który jest ładowany przez program Word. Zestaw zazwyczaj rozszerza Word, dostosowując interfejsu użytkownika i dzięki automatyzacji programu Word. W przeciwieństwie do dostosowania na poziomie dokumentu, który jest skojarzony z określonego dokumentu, funkcje, które implementuje w dodatku VSTO nie jest ograniczone do pojedynczego dokumentu.  
  
 Do tworzenia projektów dodatku VSTO dla programu Word, użyj dodatku programu Word szablonów projektu w **nowy projekt** okno dialogowe programu Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Aby uzyskać ogólne informacje na temat działania dodatków VSTO, zobacz [dodatki architektura VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="word-add-in-programming-model"></a>Word — w modelu programowania  
 Podczas tworzenia projektów dodatku VSTO programu Word w Visual Studio generuje klasy o nazwie `ThisAddIn`, która stanowi podstawę rozwiązania. Ta klasa stanowi punkt wyjścia do pisania kodu, a także przedstawia model obiektów programu Word z dodatku VSTO.  
  
 Aby uzyskać więcej informacji na temat `ThisAddIn` klasy i innych funkcji można używać w dodatku VSTO, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Dostosowywanie interfejsu użytkownika programu Word  
 Istnieją różne sposoby dostosowania interfejsu użytkownika programu Word. Niektóre opcje są dostępne dla wszystkich typów projektów i inne opcje są dostępne tylko dla dodatków VSTO lub dostosowywanie na poziomie dokumentu.  
  
### <a name="options-for-all-project-types"></a>Opcje dla wszystkich typów projektów  
 W poniższej tabeli wymieniono opcje dostosowywania dostępne do dostosowania na poziomie dokumentu i dodatków VSTO.  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Dostosowywanie Wstążki.|[Wstążka — omówienie](../vsto/ribbon-overview.md)|  
|Dodaj formanty formularzy systemu Windows lub formanty rozszerzone programu Word do niestandardowych dokumentu (na poziomie dokumentu dostosowanie) lub do otwartego dokumentu (w przypadku dodatku VSTO).|[Instrukcje: Dodawanie kontrolek Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|  
  
### <a name="options-for-document-level-customizations"></a>Opcje na poziomie dokumentu  
 W poniższej tabeli wymieniono opcje dostosowania, które są dostępne tylko na poziomie dokumentu.  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Dodawanie okienek akcji do dokumentu.|[Okienko akcji — omówienie](../vsto/actions-pane-overview.md)<br /><br /> [Instrukcje: Dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Dodaj formanty rozszerzone XMLNode i XMLNodes do powierzchni dokumentu.|[Instrukcje: Dodawanie kontrolek XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Instrukcje: Dodawanie kontrolek XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Opcje dotyczące dodatków narzędzi VSTO  
 W poniższej tabeli wymieniono opcje dostosowania, które są dostępne tylko dla dodatków VSTO.  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Tworzenie niestandardowego okienka zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)|Zawiera omówienie głównych typów dostarczonych przez model obiektów programu Word.|  
|[Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)|Zawiera informacje o rozszerzonych obiektów (dostarczonych przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) używanego w rozwiązania programu Word.|  
|[Kontrolki Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)|W tym artykule opisano, jak dodać formanty formularzy systemu Windows do dokumentów programu Word.|  
|[Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Przedstawia sposób tworzenia podstawowego dostosowywania poziomie dokumentu dla programu Word.|  
|[Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Pokazuje, jak utworzyć podstawowy dodatku VSTO dla programu Word.|  
|[Przewodnik: Dodawanie kontrolek do dokumentów w czasie wykonywania w dodatku narzędzi VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Pokazuje, jak dodać systemu Windows stanowi przycisk i a <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do dokumentu w czasie wykonywania za pomocą dodatku VSTO.|  
|[Word 2010 w programowanie Office](http://go.microsoft.com/fwlink/?LinkId=199020)|Zawiera łącza do artykułów i dokumentacji o tworzenie rozwiązania programu Word (nie odnoszą się do rozwoju pakietu Office przy użyciu programu Visual Studio).|  
  
  