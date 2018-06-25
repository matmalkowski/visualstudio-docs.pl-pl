---
title: 'Porady: zapełnianie dokumentów danymi z usług'
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
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ac901b524818086d6dbf23b7b55487054170b3e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758545"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Porady: zapełnianie dokumentów danymi z usług

Dostęp do danych działa tak samo w projektach na poziomie dokumentu, Microsoft Office, co w projektach formularzy systemu Windows. Użyj tego samego narzędzia i kodu można wyświetlić dane w ramach rozwiązania i formanty formularzy systemu Windows nawet służy do wyświetlania danych. Ponadto można korzystać formantów o nazwie formanty hosta, które są w Microsoft Office Excel i Microsoft Office Word natywnego obiekty, które zostały rozszerzone za pomocą zdarzeń i możliwość powiązania danych. Aby uzyskać więcej informacji, zobacz [elementów, a informacje o formantach](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

Poniższy przykład przedstawia sposób Dodaj formanty powiązane z danymi do dokumentów w czasie projektowania. Na przykład sposobu Dodaj formanty powiązane z danymi w dodatkach VSTO w czasie wykonywania, zobacz [wskazówki: powiązanie z danymi z usług w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak I: interakcji z usługami sieci web z programu Microsoft Excel?](http://go.microsoft.com/fwlink/?LinkID=130284).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Aby wypełnić projektu poziomie dokumentu przy użyciu danych z usługi sieci web

1.  Otwórz **źródeł danych** okna i Utwórz źródło danych usługi dla projektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md).

2.  Przeciągnij tabelę lub pole z **źródeł danych** okna do dokumentu.

     Formant jest tworzony w dokumencie <xref:System.Windows.Forms.BindingSource> utworzeniu który jest powiązany z klasy obiektów w projekcie, a klasy są generowane przez usługę.

3.  W kodzie należy utworzyć wystąpienia klasy usługi sieci web, którą połączenia w kroku 1.

4.  Jeśli nie ma właściwości, które są wymagane do komunikacji z usługą sieci web, tworzenie wystąpień tych właściwości.

5.  Tworzenie i wysyłanie żądania danych za pomocą metody ujawnione przez usługę sieci Web i wszystkie wystąpienia właściwości utworzonej w kroku 4.

     Metody, których można użyć zależą od tego, jakie usługi sieci web oferuje.

6.  Przypisz odpowiedzi danych z usługi sieci web <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość <xref:System.Windows.Forms.BindingSource>.

Po uruchomieniu projektu kontrolki wyświetlić pierwszy rekord w źródle danych. Można włączyć przewijanie rekordów dzięki obsłudze zdarzeń waluty, za pomocą obiektów <xref:System.Windows.Forms.BindingSource>.

## <a name="see-also"></a>Zobacz także

- [Wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Porady: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Porady: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Porady: aktualizowanie źródła danych danymi z formanty hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)