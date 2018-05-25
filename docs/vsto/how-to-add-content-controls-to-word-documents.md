---
title: 'Porady: Dodawanie zawartości formantów do dokumentów programu Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9ac9fbb7528559189dc74d1bf5c1d9645e47f261
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Porady: Dodawanie zawartości formantów do dokumentów programu Word
  W projektów na poziomie dokumentu programu Word można dodać formantów zawartości do dokumentu w projekcie w czasie projektowania lub w czasie wykonywania. W projektów dodatku VSTO programu Word można dodać formantów zawartości do otwartego dokumentu w czasie wykonywania.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 W tym temacie opisano następujące zadania:  
  
-   [Dodawanie formantów zawartości w czasie projektowania](#designtime)  
  
-   [Dodawanie formantów zawartości w czasie wykonywania w projektach na poziomie dokumentu](#runtimedoclevel)  
  
-   [Dodawanie formantów zawartości w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
 Aby uzyskać informacje o formantach zawartości, zobacz [formanty zawartości](../vsto/content-controls.md).  
  
##  <a name="designtime"></a> Dodaj zawartość formantów w czasie projektowania  
 Istnieje kilka sposobów, aby dodać formantów zawartości do dokumentu w projektach na poziomie dokumentu w czasie projektowania:  
  
-   Dodawanie zawartości formantu z **formanty Word** karcie **przybornika**.  
  
-   Dodawanie zawartości formantu do dokumentu w taki sam sposób należy dodać macierzystego formantu zawartości w programie Word.  
  
-   Przeciągnij formant zawartości do dokumentu z **źródeł danych** okna. Jest to przydatne, gdy chcesz powiązać formantu danych, gdy formant nie zostanie utworzony. Aby uzyskać więcej informacji, zobacz [porady: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md) i [porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Aby dodać kontrolkę zawartości w dokumencie przy użyciu przybornika  
  
1.  W dokumencie, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta, umieść kursor, której chcesz dodać formant zawartości, lub zaznacz tekst, który ma formantu zawartości, aby zastąpić.  
  
2.  Otwórz **przybornika** i kliknij przycisk **formanty Word** kartę.  
  
3.  Dodaj formant, jeden z następujących sposobów:  
  
    -   Kliknij dwukrotnie zawartości formantu w **przybornika**.  
  
         lub  
  
    -   Kliknij przycisk zawartości formantu w **przybornika** , a następnie naciśnij klawisz **Enter** klucza.  
  
         lub  
  
    -   Przeciągnij formant zawartości z **przybornika** do dokumentu. Zawartości formant został dodany bieżące zaznaczenie w dokumencie, a nie lokalizacja wskaźnika myszy.  
  
> [!NOTE]  
>  Nie można dodać <xref:Microsoft.Office.Tools.Word.GroupContentControl> za pomocą **przybornika**. Można dodawać tylko <xref:Microsoft.Office.Tools.Word.GroupContentControl> w programie Word lub w czasie wykonywania.  
  
> [!NOTE]  
>  Program Visual Studio nie zawiera formantu zawartości pola wyboru w przyborniku. Aby dodać kontrolkę pola wyboru zawartości do dokumentu, należy utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiekt programowo. Aby uzyskać więcej informacji, zobacz [formanty zawartości](../vsto/content-controls.md).  
  
#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Aby dodać kontrolkę zawartości do dokumentu programu Word  
  
1.  W dokumencie, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta, umieść kursor, której chcesz dodać formant zawartości, lub zaznacz tekst, który ma formantu zawartości, aby zastąpić.  
  
2.  Na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, należy go najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  W **formanty** grupy, kliknij ikonę zawartości formantu, który chcesz dodać.  
  
##  <a name="runtimedoclevel"></a> Dodawanie formantów zawartości w czasie wykonywania w projektach na poziomie dokumentu  
 Można dodać formanty zawartości programowo do dokumentu w czasie wykonywania za pomocą metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwość `ThisDocument` klasy w projekcie. Każda metoda charakteryzuje się trzech przeciążeń, które umożliwiają dodawanie zawartości formantu w następujący sposób:  
  
-   Dodawanie formantu w bieżącym zaznaczeniu.  
  
-   Dodawanie formantu w określonym zakresie.  
  
-   Dodaj formant, który jest oparty na macierzystego formantu zawartości w dokumencie.  
  
 Tworzone dynamicznie zawartość, którą formanty nie są zachowywane w dokumencie, gdy dokument zostanie zamknięty. Jednak macierzystego formantu zawartości pozostanie w dokumencie. Można ponownie utworzyć formant zawartości, który jest oparty na macierzystego formantu zawartości przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
> [!NOTE]  
>  Aby dodać kontrolkę pola wyboru zawartości do dokumentu w projekcie programu Word 2010, należy utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiektu. Aby uzyskać więcej informacji, zobacz [formanty zawartości](../vsto/content-controls.md).  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>Aby dodać kontrolkę zawartości w bieżącym zaznaczeniu  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metodę o nazwie `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu zawartości, który chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i ma jeden parametr nazwę nowego formantu.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodę, aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do początku dokumentu. Aby uruchomić ten kod, Dodaj kod, aby `ThisDocument` klasy w projekcie i wywołanie `AddRichTextControlAtSelection` metody z `ThisDocument_Startup` obsługi zdarzeń.  
  
     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>Aby dodać kontrolkę zawartości w określonym zakresie  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metodę o nazwie `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu zawartości, który chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i ma <xref:Microsoft.Office.Interop.Word.Range> parametru.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodę, aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do początku dokumentu. Aby uruchomić ten kod, Dodaj kod, aby `ThisDocument` klasy w projekcie i wywołanie `AddRichTextControlAtRange` metody z `ThisDocument_Startup` obsługi zdarzeń.  
  
     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]  
  
### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Aby dodać kontrolkę zawartości, która jest oparta na macierzystego formantu zawartości  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metodę o nazwie `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu zawartości, który chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i ma `Microsoft.Office.Interop.Word.ContentControl` parametru.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metody, aby utworzyć nową <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dla każdego formantu natywnego tekstu sformatowanego, który znajduje się w dokumencie. Aby uruchomić ten kod, Dodaj kod, aby `ThisDocument` klasy w projekcie i wywołanie `CreateRichTextControlsFromNativeControls` metody z `ThisDocument_Startup` obsługi zdarzeń.  
  
     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> Dodawanie formantów zawartości w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Można dodać formanty zawartości programowo do otwartego dokumentu w czasie wykonywania za pomocą dodatku VSTO. W tym celu należy wygenerować <xref:Microsoft.Office.Tools.Word.Document> hosta elementu, który jest oparta na otwartego dokumentu, a następnie użyj metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości tego elementu host. Każda metoda charakteryzuje się trzech przeciążeń, które umożliwiają dodawanie zawartości formantu w następujący sposób:  
  
-   Dodawanie formantu w bieżącym zaznaczeniu.  
  
-   Dodawanie formantu w określonym zakresie.  
  
-   Dodaj formant, który jest oparty na macierzystego formantu zawartości w dokumencie.  
  
 Tworzone dynamicznie zawartość, którą formanty nie są zachowywane w dokumencie, gdy dokument zostanie zamknięty. Jednak macierzystego formantu zawartości pozostanie w dokumencie. Można ponownie utworzyć formant zawartości, który jest oparty na macierzystego formantu zawartości przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [utrwalić formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
 Aby uzyskać więcej informacji na temat generowania elementów hosta w projektów dodatku VSTO zobacz [dokumentów rozszerzania programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
> [!NOTE]  
>  Aby dodać kontrolkę pola wyboru zawartości do dokumentu, należy utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiektu. Aby uzyskać więcej informacji, zobacz [formanty zawartości](../vsto/content-controls.md).  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>Aby dodać kontrolkę zawartości w bieżącym zaznaczeniu  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metodę o nazwie `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu zawartości, który chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i ma jeden parametr nazwę nowego formantu.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodę, aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na początku aktywny dokument. Aby uruchomić ten kod, Dodaj kod, aby `ThisAddIn` klasy w projekcie i wywołanie `AddRichTextControlAtSelection` metody z `ThisAddIn_Startup` obsługi zdarzeń.  
  
     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>Aby dodać kontrolkę zawartości w określonym zakresie  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metodę o nazwie `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu zawartości, który chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i ma <xref:Microsoft.Office.Interop.Word.Range> parametru.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodę, aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na początku aktywny dokument. Aby uruchomić ten kod, Dodaj kod, aby `ThisAddIn` klasy w projekcie i wywołanie `AddRichTextControlAtRange` metody z `ThisAddIn_Startup` obsługi zdarzeń.  
  
     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]  
  
#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Aby dodać kontrolkę zawartości, która jest oparta na macierzystego formantu zawartości  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metodę o nazwie `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu zawartości, który chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i ma `Microsoft.Office.Interop.Word.ContentControl` parametru.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metody, aby utworzyć nową <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dla każdego formantu natywnego tekstu sformatowanego, który znajduje się w dokumencie, po otwarciu dokumentu. Aby uruchomić ten kod, Dodaj kod, aby `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]  
  
     Język C#, należy również dołączyć `Application_DocumentOpen` program obsługi zdarzeń do <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzeń.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]  
  
## <a name="see-also"></a>Zobacz także  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Program dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)  
  