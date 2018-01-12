---
title: "Porady: zapełnianie dokumentów danymi z obiektów | Dokumentacja firmy Microsoft"
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
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 02f2b735ceb473f7ffe55345c1cd45dc084edb80
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Porady: zapełnianie dokumentów danymi z obiektów
  Dane w celu dostępu w obiekcie danych działa tak samo w projektach na poziomie dokumentu, dla programu Microsoft Office Word, co w projektach formularzy systemu Windows. Użyj tego samego narzędzia i kod do przeniesienia danych z obiektu do rozwiązania, a formanty formularzy systemu Windows można użyć do wyświetlania danych. Ponadto można wyświetlić dane za pomocą formantów hosta. Formanty hosta są obiektów macierzystych w programie Microsoft Office Word, które zostały rozszerzone za pomocą zdarzeń i możliwość powiązania danych. Aby uzyskać więcej informacji, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Należy wykonać trzy podstawowe kroki, aby wypełnić dokumentu przy użyciu danych z obiektu:  
  
-   Dodawanie formantu do dokumentu, które można powiązać z danymi.  
  
-   Dodaj obiekt danych do dokumentu.  
  
-   Połącz obiekt danych do parametru BindingSource.   
  
## <a name="adding-a-data-object"></a>Dodawanie obiektu danych  
  
#### <a name="to-add-a-data-object"></a>Aby dodać obiekt danych  
  
-   Otwórz **źródeł danych** okna i Utwórz źródło danych z obiektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).  
  
## <a name="connecting-the-data-object-to-the-bindingsource"></a>Obiekt danych nawiązywania połączenia z BindingSource  
 W projektach na poziomie dokumentu Dodaj formanty do dokumentu i powiązać je z danymi w czasie projektowania.  
  
 Projektów dodatku VSTO służy do tworzenia kontrolek i powiązać je w czasie wykonywania.  
  
### <a name="document-level-projects"></a>Projektów na poziomie dokumentu  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Element BindingSource nawiązać połączenia obiektu danych  
  
1.  Przeciągnij pole danych z **źródeł danych** okna do dokumentu. Powoduje to automatyczne utworzenie formantu.  
  
2.  W kodzie należy utworzyć wystąpienia typu obiektu, który został wybrany dla źródła danych.  
  
3.  Przypisz wystąpienie do <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="application-level-projects"></a>Projektów na poziomie aplikacji  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Element BindingSource nawiązać połączenia obiektu danych  
  
1.  W kodzie należy utworzyć wystąpienia typu obiektu, który jest skojarzony ze źródłem danych.  
  
2.  Utwórz wystąpienie <xref:System.Windows.Forms.BindingSource>.  
  
3.  Źródło danych, aby przypisać <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość <xref:System.Windows.Forms.BindingSource>.  
  
4.  Dodaj źródło danych jako powiązań danych z formantem.  
  
## <a name="see-also"></a>Zobacz też  
 
 [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources)   
 [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Stduio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)
 
 [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Porady: aktualizowanie źródła danych danymi z formanty hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Łączenie z danymi w aplikacjach formularzy systemu Windows](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource, składnik — omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  