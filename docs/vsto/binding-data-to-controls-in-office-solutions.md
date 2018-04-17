---
title: Wiązanie danych do kontrolek w rozwiązaniach pakietu Office | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ea9d344e3b36d9d46ea5a5adcb642e43687b75ee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="binding-data-to-controls-in-office-solutions"></a>Powiązywanie danych do kontrolek w rozwiązaniach pakietu Office
  Formanty formularzy systemu Windows można powiązać i *hostowania formantów* dla dokumentu programu Microsoft Office Word lub Arkusz Microsoft Office Excel ze źródłem danych, więc formanty automatycznie wyświetlić dane. Formanty w projektach na poziomie aplikacji jak również poziomie dokumentu można powiązać danych.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Formanty hosta rozszerza obiekty, które znajdują się w programach Word i Excel modele obiektów, takich jak formantów zawartości w programie Word i nazwanych zakresów w programie Excel. Aby uzyskać więcej informacji, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
 Zarówno formularzy systemu Windows, jak i formantów hosta korzystają z modelu powiązanie danych formularzy systemu Windows, który obsługuje zarówno *proste powiązanie danych* i *złożone powiązanie danych* ze źródłami danych, takich jak tabele zestawów danych i danych. Aby uzyskać pełne informacje na temat modelu powiązania danych w formularzach systemu Windows, zobacz [powiązania danych i formularze systemu Windows](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: korzystać z bazy danych w programie Excel?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="simple-data-binding"></a>Proste powiązanie danych  
 Proste powiązanie danych występuje, gdy właściwość formantu jest powiązana z elementu danych, takie jak wartości w tabeli danych. Na przykład <xref:Microsoft.Office.Tools.Excel.NamedRange> formant ma <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości, które mogą być powiązane z polem w zestawie danych. Gdy zmieni się pole w zestawie danych, zmienia się również wartość nazwanego zakresu Wszystkie formanty, hosta, z wyjątkiem <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolować, obsługuje proste powiązanie danych. <xref:Microsoft.Office.Tools.Word.XMLNodes> Kontroli jest kolekcją, i dlatego nie obsługuje powiązanie danych.  
  
 Aby wykonać proste powiązanie danych z formantem hosta, dodać <xref:System.Windows.Forms.Binding> właściwości powiązania danych formantu. A <xref:System.Windows.Forms.Binding> obiekt reprezentuje proste powiązanie między wartości właściwości formantu i wartość elementu danych.  
  
 W poniższym przykładzie pokazano, jak można powiązać <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości elementu danych w projektach na poziomie dokumentu.  
  
 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]  
  
 Aby uzyskać wskazówki, która przedstawia proste powiązanie danych, zobacz [wskazówki: proste powiązanie danych w projektach na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) dla projektu na poziomie dokumentu i [wskazówki: proste powiązanie danych w VSTO dodatku projektu ](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) w projekcie dodatku VSTO.  
  
## <a name="complex-data-binding"></a>Złożone powiązanie danych  
 Złożone powiązanie danych występuje, gdy właściwość formantu jest powiązana z więcej niż jeden element danych, takich jak wiele kolumn w tabeli danych. <xref:Microsoft.Office.Tools.Excel.ListObject> Kontroli dla programu Excel jest tylko kontroli hosta, który obsługuje złożone powiązanie danych. Istnieją również wiele formantów formularzy systemu Windows, które obsługują złożone powiązanie danych, takich jak <xref:System.Windows.Forms.DataGridView> formantu.  
  
 Aby wykonać złożone powiązanie danych, ustaw właściwość formantu do obiektu źródła danych, która jest obsługiwana przez złożone powiązanie danych. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> właściwość <xref:Microsoft.Office.Tools.Excel.ListObject> formantu można powiązać wiele kolumn w tabeli danych. Wszystkie dane w tabeli danych zostanie wyświetlony w <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli i jak dane w tabeli zmian danych, <xref:Microsoft.Office.Tools.Excel.ListObject> również zmiany. Aby uzyskać listę źródeł danych, które umożliwiają złożone powiązanie danych, zobacz [danych źródła obsługiwane przez program Windows Forms](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).  
  
 Poniższy przykład kodu tworzy <xref:System.Data.DataSet> z dwoma <xref:System.Data.DataTable> obiekty i wypełnia jedną z tabel z danymi. Następnie wiąże kod <xref:Microsoft.Office.Tools.Excel.ListObject> do tabeli, która zawiera dane. W tym przykładzie jest dla projektu na poziomie dokumentu programu Excel.  
  
 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]  
  
 Aby uzyskać wskazówki dotyczące pokazują złożone powiązanie danych, zobacz [wskazówki: złożone powiązanie danych w projektach na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) dla projektu na poziomie dokumentu i [wskazówki: złożone powiązanie danych w VSTO dodatku projektu ](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) w projekcie dodatku VSTO.  
  
