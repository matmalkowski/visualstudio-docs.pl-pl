---
title: "Porady: zapełnianie arkuszy danymi z bazy danych | Dokumentacja firmy Microsoft"
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
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3b7cfb842a0372d4410a0794ff8ade901af713b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Porady: zapełnianie arkuszy danymi z bazy danych
  Można uzyskać dostępu do danych w projektach pakietu Office poziomie dokumentu w taki sam sposób, że uzyskujesz dostęp do danych w projektach formularzy systemu Windows. Użyj tego samego narzędzia i kodu można wyświetlić dane w ramach rozwiązania i formanty formularzy systemu Windows nawet służy do wyświetlania danych. Ponadto można korzystać formantów o nazwie formanty hosta, które są obiektów macierzystych w programie Microsoft Office Excel, które zostały rozszerzone za pomocą zdarzeń i możliwości wiązania danych. Aby uzyskać więcej informacji, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Poniższy przykład przedstawia sposób Dodaj formanty powiązane z danymi w przy użyciu projektanta projektów na poziomie dokumentu. Na przykład sposobu Dodaj formanty powiązane z danymi w projektach na poziomie aplikacji w czasie wykonywania, zobacz [wskazówki: złożone powiązanie danych w VSTO dodatku projektu](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: Transfer danych w arkuszu programu Excel?](http://go.microsoft.com/fwlink/?LinkID=130277), i [jak czy I: korzystać z bazy danych w programie Excel?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="adding-a-data-bound-control-to-a-worksheet-at-design-time"></a>Dodawanie formantu powiązanego z danymi do arkusza w czasie projektowania  
  
#### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Aby wypełnić arkusza z danymi z bazy danych  
  
1.  Otwórz projekt poziomie dokumentu programu Excel w programie Visual Studio, po otwarciu arkusza w projektancie.  
  
2.  Otwórz **źródeł danych** okna i Utwórz źródło danych dla projektu. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
3.  Przeciągnij pola lub tabeli z **źródeł danych** okna do arkusza.  
  
 Jedną z poniższych formantów jest tworzony w arkuszu:  
  
-   Jeśli możesz przeciągnąć pola, <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki jest tworzona w arkuszu. Aby uzyskać więcej informacji, zobacz [namedrange — formant](../vsto/namedrange-control.md).  
  
-   Przeciągnięcie tabeli, <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki jest tworzona w arkuszu. Aby uzyskać więcej informacji, zobacz [ListObject — formant](../vsto/listobject-control.md).  
  
 Można dodać inny formant, wybierając w tabeli lub pola w **źródeł danych** okna, a następnie wybierając inny formant z listy rozwijanej.  
  
## <a name="objects-in-the-project"></a>Obiekty w projekcie  
 Oprócz formantu następujące obiekty powiązane dane są automatycznie dodawane do projektu:  
  
-   Typizowany zestaw danych, który hermetyzuje tabel danych, które podłączone do bazy danych. Aby uzyskać więcej informacji, zobacz [narzędzia zestawu danych w programie Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
-   A <xref:System.Windows.Forms.BindingSource> łączące formantu się typizowanego obiektu dataset. Aby uzyskać więcej informacji, zobacz [informacje o składniku BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
-   TableAdapter, łączącego typizowany zestaw danych do bazy danych. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
-   Obiekt TableAdapterManager, który służy do koordynowania adaptery tabel w zestawie danych do włączenia hierarchicznej aktualizacji. Aby uzyskać więcej informacji, zobacz [hierarchiczna aktualizacja](../data-tools/hierarchical-update.md) i [odwołania TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).  
  
 Po uruchomieniu projektu kontrolka Wyświetla pierwszy rekord w źródle danych. Można użyć <xref:System.Windows.Forms.BindingSource> aby umożliwić użytkownikom do przewijania rekordów.  
  
#### <a name="to-scroll-through-the-records"></a>Do przewijania rekordów  
  
-   Użyj <xref:System.Windows.Forms.BindingSource> metod, takich jak <xref:System.Windows.Forms.BindingSource.MoveNext%2A> i <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Aby dowiedzieć się, jak wysyłać aktualizacje do typizowanego obiektu dataset i bazę danych, zobacz [porady: aktualizowanie źródła danych danymi z kontrolką hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources)   
 [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Porady: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Porady: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Porady: aktualizowanie źródła danych danymi z formanty hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Jak I: transferu danych w arkuszu programu Excel](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [Jak I: używać bazy danych w programie Excel](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  