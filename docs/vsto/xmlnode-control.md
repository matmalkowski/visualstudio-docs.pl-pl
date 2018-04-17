---
title: Formant XMLNode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b21f6f4e84672d195b6147f73c513c1995200a03
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="xmlnode-control"></a>Formant XMLNode
  **Ważne** informacji zawartych w tym temacie dotyczące programu Microsoft Word jest przedstawioną wyłącznie do korzyści i użyj osób i organizacji, które znajdują się poza Stanami Zjednoczonymi i jego terytoriów lub używający lub tworzenie programy, które działają na, produktów Microsoft Word, które są licencjonowane przez firmę Microsoft przed 2010 stycznia, po usunięciu implementację funkcji określonej przez Microsoft związane z niestandardowy plik XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word może nie być odczytywane lub używane przez osoby lub organizacji w Stanach Zjednoczonych lub w jego terytoriów użytkowników przy użyciu lub tworzenie programów uruchamianych na produktów Microsoft Word, które są licencjonowane przez firmę Microsoft po 10 stycznia 2010 ; te produkty nie będzie działać taka sama jak produktów licencjonowanych przed tą datą lub zakupione i licencję na korzystanie z niego poza Stanami Zjednoczonymi.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Formant jest mapowanych obiektu węzła XML opisuje zdarzenia, który może być powiązany z danymi. <xref:Microsoft.Office.Tools.Word.XMLNode> Kontroli jest tworzony tylko wtedy, gdy element schematu niepowtarzającymi jest zamapowane do dokumentu programu Microsoft Office Word. Po Visual Studio tworzy węzeł XML, można program na nim bezpośrednio, bez konieczności przechodzenia modelu obiektów programu Word.  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Formantu można usunąć tylko przez usunięcie mapowania elementu w programie Word.  
  
## <a name="binding-data-to-the-control"></a>Wiązanie danych do kontrolki  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Sterowanie obsługuje proste powiązanie danych. Węzeł XML powinien być związany ze źródłem danych przy użyciu <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> właściwości. Jeśli dane w zestawie danych powiązane są aktualizowane, <xref:Microsoft.Office.Tools.Word.XMLNode> kontroli odzwierciedla zmiany.  
  
## <a name="formatting"></a>Formatowanie  
 Formatowanie, które mogą być stosowane do <xref:Microsoft.Office.Interop.Word.XMLNode> obiektu można zastosować do <xref:Microsoft.Office.Tools.Word.XMLNode> formantu. W tym czcionki, style podkreślenia i style znaków.  
  
## <a name="events"></a>Zdarzenia  
 Następujące zdarzenia są dostępne dla <xref:Microsoft.Office.Tools.Word.XMLNode> sterowania:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="comparing-events"></a>Porównywanie zdarzenia  
 Można przechwycić zdarzenie, gdy użytkownik przesuwa kursor lub jej w kontekście określonego <xref:Microsoft.Office.Tools.Word.XMLNode> formantu. Na przykład może być <xref:Microsoft.Office.Tools.Word.XMLNode> formantu o nazwie `Customer` ma element podrzędny <xref:Microsoft.Office.Tools.Word.XMLNode> formantu o nazwie `Company`, i `Company` ma dwa podrzędny <xref:Microsoft.Office.Tools.Word.XMLNode> formantów `CompanyName` i `CompanyRegion` w następujący sposób:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Jeśli chcesz wyświetlić formantu w okienku Akcje zawsze, gdy kursor jest przenoszony do `Company` węzła, jego powinien niezależnie od tego, czy znajduje się kursor w `CompanyName` lub `CompanyRegion` ponieważ są one zarówno w kontekście `Company`. W takim przypadku możesz pisać kod <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> zdarzenie `Company`.  
  
 W większości przypadków, gdy kursor wprowadza <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolować zarówno <xref:Microsoft.Office.Tools.Word.XMLNode.Select> i <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> pojawienia się zdarzenia. W poniższej tabeli przedstawiono różnice między tymi zdarzeniami.  
  
|Wybierz zdarzenie|Zdarzenie ContextEnter|  
|------------------|------------------------|  
|Występuje, gdy kursor znajduje się wewnątrz <xref:Microsoft.Office.Tools.Word.XMLNode>.|Występuje, gdy kursor znajduje się wewnątrz <xref:Microsoft.Office.Tools.Word.XMLNode> lub jednego z jego węzłów podrzędnych, z obszaru poza kontekstem węzła. Innymi słowy jest wywoływane tylko wtedy, gdy zmienia kontekst.|  
  
 Na przykład, gdy kursor jest z poza `Customer` do `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> zdarzenia dla `Customer`, `Company`, i `CompanyName` jest wywoływane. Jeśli następnie przesuń kursor z `CompanyName` do `CompanyRegion`, tylko <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> zdarzenia dla `CompanyRegion` jest zgłaszane, ponieważ są nadal w kontekście zarówno `Company` i `Customer`.  
  
 Tym samym różnice między <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> zdarzeń i <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Formant XMLNodes](../vsto/xmlnodes-control.md)   
 [Porady: dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Porady: mapowanie schematów z dokumentami programu Word w Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  