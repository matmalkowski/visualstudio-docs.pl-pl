---
title: 'Porady: zapełnianie dokumentów danymi z bazy danych'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3e6ad96b77eef4ba7bb0a90447b307eb340d8f20
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255333"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Porady: zapełnianie dokumentów danymi z bazy danych
  Miały dostęp do danych w projektach na poziomie dokumentu dla programu Microsoft Office, w taki sam sposób, że uzyskujesz dostęp do danych w projektach formularzy systemu Windows. Używania tego samego narzędzia i kod, aby przenosić dane z bazy danych w ramach rozwiązania i formanty formularzy systemu Windows można użyć do wyświetlania danych.  
  
 Ponadto można wyświetlić dane za pomocą formantów hosta. Formanty hosta są obiektów macierzystych w programie Microsoft Office Word, które zostały rozszerzone za pomocą zdarzeń i możliwość powiązania danych. Aby uzyskać więcej informacji, zobacz [elementów, a informacje o formantach](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Poniższy przykład przedstawia sposób Dodaj formanty powiązane z danymi w przy użyciu projektanta projektów na poziomie dokumentu. Na przykład sposobu Dodaj formanty powiązane z danymi w projektów dodatku VSTO w czasie wykonywania, zobacz [wskazówki: proste powiązanie danych w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [powiązywanie danych do programu Word 2007 zawartości kontrolki za pomocą narzędzi Visual Studio Tools dla pakietu Office (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## <a name="add-a-control-to-a-document-at-design-time"></a>Dodawanie formantu do dokumentu w czasie projektowania  
  
### <a name="to-populate-a-document-with-data-from-a-database"></a>Aby wypełnić dokument z danymi z bazy danych  
  
1.  Otwórz projekt poziomie dokumentu programu Word w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dokument jest otwarty w projektancie.  
  
2.  Otwórz **źródeł danych** okna i Utwórz źródło danych z bazy danych. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
3.  Przeciągnij pola z **źródeł danych** okna do dokumentu.  
  
 Formant zawartości jest dodawany do dokumentu. Typ zawartości formantu zależy od typu danych wybranego pola. Aby uzyskać więcej informacji, zobacz [formanty zawartości](../vsto/content-controls.md).  
  
 Inny formant można dodawać przez zaznaczenie pola danych w **źródeł danych** okna, a następnie wybierając inny formant z listy rozwijanej.  
  
## <a name="objects-in-the-project"></a>Obiekty w projekcie  
 Oprócz formantu następujące obiekty powiązane dane są automatycznie dodawane do projektu:  
  
-   Typizowany zestaw danych, który hermetyzuje tabel danych, które podłączone do bazy danych. Aby uzyskać więcej informacji, zobacz [narzędzia zestawu danych w programie Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
-   A <xref:System.Windows.Forms.BindingSource> łączące formantu się typizowanego obiektu dataset. Aby uzyskać więcej informacji, zobacz [informacje o składniku BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
-   TableAdapter, łączącego typizowany zestaw danych do bazy danych. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
-   Obiekt TableAdapterManager, który służy do koordynowania adaptery tabel w zestawie danych do włączenia hierarchicznej aktualizacji. Aby uzyskać więcej informacji, zobacz [hierarchiczna aktualizacja](../data-tools/hierarchical-update.md) i [odwołania TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).  
  
 Po uruchomieniu projektu kontrolka Wyświetla pierwszy rekord w źródle danych. Można użyć <xref:System.Windows.Forms.BindingSource> aby umożliwić użytkownikom do przewijania rekordów.  
  
### <a name="to-scroll-through-the-records"></a>Do przewijania rekordów  
  
-   Użyj <xref:System.Windows.Forms.BindingSource> metod, takich jak <xref:System.Windows.Forms.BindingSource.MoveNext%2A> i <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Aby dowiedzieć się, jak wysyłać aktualizacje do typizowanego obiektu dataset i bazę danych, zobacz [porady: aktualizowanie źródła danych danymi z kontrolką hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources)   
 [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Porady: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Porady: aktualizowanie źródła danych danymi z formanty hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Użyj plików lokalnej bazy danych w rozwiązań Office ― omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Łączenie z danymi w aplikacjach formularzy systemu Windows](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Informacje o składniku BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  