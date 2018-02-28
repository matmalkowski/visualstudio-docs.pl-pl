---
title: "ListObject — formant | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 2100a1c30fda5981d3d7e58f2f5077e0cdf87a2d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="listobject-control"></a>ListObject — Formant
  <xref:Microsoft.Office.Tools.Excel.ListObject> Formant jest listę, która opisuje zdarzenia i może być powiązany z danymi. Po dodaniu listy do arkusza programu Visual Studio tworzy <xref:Microsoft.Office.Tools.Excel.ListObject> formant, który można program względem bezpośrednio, bez konieczności przechodzenia modelu obiektu programu Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Tworzenie formantu  
 W projektach na poziomie dokumentu, można dodać <xref:Microsoft.Office.Tools.Excel.ListObject> formantów do arkusza w czasie projektowania lub w czasie wykonywania. W dodatku VSTO projektów, można dodać <xref:Microsoft.Office.Tools.Excel.ListObject> formantów do arkuszy w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Domyślnie lista utworzony dynamicznie obiektów nie są zachowywane w arkuszu zgodnie z formanty hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="binding-data-to-the-control"></a>Wiązanie danych do kontrolki  
 A <xref:Microsoft.Office.Tools.Excel.ListObject> sterowanie obsługuje powiązanie danych proste i złożone. <xref:Microsoft.Office.Tools.Excel.ListObject> Formantu można powiązać źródła danych przy użyciu <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> i <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> właściwości w czasie projektowania lub <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metody w czasie wykonywania.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.ListObject> Jest aktualizowane automatycznie, gdy jest powiązany ze źródłem danych, takich jak <xref:System.Data.DataTable>, który informuje o zdarzeniach po zmianie danych. W przypadku powiązania <xref:Microsoft.Office.Tools.Excel.ListObject> ze źródłem danych nie wywołać zdarzenia w przypadku zmiany danych, należy wywołać <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> lub <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> metodę aktualizowania <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
 Po dodaniu <xref:Microsoft.Office.Tools.Excel.ListObject> w komórce arkusza mapując powtarzający się element schematu tej komórki, Visual Studio automatycznie mapuje <xref:Microsoft.Office.Tools.Excel.ListObject> do wygenerowanego zestawu danych. Jednak <xref:Microsoft.Office.Tools.Excel.ListObject> automatycznie nie jest powiązany z danymi. Należy wykonać czynności, aby powiązać <xref:Microsoft.Office.Tools.Excel.ListObject> do zestawu danych w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu. Programowo można powiązać <xref:Microsoft.Office.Tools.Excel.ListObject> do zestawu danych w czasie wykonywania w dodatku VSTO.  
  
 Ponieważ dane są oddzielne od <xref:Microsoft.Office.Tools.Excel.ListObject>, należy dodawać i usuwać dane za pośrednictwem powiązania zestawu danych, a nie bezpośrednio za pomocą <xref:Microsoft.Office.Tools.Excel.ListObject>. Jeśli dane w zestawie danych powiązane są aktualizowane przy użyciu dowolnego mechanizmu <xref:Microsoft.Office.Tools.Excel.ListObject> formant automatycznie zmienia. Aby uzyskać więcej informacji, zobacz [wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Możesz szybko wpisać <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli przez powiązanie <xref:Microsoft.Office.Tools.Excel.ListObject> ze źródłem danych. Jeśli edytujesz danych z danymi <xref:Microsoft.Office.Tools.Excel.ListObject>, zmiany zostaną zastosowane automatycznie ze źródła danych. Jeśli chcesz wypełnić <xref:Microsoft.Office.Tools.Excel.ListObject> , a następnie włączyć użytkownika do zmiany danych w <xref:Microsoft.Office.Tools.Excel.ListObject> bez modyfikowania źródła danych, można użyć <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> metodę, aby odłączyć <xref:Microsoft.Office.Tools.Excel.ListObject> ze źródła danych. Aby uzyskać więcej informacji, zobacz [porady: wypełnianie formantów ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
> [!NOTE]  
>  Powiązanie danych nie jest obsługiwana w nakładających się <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki.  
  
### <a name="improving-performance-in-listobject-controls"></a>Poprawianie wydajności w formantów ListObject  
 Odczytywanie pliku XML do powiązanych z danymi <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli zwykle jest wolniejsze, jeśli najpierw powiązać formant, a następnie wywołać <xref:System.Data.DataSet.ReadXml%2A> aby wypełnić dataset. Aby zwiększyć wydajność, należy wywołać <xref:System.Data.DataSet.ReadXml%2A> przed powiązywanie formantu.  
  
### <a name="disconnecting-listobject-controls-from-the-data-source"></a>Rozłączanie formantów ListObject ze źródła danych  
 Po wypełnieniu <xref:Microsoft.Office.Tools.Excel.ListObject> formantu z danymi przez powiązanie go ze źródłem danych, możesz odłączyć go tak, aby zmiany wprowadzone w danych w obiekcie listy nie wpływają na źródle danych. Aby uzyskać więcej informacji, zobacz [porady: wypełnianie formantów ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md).  
  
### <a name="restoring-column-and-row-order"></a>Przywracanie kolumny i kolejność wierszy  
 Po powiązaniu danych <xref:Microsoft.Office.Tools.Excel.ListObject> formant, który został dodany do dokumentu w czasie projektowania Visual Studio przechowuje informacje o kolejności kolumn i wierszy przy każdym zapisać skoroszyt. Jeśli użytkownik przeniesie <xref:Microsoft.Office.Tools.Excel.ListObject> kolumn lub wierszy w czasie wykonywania, nową kolejność jest zachowywana przy następnym otwarciu skoroszytu i <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli wiąże się ze źródłem danych ponownie.  
  
 Jeśli chcesz przywrócić <xref:Microsoft.Office.Tools.Excel.ListObject> do oryginalnych kolumn i kolejność wierszy można wywołać <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> metody. Ta metoda usuwa niestandardowe właściwości dokumentu dotyczące kolumny i kolejność wiersza określony <xref:Microsoft.Office.Tools.Excel.ListObject>. Wywołanie tej metody z <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> zdarzeń skoroszytu, jeśli nie chcesz zachować kolejność kolumn i wierszy <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
## <a name="formatting"></a>Formatowanie  
 Formatowanie, które mogą być stosowane do <xref:Microsoft.Office.Interop.Excel.ListObject> można zastosować do <xref:Microsoft.Office.Tools.Excel.ListObject> formantu. W tym obramowania, czcionki, format liczbowy i style. Użytkownicy końcowi mogą zmienić kolejność kolumn z danymi <xref:Microsoft.Office.Tools.Excel.ListObject>, a te zmiany zostaną utrwalone w dokumencie, pod warunkiem <xref:Microsoft.Office.Tools.Excel.ListObject> został dodany do dokumentu w czasie projektowania. Przy następnym otwarciu dokumentu obiektu list zostanie powiązany z tym samym źródłem danych, ale kolejność kolumn, zostaną one zastosowane zmiany użytkowników.  
  
## <a name="adding-and-removing-columns-at-run-time"></a>Dodawanie i usuwanie kolumn w czasie wykonywania  
 Nie można ręcznie dodać ani usunąć kolumn z danymi <xref:Microsoft.Office.Tools.Excel.ListObject> formantu w czasie wykonywania. Jeśli użytkownik końcowy próbuje usunąć kolumnę, zostanie natychmiast przywrócona i dodać kolumny zostaną usunięte. W związku z tym należy napisać kod, aby wyjaśnienia użytkownikom, dlaczego nie mogą wykonywać te akcje na <xref:Microsoft.Office.Tools.Excel.ListObject> który jest powiązany z danymi. Program Visual Studio udostępnia kilka zdarzeń na <xref:Microsoft.Office.Tools.Excel.ListObject> dotyczące powiązania danych. Na przykład można użyć <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> zdarzeń, aby ostrzec użytkowników, którzy mają one podjął próbę usunięcia danych nie można usunąć i zostało przywrócone.  
  
## <a name="adding-and-removing-rows-at-run-time"></a>Dodawanie i usuwanie wierszy w czasie wykonywania  
 Możesz ręcznie dodać i usunąć wierszy z danymi <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli, podana źródło danych umożliwia dodawanie nowych wierszy i nie jest tylko do odczytu. Można pisać kod dla zdarzeń, takich jak <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> sprawdzania poprawności danych. Aby uzyskać więcej informacji, zobacz [porady: Sprawdzanie poprawności danych po dodaniu nowego rzędu do formantu ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).  
  
 Czasami relacji obiektu listy do źródła danych powoduje, że błędy rutynowych. Na przykład można zamapować kolumny, które mają być wyświetlane w <xref:Microsoft.Office.Tools.Excel.ListObject>, więc w przypadku pominięcia kolumn, które mają zastosowanie ograniczenia, np. pola, które nie może akceptować wartości null, błędy są wywoływane za każdym razem, gdy wiersz jest tworzony. Można napisać kod, aby dodać brakujące wartości w obsłudze zdarzeń dla <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> zdarzeń.  
  
## <a name="renaming-listobject-controls-in-excel"></a>Zmiana nazwy formantów ListObject w programie Excel  
 Excel umożliwia użytkownikom zmianę nazwy tabel programu Excel w czasie wykonywania za pomocą **projekt** kartę. Jednak <xref:Microsoft.Office.Tools.Excel.ListObject> formant nie obsługuje tej funkcji. Jeśli użytkownik próbuje zmienić nazwy tabeli programu Excel, która odpowiada <xref:Microsoft.Office.Tools.Excel.ListObject>, nazwa tabeli programu Excel automatycznie zostanie przywrócona oryginalna nazwa po zapisaniu skoroszytu.  
  
## <a name="events"></a>Zdarzenia  
 Następujące zdarzenia są dostępne dla <xref:Microsoft.Office.Tools.Excel.ListObject> sterowania:  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Porady: dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Porady: zmiana rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Porady: Sprawdzanie poprawności danych po dodaniu nowego rzędu do formantu ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Porady: mapowanie kolumn ListObject do danych](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Porady: wypełnianie formantów ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Porady: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  