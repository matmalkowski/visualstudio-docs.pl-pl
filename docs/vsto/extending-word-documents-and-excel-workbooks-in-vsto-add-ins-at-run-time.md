---
title: "Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania | Dokumentacja firmy Microsoft"
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
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
ms.assetid: c1607314-4cf8-439c-b4c5-709db8b71cff
caps.latest.revision: "61"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93010f03384e3cb3930911115ee92b3bb9205b9e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania
  Dodatku VSTO służy do dostosowywania dokumentów programu Word i skoroszytów programu Excel w następujący sposób:  
  
-   Dodaj formanty zarządzane otwartego dokumentu lub arkusza.  
  
-   Konwersja istniejącego obiektu listy w arkuszu programu Excel do rozszerzonego <xref:Microsoft.Office.Tools.Excel.ListObject> opisuje zdarzenia i może być powiązana z danymi przy użyciu modelu powiązanie danych formularzy systemu Windows.  
  
-   Zdarzenia poziomu aplikacji dostępu, które są dostępne w programach Word i Excel dla określonych dokumentów, skoroszytów i arkuszy.  
  
 Aby używać tej funkcji, można wygenerować obiektu w czasie wykonywania, rozszerzający dokumentu lub skoroszytu.  
  
 **Dotyczy:** informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla następujących aplikacji: Excel i Word. Aby uzyskać więcej informacji, zobacz [dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
## <a name="generating-extended-objects-in-vsto-add-ins"></a>Generowanie rozszerzonych obiektów w dodatkach VSTO  
 *Obiektów rozszerzonych* wystąpień typów podana przy użyciu programu Visual Studio Tools dla pakietu Office runtime Dodawanie funkcji do obiektów, które natywnie istnieje w modelach obiektu Word czy Excel (nazywane *natywny obiektów pakietu Office*). Aby wygenerować obiektu rozszerzonej dla obiekt Word czy Excel, należy użyć metody GetVstoObject. Przy pierwszym wywołaniu metody GetVstoObject dla określonego obiektu Word czy Excel, zwraca nowy obiekt, rozszerzający określony obiekt. Zawsze należy wywołać metodę i określić ten sam programu Word lub w programie Excel obiektu, zwraca ten sam obiekt rozszerzonej.  
  
 Typ obiektu rozszerzonej ma taką samą nazwę jak typ macierzysty obiekt pakietu Office, ale typ jest zdefiniowany w <xref:Microsoft.Office.Tools.Excel> lub <xref:Microsoft.Office.Tools.Word> przestrzeni nazw. Na przykład, jeśli należy wywołać metodę GetVstoObject rozszerzenie <xref:Microsoft.Office.Interop.Word.Document> obiektów, metoda zwraca <xref:Microsoft.Office.Tools.Word.Document> obiektu.  
  
 Metody GetVstoObject są przeznaczone do użycia głównie w przypadku projektów dodatku VSTO. Można również użyć tych metod w projektach na poziomie dokumentu, ale różniących się zachowaniem i ma mniejszą liczbę zastosowań.  
  
 Aby ustalić, czy rozszerzonej obiekt został już wygenerowany dla danego obiektu Office macierzystego, należy użyć metody HasVstoObject. Aby uzyskać więcej informacji, zobacz [określającą czy Office obiekt został rozszerzony](#HasVstoObject).  
  
### <a name="generating-host-items"></a>Generowanie obiekty hosta  
 Jeśli używasz GetVstoObject rozszerzenie obiektu na poziomie dokumentu (oznacza to, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, lub <xref:Microsoft.Office.Interop.Word.Document>), jest nazywany zwrócony obiekt *element hosta*. Element hosta jest typem, który może zawierać inne obiekty, w tym inne obiekty rozszerzone i formantów. Podobny do danego typu w Word czy Excel podstawowego zestawu międzyoperacyjnego, ale ma dodatkowe funkcje. Aby uzyskać informacje o obiektach hosta, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
 Po wygenerowaniu elementu hosta można go dodać zarządzane formanty do dokumentu, skoroszytu lub arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie do dokumentów i arkuszy zarządzane formanty](#AddControls).  
  
##### <a name="to-generate-a-host-item-for-a-word-document"></a>Aby wygenerować element hosta dokumentu programu Word  
  
-   Poniższy przykład kodu pokazuje sposób generowania elementu hosta dla aktywnego dokumentu.  
  
     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]  
  
##### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Aby wygenerować element hosta skoroszytu programu Excel  
  
-   Poniższy przykład kodu pokazuje sposób generowania elementu hosta dla aktywnego skoroszytu.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]  
  
##### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Aby wygenerować elementu hosta dla programu Excel  
  
-   Poniższy przykład kodu pokazuje sposób generowania elementu hosta dla aktywnego arkusza w projekcie.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]  
  
### <a name="generating-listobject-host-controls"></a>Generowanie formantów ListObject hosta  
 Jeśli używasz metody GetVstoObject rozszerzenie <xref:Microsoft.Office.Interop.Excel.ListObject>, metoda zwraca <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Zawiera wszystkie funkcje oryginalnej <xref:Microsoft.Office.Interop.Excel.ListObject>, ale ma także dodatkowe funkcje, takie jak możliwość można powiązać z danymi przy użyciu modelu powiązanie danych formularzy systemu Windows. Aby uzyskać więcej informacji, zobacz [ListObject — formant](../vsto/listobject-control.md).  
  
##### <a name="to-generate-a-host-control-for-a-listobject"></a>Aby wygenerować kontroli hosta dla ListObject  
  
-   Poniższy przykład kodu pokazuje sposób generowania <xref:Microsoft.Office.Tools.Excel.ListObject> pierwszy <xref:Microsoft.Office.Interop.Excel.ListObject> w aktywnym arkuszu w projekcie.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]  
  
##  <a name="AddControls"></a>Dodawanie formantów zarządzanego do dokumentów i arkuszy  
 Po wygenerowaniu <xref:Microsoft.Office.Tools.Word.Document> lub <xref:Microsoft.Office.Tools.Excel.Worksheet>, można dodawać formanty do dokumentu lub arkuszu, które są rozszerzone obiekty reprezentują. Aby to zrobić, użyj właściwości kontrolki <xref:Microsoft.Office.Tools.Word.Document> lub <xref:Microsoft.Office.Tools.Excel.Worksheet>. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Formanty formularzy systemu Windows można dodać lub *hostowania formantów*. Formanty hosta jest udostępniane przez formant [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] który opakowuje odpowiedniego formantu w Word czy Excel podstawowego zestawu międzyoperacyjnego. Formanty hosta przedstawia wszystkie zachowania obiekt natywny pakietu Office, ale również informuje o zdarzeniach i może być powiązana z danymi przy użyciu modelu powiązanie danych formularzy systemu Windows. Aby uzyskać więcej informacji, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
