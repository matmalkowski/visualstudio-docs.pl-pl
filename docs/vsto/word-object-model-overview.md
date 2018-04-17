---
title: Omówienie modelu obiektu Word | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word object model
- Word [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Word
- objects [Office development in Visual Studio], Office object models
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aae1d5648b2db72a4e5ddd6b792f2b3aed846e76
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="word-object-model-overview"></a>Model obiektu Word — Omówienie
  Podczas opracowywania rozwiązań programu Word w Visual Studio, interakcji z modelu obiektów programu Word. Ten model obiektów składa się z klasy i interfejsy, które znajdują się w podstawowego zestawu międzyoperacyjnego dla programu Word i są zdefiniowane w <xref:Microsoft.Office.Interop.Word> przestrzeni nazw.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Ten temat zawiera krótki przegląd modelu obiektów programu Word. Dla zasobów można znaleźć więcej informacji na temat całego modelu obiektów programu Word, zobacz [przy użyciu dokumentacji modelu obiektów programu Word](#WordOMDocumentation).  
  
 Aby dowiedzieć się, jak za pomocą modelu obiektów programu Word do wykonywania określonych zadań zobacz następujące tematy:  
  
-   [Praca z dokumentami](../vsto/working-with-documents.md)  
  
-   [Praca z dokumentami tekstowymi](../vsto/working-with-text-in-documents.md)  
  
-   [Praca z tabelami](../vsto/working-with-tables.md)  
  
##  <a name="understanding"></a> Opis modelu obiektów programu Word  
 Word zawiera setki obiektów, które mogą prowadzić interakcję. Te obiekty są zorganizowane w hierarchii, która jest ściśle zgodna interfejsu użytkownika. W górnej części hierarchii jest <xref:Microsoft.Office.Interop.Word.Application> obiektu. Ten obiekt reprezentuje bieżące wystąpienie programu Word. <xref:Microsoft.Office.Interop.Word.Application> Zawiera obiekt <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, <xref:Microsoft.Office.Interop.Word.Bookmark>, i <xref:Microsoft.Office.Interop.Word.Range> obiektów. Każdy z tych obiektów zawiera wiele metod i właściwości, do których masz dostęp do manipulowania i interakcji z obiektem.  
  
 Na poniższej ilustracji przedstawiono jeden widok tych obiektów w hierarchii modelu obiektów programu Word.  
  
 ![Grafika przedstawiająca Model obiektów programu Word](../vsto/media/wrwordobjectmodel.gif "grafiki Model obiektów programu Word")  
  
 Obiekty są wyświetlane na pierwszy rzut oka nakładanie się. Na przykład <xref:Microsoft.Office.Interop.Word.Document> i <xref:Microsoft.Office.Interop.Word.Selection> obiekty są członkami zarówno <xref:Microsoft.Office.Interop.Word.Application> obiektu, ale <xref:Microsoft.Office.Interop.Word.Document> obiektu jest również członkiem <xref:Microsoft.Office.Interop.Word.Selection> obiektu. Zarówno <xref:Microsoft.Office.Interop.Word.Document> i <xref:Microsoft.Office.Interop.Word.Selection> obiekty zawierają <xref:Microsoft.Office.Interop.Word.Bookmark> i <xref:Microsoft.Office.Interop.Word.Range> obiektów. Nakładanie się istnieje, ponieważ istnieje wiele sposobów, można uzyskać dostępu do tego samego typu obiektu. Na przykład zastosować formatowanie do <xref:Microsoft.Office.Interop.Word.Range> obiektu; ale może być dostępu do zakresu bieżącego zaznaczenia, określonego akapitu, sekcji lub całego dokumentu.  
  
 W poniższych sekcjach opisano krótko najwyższego poziomu obiektów i ich interakcji ze sobą. Te obiekty obejmują następujące pięć:  
  
-   Obiekt aplikacji  
  
-   Obiekt dokumentu  
  
-   Obiekt wyboru  
  
-   obiekt zakresu  
  
-   Obiekt zakładki  
  
 Oprócz modelu obiektów programu Word, podaj projektów pakietu Office w Visual Studio *hosta elementów* i *hostowania formantów* który rozszerzać niektórych obiektów w modelu obiektów programu Word. Obiekty hosta i formantów hosta przypominają obiektów programu Word, które rozszerzają, ale ma także dodatkowe funkcje, takie jak możliwości wiązania danych oraz dodatkowe zdarzenia. Aby uzyskać więcej informacji, zobacz [automatyzacji programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md) i [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
### <a name="application-object"></a>Obiekt aplikacji  
 <xref:Microsoft.Office.Interop.Word.Application> Obiekt reprezentuje aplikacji Word i jest elementem nadrzędnym wszystkie inne obiekty. Jej elementów członkowskich się zazwyczaj do programu Word jako całość. Jego właściwości i metody można użyć do kontrolowania środowiska programu Word.  
  
 W dodatku VSTO projekty można uzyskiwać dostęp do <xref:Microsoft.Office.Interop.Word.Application> obiektu za pomocą `Application` pole `ThisAddIn` klasy. Aby uzyskać więcej informacji, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 W projektach na poziomie dokumentu, można uzyskać dostępu do <xref:Microsoft.Office.Interop.Word.Application> obiektu za pomocą <xref:Microsoft.Office.Tools.Word.Document.Application%2A> właściwość `ThisDocument` klasy.  
  
### <a name="document-object"></a>Obiekt dokumentu  
 <xref:Microsoft.Office.Interop.Word.Document> Obiektu jest podstawą do programowania programu Word. Reprezentuje dokument i całą jego zawartość. Po otwarciu dokumentu lub Utwórz nowy dokument, możesz utworzyć nową <xref:Microsoft.Office.Interop.Word.Document> obiektu, który zostanie dodany do <xref:Microsoft.Office.Interop.Word.Documents> Kolekcja <xref:Microsoft.Office.Interop.Word.Application> obiektu. Dokument, który ma fokus jest wywoływana aktywny dokument. Jest reprezentowana przez <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> właściwość <xref:Microsoft.Office.Interop.Word.Application> obiektu.  
  
 Rozszerzanie narzędzi programowania pakietu Office w Visual Studio <xref:Microsoft.Office.Interop.Word.Document> obiektu podając <xref:Microsoft.Office.Tools.Word.Document> typu. Ten typ jest *element hosta* który umożliwia dostęp do wszystkich funkcji <xref:Microsoft.Office.Interop.Word.Document> obiektu i dodaje dodatkowe zdarzenia i możliwość dodawania zarządzane formanty.  
  
 Podczas tworzenia projektu poziomie dokumentu, można uzyskać dostęp <xref:Microsoft.Office.Tools.Word.Document> elementów członkowskich za pomocą wygenerowany `ThisDocument` klasy w projekcie. Można uzyskać dostępu do elementów członkowskich <xref:Microsoft.Office.Tools.Word.Document> element hosta za pomocą **mnie** lub **to** słowa kluczowe z kodu w `ThisDocument` klasy lub przy użyciu `Globals.ThisDocument` z kodu poza `ThisDocument` Klasa. Aby uzyskać więcej informacji, zobacz [programowania dostosowań na poziome dokumentu](../vsto/programming-document-level-customizations.md). Na przykład aby wybrać pierwszym akapicie dokumentu, należy użyć poniższego kodu.  
  
 [!code-vb[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#120)]
 [!code-csharp[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#120)]  
  
 W dodatku VSTO projektów, można wygenerować <xref:Microsoft.Office.Tools.Word.Document> hosta elementów w czasie wykonywania. Element hosta wygenerowanego umożliwia dodawanie formantów do skojarzonego dokumentu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="selection-object"></a>Obiekt wyboru  
 <xref:Microsoft.Office.Interop.Word.Selection> Obiekt reprezentuje obszar, który jest aktualnie wybrany. Podczas wykonywania operacji w interfejsie użytkownika programu Word, taki jak tekst pogrubienie wybrać, lub zaznacz tekst i Zastosuj formatowanie. <xref:Microsoft.Office.Interop.Word.Selection> Obiektu zawsze znajduje się w dokumencie. Jeśli nic nie zostanie wybrane, następnie reprezentuje punkt wstawiania. Ponadto zaznaczenia może obejmować wiele bloków tekstu, które nie są ciągłe.  
  
### <a name="range-object"></a>Obiekt zakresu  
 <xref:Microsoft.Office.Interop.Word.Range> Obiekt reprezentuje ciągły obszar w dokumencie i jest definiowana za pomocą znaku na pozycji początkowej i końcowej pozycji znaku. Nie są ograniczone do jednego <xref:Microsoft.Office.Interop.Word.Range> obiektu. Można zdefiniować wiele <xref:Microsoft.Office.Interop.Word.Range> obiektów w tym samym dokumencie. A <xref:Microsoft.Office.Interop.Word.Range> obiekt ma następującą charakterystykę:  
  
-   Może się składać tylko punkt wstawiania, zakres tekstu lub całego dokumentu.  
  
-   Obejmuje on niedrukowalne znaki spacji, znaków tabulacji i znaczniki akapitu.  
  
-   Może być reprezentowany przez bieżący wybór obszaru lub może reprezentować obszar inny niż bieżący wybór.  
  
-   Nie jest widoczny w dokumencie, w przeciwieństwie do wyboru, która jest zawsze widoczne.  
  
-   Nie zapisano dokument, a istnieje tylko w czasie wykonywania kodu.  
  
 Po wstawieniu tekst na końcu zakresu, Word automatycznie rozszerza zakres, aby dołączyć wstawionego tekstu.  
  
### <a name="content-control-objects"></a>Formant zawartości obiektów  
 A <xref:Microsoft.Office.Interop.Word.ContentControl> umożliwia kontrolowanie danych wejściowych i prezentacji tekstu i innych typów zawartości w dokumentach programu Word. A <xref:Microsoft.Office.Interop.Word.ContentControl> można wyświetlić kilka różnych typów interfejsu użytkownika, które są zoptymalizowane pod kątem użycia w dokumentach programu Word, takie jak tekstu sformatowanego, wyboru daty lub pola kombi. Można również użyć <xref:Microsoft.Office.Interop.Word.ContentControl> aby uniemożliwić użytkownikom edytowanie części dokumentu lub szablonu.  
  
 Visual Studio rozszerza <xref:Microsoft.Office.Interop.Word.ContentControl> obiektu do kilku formantów do innego hosta. Natomiast <xref:Microsoft.Office.Interop.Word.ContentControl> obiektów można wyświetlić te z nich różnych typów interfejsu użytkownika, które są dostępne dla formantów zawartości, program Visual Studio udostępnia innego typu dla każdego formantu zawartości. Na przykład można użyć <xref:Microsoft.Office.Tools.Word.RichTextContentControl> można użyć do utworzenia tekstu sformatowanego, lub <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> można utworzyć selektora daty. Te kontrolki hosta przypominają natywnego <xref:Microsoft.Office.Interop.Word.ContentControl>, ale mają dodatkowe zdarzenia oraz funkcje do wiązania danych. Aby uzyskać więcej informacji, zobacz [formantów zawartości](../vsto/content-controls.md).  
  
### <a name="bookmark-object"></a>Obiekt zakładki  
 <xref:Microsoft.Office.Interop.Word.Bookmark> Obiekt reprezentuje ciągły obszar w dokumencie z pozycji początkowej i końcowej pozycji. Zakładki służy do oznaczania lokalizacji w dokumencie lub jako kontener dla tekstu w dokumencie. A <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu może składać się z punktu wstawiania, lub być możliwie jak całego dokumentu. A <xref:Microsoft.Office.Interop.Word.Bookmark> ma następujące właściwości, które ustaw ją z wyjątkiem <xref:Microsoft.Office.Interop.Word.Range> obiektu:  
  
-   Można określić nazwę zakładki w czasie projektowania.  
  
-   <xref:Microsoft.Office.Interop.Word.Bookmark> obiekty są zapisane w dokumencie i w związku z tym nie są usuwane w kod przestanie działać lub dokumentu jest zamknięty.  
  
-   Zakładki może być ukryty lub stają się widoczne, ustawiając <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> właściwość <xref:Microsoft.Office.Interop.Word.View> do obiektu **false** lub **true**.  
  
 Visual Studio rozszerza <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu podając <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki hosta. <xref:Microsoft.Office.Tools.Word.Bookmark> Kontroli hosta zachowuje się jak natywny <xref:Microsoft.Office.Interop.Word.Bookmark>, ale ma dodatkowych zdarzeń i możliwości wiązania danych. W ten sam sposób powiązania danych do formantu pola tekstowego na formularzu systemu Windows można powiązać danych formant zakładki w dokumencie. Aby uzyskać więcej informacji, zobacz [formant zakładki](../vsto/bookmark-control.md).  
  
##  <a name="WordOMDocumentation"></a> Korzystając z dokumentacji modelu obiektów programu Word  
 Aby uzyskać pełne informacje o modelu obiektów programu Word mogą odwoływać się do programu Word odwołanie podstawowy zestaw międzyoperacyjny (PIA) i Visual Basic for Applications (VBA) odwołania do modelu obiektu.  
  
### <a name="primary-interop-assembly-reference"></a>Odwołanie do podstawowego zestawu międzyoperacyjnego  
 Dokumentacja odwołania Word PIA opisano typy w podstawowego zestawu międzyoperacyjnego dla programu Word. Niniejsza dokumentacja jest dostępna z następującej lokalizacji: [odwołania zestawu Interop Word 2010 podstawowy](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Aby uzyskać więcej informacji dotyczących projektu PIA programu Word, takie jak różnice między klasy i interfejsy PIA i implementowania zdarzeń w PIA, zobacz [Przegląd klasy i interfejsy Office podstawowe zestawy międzyoperacyjne](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>Odwołania do modelu obiektu VBA  
 Odwołania do modelu obiektu VBA dokumentów modelu obiektów programu Word, ponieważ jest narażony na kod. Aby uzyskać więcej informacji, zobacz [odwołania do modelu obiektu programu Word 2010](http://go.microsoft.com/fwlink/?LinkId=199772).  
  
 Wszystkie obiekty i elementów członkowskich w odwołania do modelu obiektu VBA odpowiadają typy i składniki w PIA programu Word. Na przykład obiekt dokumentu w odwołania do modelu obiektu VBA odpowiada <xref:Microsoft.Office.Interop.Word.Document> obiektu w PIA programu Word. Odwołania do modelu obiektu VBA zapewnia przykłady kodu dla większości właściwości, metod i zdarzeń, jednak musi tłumaczenia kodu VBA w niniejszej dokumentacji w języku Visual Basic lub Visual C#, jeśli chcesz używać ich w programie projektu tworzenia w programie Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Praca z dokumentami](../vsto/working-with-documents.md)   
 [Praca z dokumentami tekstowymi](../vsto/working-with-text-in-documents.md)   
 [Praca z tabelami](../vsto/working-with-tables.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  