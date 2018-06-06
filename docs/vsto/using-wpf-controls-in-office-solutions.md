---
title: Użyj formantów WPF w rozwiązaniach pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 87305902c80d9848df63d2c8bd9f431fd93a5508
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767598"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Użyj formantów WPF w rozwiązaniach pakietu Office
  Mimo że rozwiązania utworzone przy użyciu narzędzi programowania pakietu Office w Visual Studio zostały zaprojektowane do pracy z bezpośrednio z formanty formularzy systemu Windows, umożliwia także formantów WPF w ramach rozwiązań. Windows Presentation Foundation (WPF) stanowi alternatywę do formularzy systemu Windows dla projektowanie interfejsów użytkownika. WPF używa język o nazwie Extensible Application Markup Language (XAML), aby zapewnić nowe techniki do włączania interfejsu użytkownika, nośniki i dokumenty. Aby uzyskać więcej informacji, zobacz [wprowadzenie do platformy WPF w programie Visual Studio 2015](/dotnet/framework/wpf/getting-started/introduction-to-wpf-in-vs).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Dowolny element interfejsu użytkownika, który może zawierać formanty formularzy systemu Windows w rozwiązaniach pakietu Office może również obsługiwać formantów WPF. W tym następujące elementy:  
  
-   Dokumenty i arkuszy w dostosowaniach na poziomie dokumentu.  
  
-   Okienka akcji w dostosowaniach na poziomie dokumentu.  
  
-   Niestandardowe okienka zadań w dodatkach VSTO.  
  
-   Regiony formularzy w dodatkach VSTO dla programu Outlook.  
  
## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Dodawanie formantów WPF do projektów pakietu Office w czasie projektowania  
 Nie można dodać formantów WPF bezpośrednio do elementów interfejsu użytkownika w rozwiązaniach pakietu Office. Zamiast tego dodać **kontrolki użytkownika (WPF)** elementu do projektu i używać go jako powierzchni projektowej formantów WPF. Następnie dodaj formanty użytkownika WPF do elementu interfejsu użytkownika w projekcie.  
  
### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Do dodawania formantów WPF w okienku Akcje, niestandardowego okienka zadań lub regionu formularza  
  
1.  Otwórz projekt, do którego chcesz dodać niestandardowego okienka zadań, w okienku Akcje lub regionu formularza.  
  
2.  Dodaj **kontrolki użytkownika (WPF)** elementu do projektu.  
  
3.  Z **przybornika**, Dodaj formanty WPF na powierzchnię projektu kontrolki użytkownika WPF.  
  
     Domyślnie po otwarciu projektanta formantów WPF użytkownika **przybornika** zawiera tylko formantów WPF.  
  
4.  Skompiluj projekt.  
  
5.  Dodaj do projektu w okienku Akcje, regionu formularza lub niestandardowego okienka zadań:  
  
    -   Regiony formularzy można dodać **regionów formularzy programu Outlook** elementu do projektu. Aby uzyskać więcej informacji, zobacz [porady: dodawanie regionu formularza do projektu dodatek programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
    -   Okienka akcji można dodać **formant okienka Akcje** lub **kontrolki użytkownika** elementu do projektu. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie okienek akcji do dokumentów programu Word lub skoroszyty programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) i [porady: Dodawanie okienek akcji do dokumentów programu Word lub skoroszyty programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
    -   Niestandardowe okienka zadań, można dodać **kontrolki użytkownika** elementu do projektu. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
6.  Z *ProjectName* **formanty użytkownika WPF** karcie **przybornika**, przeciągnij formanty użytkownika WPF do projektanta w okienku Akcje, regionu formularza lub niestandardowego okienka zadań.  
  
     Program Visual Studio automatycznie tworzy <xref:System.Windows.Forms.Integration.ElementHost> obiekt, który zawiera formanty użytkownika WPF dla elementu interfejsu użytkownika.  
  
7.  Skompiluj ponownie projekt.  
  
#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Do dodawania formantów WPF w dokumencie lub arkusz w projektach na poziomie dokumentu  
  
1.  Otwórz projekt poziomie dokumentu dla programu Word i Excel.  
  
2.  Dodaj **kontrolki użytkownika (WPF)** elementu do projektu.  
  
3.  Z **przybornika**, Dodaj formanty WPF na powierzchnię projektu kontrolki użytkownika WPF.  
  
4.  Skompiluj projekt.  
  
5.  Dodaj **kontrolki użytkownika** elementu (to znaczy formantu użytkownika formularzy systemu Windows) do projektu.  
  
6.  Otwórz projektanta dla formantu użytkownika formularzy systemu Windows.  
  
7.  Z *ProjectName* **formanty użytkownika WPF** karcie **przybornika**, przeciągnij formanty użytkownika WPF do projektanta.  
  
     Program Visual Studio automatycznie tworzy <xref:System.Windows.Forms.Integration.ElementHost> obiekt, który zawiera formanty użytkownika WPF w formancie użytkownika formularzy systemu Windows.  
  
8.  Pisanie kodu, który programowo dodaje formantu użytkownika formularzy systemu Windows do dokumentu lub skoroszytu. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
    > [!NOTE]  
    >  Nie można przeciągnąć formantu użytkownika formularzy systemu Windows do dokumentu lub arkusza w projektancie.  
  
9. Skompiluj ponownie projekt.  
  
## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Formanty WPF hosta za pomocą klasy ElementHost  
 Program Visual Studio udostępnia funkcje, które ułatwiają używać formanty formularzy systemu Windows w ramach rozwiązań pakietu Office, ale nie zapewnia funkcje podobne do formantów WPF. Na przykład dodaniem formanty formularzy systemu Windows do dokumentów i arkuszy w czasie projektowania, przeciągając formanty z **przybornika**, lub w czasie wykonywania za pomocą metody pomocnicze. Jednak te narzędzia nie są dostępne dla formantów WPF.  
  
 WPF steruje użyciem <xref:System.Windows.Forms.Integration.ElementHost> klasy jako warstwa integracji między formantu formularzy systemu Windows lub formularza i formantów WPF. Po dodaniu formantów WPF do rozwiązania w czasie projektowania Visual Studio automatycznie generuje <xref:System.Windows.Forms.Integration.ElementHost> obiekt.  
  
## <a name="wpf-resources"></a>Zasoby WPF  
 Aby uzyskać więcej informacji na temat architektury i zagadnienia dotyczące projektowania, hostingu formantów WPF w formularzach i formanty formularzy systemu Windows zobacz następujące tematy:  
  
-   [Architektura wejściowych współdziałania formularzy systemu Windows i WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)  
  
-   [Mapowanie właściwości formularzy systemu Windows i WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)  
  
-   [Współdziałanie z WPF i formularze systemu Windows](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)  
  
-   [Formanty formularzy systemu Windows i równoważne WPF kontrolki](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)  
  
 Aby uzyskać więcej informacji na temat dodawania formantów WPF formanty formularzy systemu Windows i formularzy w programie Visual Studio w czasie projektowania zobacz następujące tematy:  
  
-   [Wskazówki: Tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)  
  
-   [Wskazówki: Rozmieszczanie zawartości WPF na formularzach systemu Windows w czasie projektowania](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)  
  
-   [Wskazówki: Stylu zawartości WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)  
  
## <a name="see-also"></a>Zobacz także  
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Formanty formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Porady: Dodawanie okienek akcji do dokumentów programu Word lub skoroszyty programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Porady: Dodawanie okienek akcji do dokumentów programu Word lub skoroszyty programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Porady: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Porady: dodawanie regionu formularza do projektu dodatek programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  