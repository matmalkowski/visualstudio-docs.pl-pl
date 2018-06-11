---
title: 'Porady: zapełnianie dokumentów danymi z obiektów'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5a7dee9c56b454ad7d9213817c62b0ea4fbe7c8c
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255752"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Porady: zapełnianie dokumentów danymi z obiektów
  Dane w celu dostępu w obiekcie danych działa tak samo w projektach na poziomie dokumentu, dla programu Microsoft Office Word, co w projektach formularzy systemu Windows. Użyj tego samego narzędzia i kod do przeniesienia danych z obiektu do rozwiązania, a formanty formularzy systemu Windows można użyć do wyświetlania danych. Ponadto można wyświetlić dane za pomocą formantów hosta. Formanty hosta są obiektów macierzystych w programie Microsoft Office Word, które zostały rozszerzone za pomocą zdarzeń i możliwość powiązania danych. Aby uzyskać więcej informacji, zobacz [elementów, a informacje o formantach](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Należy wykonać trzy podstawowe kroki, aby wypełnić dokumentu przy użyciu danych z obiektu:  
  
-   Dodawanie formantu do dokumentu, które można powiązać z danymi.  
  
-   Dodaj obiekt danych do dokumentu.  
  
-   Połącz obiekt danych do parametru BindingSource.   
  
## <a name="add-a-data-object"></a>Dodaj obiekt danych  
  
### <a name="to-add-a-data-object"></a>Aby dodać obiekt danych  
  
-   Otwórz **źródeł danych** okna i Utwórz źródło danych z obiektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).  
  
## <a name="connect-the-data-object-to-the-bindingsource"></a>Połącz obiekt danych do parametru BindingSource  
 W projektach na poziomie dokumentu Dodaj formanty do dokumentu i powiązać je z danymi w czasie projektowania.  
  
 Projektów dodatku VSTO służy do tworzenia kontrolek i powiązać je w czasie wykonywania.  
  
### <a name="document-level-projects"></a>Projektów na poziomie dokumentu  
  
#### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Element BindingSource nawiązać połączenia obiektu danych  
  
1.  Przeciągnij pole danych z **źródeł danych** okna do dokumentu. Powoduje to automatyczne utworzenie formantu.  
  
2.  W kodzie należy utworzyć wystąpienia typu obiektu, który został wybrany dla źródła danych.  
  
3.  Przypisz wystąpienie do <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="application-level-projects"></a>Projektów na poziomie aplikacji  
  
#### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Element BindingSource nawiązać połączenia obiektu danych  
  
1.  W kodzie należy utworzyć wystąpienia typu obiektu, który jest skojarzony ze źródłem danych.  
  
2.  Utwórz wystąpienie <xref:System.Windows.Forms.BindingSource>.  
  
3.  Źródło danych, aby przypisać <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość <xref:System.Windows.Forms.BindingSource>.  
  
4.  Dodaj źródło danych jako powiązań danych z formantem.  
  
## <a name="see-also"></a>Zobacz także  
 
 [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources)   
 [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)
 
 [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Porady: aktualizowanie źródła danych danymi z formanty hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Łączenie z danymi w aplikacjach formularzy systemu Windows](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Informacje o składniku BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  