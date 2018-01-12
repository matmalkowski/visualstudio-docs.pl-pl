---
title: Formant XMLNodes | Dokumentacja firmy Microsoft
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
- XMLNodes control, events
- XMLNodes control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1a3759070d406e721a12e01950e0e99cea40d1fc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="xmlnodes-control"></a>Formant XMLNodes
  **Ważne** informacji zawartych w tym temacie dotyczące programu Microsoft Word jest przedstawioną wyłącznie do korzyści i użyj osób i organizacji, które znajdują się poza Stanami Zjednoczonymi i jego terytoriów lub używający lub tworzenie programy, które działają na, produktów Microsoft Word, które są licencjonowane przez firmę Microsoft przed 2010 stycznia, po usunięciu implementację funkcji określonej przez Microsoft związane z niestandardowy plik XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word może nie być odczytywane lub używane przez osoby lub organizacji w Stanach Zjednoczonych lub w jego terytoriów użytkowników przy użyciu lub tworzenie programów uruchamianych na produktów Microsoft Word, które są licencjonowane przez firmę Microsoft po 10 stycznia 2010 ; te produkty nie będzie działać taka sama jak produktów licencjonowanych przed tą datą lub zakupione i licencję na korzystanie z niego poza Stanami Zjednoczonymi.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> Formant jest zbiór mapowanych obiektów węzła XML, który opisuje zdarzenia. <xref:Microsoft.Office.Tools.Word.XMLNodes> Kontroli jest tworzony tylko wtedy, gdy powtarzający się element schematu jest mapowana na dokument programu Microsoft Office Word. Jeśli powtarzający się element zawiera elementy podrzędne, każdy z elementów podrzędnych tworzona jest również jako <xref:Microsoft.Office.Tools.Word.XMLNodes> formantu.  
  
 Gdy program Visual Studio utworzy kolekcja węzłów XML, można programu względem formantu bezpośrednio, bez konieczności przechodzenia modelu obiektów programu Word. <xref:Microsoft.Office.Tools.Word.XMLNodes> Formantu można usunąć tylko przez usunięcie mapowania elementu z dokumentu.  
  
> [!NOTE]  
>  Jeśli dostęp do elementu podrzędnego <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolować za pośrednictwem <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> właściwości, zwraca <xref:Microsoft.Office.Interop.Word.XMLNode> obiektu zamiast <xref:Microsoft.Office.Tools.Word.XMLNode> formantu. Aby uzyskać więcej informacji, zobacz [programowe ograniczenia elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="binding-data-to-the-control"></a>Wiązanie danych do kontrolki  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> Formant nie obsługuje powiązanie danych. Jest to spowodowane <xref:Microsoft.Office.Tools.Word.XMLNodes> formant nie ma złożone powiązanie możliwości danych i proste powiązanie danych nie może reprezentować powtarzanie danych.  
  
## <a name="formatting"></a>Formatowanie  
 Żadnego formatowania, który można zastosować do tekstu w dokumencie można zastosować do <xref:Microsoft.Office.Tools.Word.XMLNodes> formantu.  
  
## <a name="events"></a>Zdarzenia  
 Dostępne dla zdarzeń <xref:Microsoft.Office.Tools.Word.XMLNodes> formantu są:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="comparing-events"></a>Porównywanie zdarzenia  
 Można przechwycić zdarzenie, gdy użytkownik przesuwa kursor lub jej w kontekście określonego <xref:Microsoft.Office.Tools.Word.XMLNodes> formantu. Na przykład może być <xref:Microsoft.Office.Tools.Word.XMLNodes> formantu o nazwie `Customer` ma element podrzędny <xref:Microsoft.Office.Tools.Word.XMLNodes> formantu o nazwie `Company`, i `Company` ma dwa podrzędny <xref:Microsoft.Office.Tools.Word.XMLNodes> formantów `CompanyName` i `CompanyRegion` w następujący sposób:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Jeśli chcesz wyświetlić formantu w okienku Akcje zawsze, gdy kursor jest przenoszony do `Company` węzła, jego powinien niezależnie od tego, czy znajduje się kursor w `CompanyName` lub `CompanyRegion` ponieważ są one zarówno w kontekście `Company`. W takim przypadku możesz pisać kod <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> zdarzenie `Company`.  
  
 W większości przypadków, gdy kursor wprowadza <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolować zarówno <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> i <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> pojawienia się zdarzenia. W poniższej tabeli przedstawiono różnice między tymi zdarzeniami.  
  
|Wybierz zdarzenie|Zdarzenie ContextEnter|  
|------------------|------------------------|  
|Występuje, gdy kursor znajduje się w jednym z węzłów <xref:Microsoft.Office.Tools.Word.XMLNodes> kolekcji.|Występuje, gdy kursor znajduje się w jednym z węzłów lub węzły podrzędne <xref:Microsoft.Office.Tools.Word.XMLNodes> kolekcji z obszaru poza kontekstem węzła. Innymi słowy, jest wywoływane tylko wtedy, gdy zmieni się kontekstu i może nie być zgłaszany wielu zagnieżdżonych <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolki.|  
  
 Na przykład, gdy kursor jest z poza `Customer` do `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> zdarzenia `Customer`, `Company`, i `CompanyName` są zgłaszane. Jeśli następnie przesuń kursor z `CompanyName` do `CompanyRegion`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> zdarzenia tylko dla `CompanyRegion` jest zgłaszane, ponieważ kontekst jest taka sama dla obu `Company` i `Customer`. Istnieje wiele `Company` węzły w dokumencie. Przesunięcie kursora z `CompanyName` węzła jednego `Company` do `CompanyName` węzła innego `Company`, kontekst jest taka sama, co pozwoli tylko <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> zdarzenia.  
  
 Tym samym różnice między <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> zdarzeń i <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Formant XMLNode](../vsto/xmlnode-control.md)   
 [Porady: dodawanie formantów XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Porady: mapowanie schematów z dokumentami programu Word w Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  