## <a name="displaying-data-in-documents-and-workbooks"></a>Wyświetlanie danych w dokumentach i skoroszytów  
 W projektach na poziomie dokumentu, można użyć **źródeł danych** okno, aby łatwo Dodaj formanty powiązane z danymi do dokumentów lub skoroszytów, ten sam sposób, możesz użyć dla formularzy systemu Windows. Aby uzyskać więcej informacji o korzystaniu z **źródeł danych** okna, zobacz [formanty formularzy systemu Windows powiązać z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) i [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md).  
  
### <a name="dragging-controls-from-the-data-sources-window"></a>Przeciąganie z okna źródeł danych kontrolki  
 Formant jest tworzony w dokumencie, gdy obiekt zostanie przeciągnięty na go z **źródeł danych** okna. Typ formantu, który jest tworzony zależy od tego, czy powiązanie pojedynczej kolumny danych lub wiele kolumn z danymi.  
  
 Dla programu Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki jest tworzona w arkuszu dla każdego indywidualnego pola i <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli jest tworzony dla każdego zakresu danych, który zawiera wiele wierszy i kolumn. Możesz zmienić to ustawienie domyślne, wybierając w tabeli lub pola w **źródeł danych** okna, a następnie wybierając inny formant z listy rozwijanej.  
  
 A <xref:Microsoft.Office.Tools.Word.ContentControl> formant został dodany do dokumentów. Typ zawartości formantu zależy od typu danych wybranego pola.  
  
### <a name="binding-data-in-document-level-projects-at-design-time"></a>Wiązanie danych w projektach na poziomie dokumentu w czasie projektowania  
 W następujących tematach opisano przykłady powiązania danych w czasie projektowania:  
  
-   [Instrukcje: Zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)  
  
-   [Instrukcje: Zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)  
  
-   [Instrukcje: Zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)  
  
-   [Instrukcje: Zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
-   [Instrukcje: Przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)  
  
### <a name="binding-data-in-vsto-add-in-projects"></a>Powiązanie danych w projektach w dodatku VSTO  
 W dodatku VSTO projektów można dodawać formanty tylko w czasie wykonywania. W następujących tematach opisano przykłady powiązania danych w czasie wykonywania:  
  
-   [Przewodnik: Proste powiązanie danych w projektach dodatku narzędzi VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)  
  
-   [Przewodnik: Złożone powiązanie danych w projektach dodatku VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)  
  
## <a name="updating-data-that-is-bound-to-host-controls"></a>Aktualizowanie danych powiązanej z formanty hosta  
 Powiązanie danych między źródłem danych i kontroli hosta obejmuje aktualizacji dwukierunkowe danych. W proste powiązanie danych, zmian w źródle danych są automatycznie odzwierciedlane w formancie hosta, ale zmiany w formancie hosta wymagają jawnym wywołaniem do aktualizowania źródła danych. Przyczyną jest to, że w niektórych przypadkach, zmiany w jedno pole powiązane z danymi nie zostały zaakceptowane, chyba że posiadają zmiany w innym polu powiązane z danymi. Na przykład może być dwa pola, jeden dla wieku i jeden lat środowisko. Środowisko nie może przekraczać wieku. Użytkownik nie może zaktualizować wieku od 50 do 25, a następnie środowisko od 30 do 10, chyba że użytkownik wprowadza zmiany w tym samym czasie. Aby rozwiązać ten problem, pola z proste powiązanie danych nie zostaną zaktualizowane aktualizacje jawnie są wysyłane przez kod.  
  
 Aby zaktualizować źródła danych z formantami hosta, które umożliwiają proste powiązanie danych, musisz wysłać aktualizacje do źródła danych w pamięci (takie jak <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>) i bazą danych zaplecza, jeśli rozwiązanie korzysta z jednego.  
  
 Nie trzeba jawnie aktualizowania źródła danych w pamięci podczas wykonywania złożone powiązanie danych przy użyciu <xref:Microsoft.Office.Tools.Excel.ListObject> formantu. W takim przypadku zmiany są automatycznie wysyłane do źródła danych w pamięci bez dodatkowego kodu.  
  
 Aby uzyskać więcej informacji, zobacz [porady: aktualizowanie źródła danych danymi z kontrolką hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Jak I: używać bazy danych w programie Excel](http://go.microsoft.com/fwlink/?LinkID=130287)   
 [Powiązanie danych i formularze systemu Windows](/dotnet/framework/winforms/data-binding-and-windows-forms)   
 [Porady: Tworzenie prostego formantu powiązanego na formularzu systemu Windows](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)   
 [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Zapisywanie danych w bazie danych](../data-tools/save-data-back-to-the-database.md)    
 [Aktualizowanie danych za pomocą TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Buforowanie danych](../vsto/caching-data.md)   
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)  
  
  