> [!NOTE]  
>  Nie można dodać <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> formantu do arkusza lub <xref:Microsoft.Office.Tools.Word.XMLNode> lub <xref:Microsoft.Office.Tools.Word.XMLNodes> kontroli w dokumencie przy użyciu dodatku VSTO. Te kontrolki hosta nie można dodać programistycznie. Aby uzyskać więcej informacji, zobacz [programowe ograniczenia elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="persisting-and-removing-controls"></a>Przechowywanie i usuwanie kontrolek  
 Po dodaniu zarządzane formanty w dokumencie lub arkusz formanty nie są zachowywane w przypadku dokumentu jest zapisane, a następnie zamknięte. Wszystkie formanty hosta zostaną usunięte, tak aby tylko podstawowy natywny obiektów pakietu Office są pozostawione. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject> staje się <xref:Microsoft.Office.Interop.Excel.ListObject>. Wszystkie formanty formularzy systemu Windows są również usuwane, ale otoki kontrolki ActiveX są pozostawione w dokumencie. Należy dołączyć kod w dodatek VSTO wyczyścić formantów lub ponownie utworzyć formantów przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [przechowywanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
## <a name="accessing-application-level-events-on-documents-and-workbooks"></a>Uzyskiwanie dostępu do zdarzenia na poziomie aplikacji dla dokumentów i skoroszytów  
 Niektóre zdarzenia dokumentów, skoroszytów i arkuszy w macierzystym modele obiektów programu Word i Excel pojawienia się tylko na poziomie aplikacji. Na przykład <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzenie jest zgłaszane po otwarciu dokumentu programu Word, ale to zdarzenie jest zdefiniowany w <xref:Microsoft.Office.Interop.Word.Application> klasy, a nie <xref:Microsoft.Office.Interop.Word.Document> klasy.  
  
 Gdy używasz tylko natywny obiektów pakietu Office w dodatku VSTO z musi obsługiwać te zdarzenia na poziomie aplikacji, a następnie wpisz dodatkowy kod w celu ustalenia, czy dokument, który wywołał zdarzenie to takie, które zostały dostosowane. Obiekty hosta Podaj te zdarzenia na poziomie dokumentu, dzięki czemu możliwe jest łatwiejsze do obsługi zdarzeń dla określonego dokumentu. Można wygenerować element hosta i następnie obsługi zdarzeń dla tego elementu host.  
  
### <a name="example-that-uses-native-word-objects"></a>Przykład korzystającej z natywnego programu Word  
 Poniższy przykład kodu pokazuje sposób obsługi zdarzeń aplikacji na poziomie dokumentów programu Word. `CreateDocument` Metoda tworzy nowy dokument, a następnie definiuje <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> obsługi zdarzeń, który uniemożliwia zapisywane w tym dokumencie. Ponieważ jest to zdarzenie jest wywoływane dla poziomu aplikacji <xref:Microsoft.Office.Interop.Word.Application> obiekt programu obsługi zdarzeń musi porównywać `Doc` parametr o `document1` obiekt, aby określić, czy `document1` reprezentuje zapisany dokument.  
  
 [!code-vb[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]  
  
### <a name="examples-that-use-a-host-item"></a>Przykłady, których użyć elementu hosta  
 W poniższych przykładach kodu uproszczenia tego procesu Obsługa <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> zdarzenie <xref:Microsoft.Office.Tools.Word.Document> element hosta. `CreateDocument2` Generowanie metody w tych przykładach <xref:Microsoft.Office.Tools.Word.Document> który rozszerza `document2` obiektu, a następnie definiuje <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> obsługi zdarzeń, który uniemożliwia zapisanie dokumentu. Ponieważ ten program obsługi zdarzeń jest wywoływana tylko wtedy, gdy `document2` jest zapisywane zdarzenie obsługi można anulować, Zapisz działania bez wykonywania dodatkowych pracę, aby sprawdzić, który dokument został zapisany.  
  
 W poniższym przykładzie kodu pokazano to zadanie.  
  
 [!code-vb[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]  
  
##  <a name="HasVstoObject"></a>Określanie, czy obiekt pakietu Office został rozszerzony  
 Aby ustalić, czy rozszerzonej obiekt został już wygenerowany dla danego obiektu Office macierzystego, należy użyć metody HasVstoObject. Ta metoda zwraca **true** przypadku rozszerzonej obiekt został już wygenerowany; w przeciwnym razie zwraca **false**.  
  
 Użyj metody Globals.Factory.HasVstoMethod. Przekazywanie Word czy Excel obiekt natywny, takich jak <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Worksheet>, które mają zostać przetestowane dla obiekt rozszerzonej.  
  
 HasVstoObject — metoda jest przydatne, jeśli chcesz uruchomić kod tylko wtedy, gdy określony obiekt Office rozszerzonej obiektu. Na przykład, jeśli masz dodatku VSTO programu Word, która obsługuje <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeń do usunięcia z dokumentu przed nią zarządzane formanty jest zapisywana, metoda HasVstoObject służy do określenia, czy dokument został rozszerzony. Jeśli dokument nie został rozszerzony, nie może zawierać formanty zarządzane i w związku z tym obsługi zdarzeń można po prostu wrócić bez próby wyczyścić formantów w dokumencie.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)  
  
  