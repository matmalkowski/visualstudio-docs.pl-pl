---
title: "Korzystanie z formantów WPF w rozwiązaniach pakietu Office | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 74ee8c574f6f654aca166844d85a30f2d3d9d4c3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="using-wpf-controls-in-office-solutions"></a>Korzystanie z formantów WPF w rozwiązaniach pakietu Office
  Mimo że rozwiązania utworzone przy użyciu narzędzi programowania pakietu Office w Visual Studio zostały zaprojektowane do pracy z bezpośrednio z formanty formularzy systemu Windows, umożliwia także formantów WPF w ramach rozwiązań. Windows Presentation Foundation (WPF) stanowi alternatywę do formularzy systemu Windows dla projektowanie interfejsów użytkownika. WPF używa język o nazwie Extensible Application Markup Language (XAML), aby zapewnić nowe techniki do włączania interfejsu użytkownika, nośniki i dokumenty. Aby uzyskać więcej informacji, zobacz [wprowadzenie do platformy WPF w programie Visual Studio 2015](/dotnet/framework/wpf/getting-started/introduction-to-wpf-in-vs).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Dowolny element interfejsu użytkownika, który może zawierać formanty formularzy systemu Windows w rozwiązaniach pakietu Office może również obsługiwać formantów WPF. W tym następujące elementy:  
  
-   Dokumenty i arkuszy w dostosowaniach na poziomie dokumentu.  
  
-   Okienka akcji w dostosowaniach na poziomie dokumentu.  
  
-   Niestandardowe okienka zadań w dodatkach VSTO.  
  
-   Regiony formularzy w dodatkach VSTO dla programu Outlook.  
  
## <a name="adding-wpf-controls-to-office-projects-at-design-time"></a>Dodawanie formantów WPF w projektach pakietu Office w czasie projektowania  
 Nie można dodać formantów WPF bezpośrednio do elementów interfejsu użytkownika w rozwiązaniach pakietu Office. Zamiast tego dodać **kontrolki użytkownika (WPF)** elementu do projektu i używać go jako powierzchni projektowej formantów WPF. Następnie dodaj formanty użytkownika WPF do elementu interfejsu użytkownika w projekcie.  
  
#### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Do dodawania formantów WPF w okienku Akcje, niestandardowego okienka zadań lub regionu formularza  
  
1.  Otwórz projekt, do którego chcesz dodać niestandardowego okienka zadań, w okienku Akcje lub regionu formularza.  
  
2.  Dodaj **kontrolki użytkownika (WPF)** elementu do projektu.  
  
3.  Z **przybornika**, Dodaj formanty WPF na powierzchnię projektu kontrolki użytkownika WPF.  
  
     Domyślnie po otwarciu projektanta formantów WPF użytkownika **przybornika** zawiera tylko formantów WPF.  
  
4.  Skompiluj projekt.  
  
5.  Dodaj do projektu w okienku Akcje, regionu formularza lub niestandardowego okienka zadań:  
  
    -   Regiony formularzy można dodać **regionów formularzy programu Outlook** elementu do projektu. Aby uzyskać więcej informacji, zobacz [porady: dodawanie regionu formularza do projektu dodaj programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
    -   Okienka akcji można dodać **formant okienka Akcje** lub **kontrolki użytkownika** elementu do projektu. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) i [porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
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
  
## <a name="hosting-wpf-controls-by-using-the-elementhost-class"></a>Hosting formantów WPF przy użyciu klasy ElementHost  
 Program Visual Studio udostępnia funkcje, które ułatwiają używać formanty formularzy systemu Windows w ramach rozwiązań pakietu Office, ale nie zapewnia funkcje podobne do formantów WPF. Na przykład dodaniem formanty formularzy systemu Windows do dokumentów i arkuszy w czasie projektowania, przeciągając formanty z **przybornika**, lub w czasie wykonywania za pomocą metody pomocnicze. Jednak te narzędzia nie są dostępne dla formantów WPF.  
  
 WPF steruje użyciem <xref:System.Windows.Forms.Integration.ElementHost> klasy jako warstwa integracji między formantu formularzy systemu Windows lub formularza i formantów WPF. Po dodaniu formantów WPF do rozwiązania w czasie projektowania Visual Studio automatycznie generuje <xref:System.Windows.Forms.Integration.ElementHost> obiekt.  
  
## <a name="wpf-resources"></a>Zasoby WPF  
 Aby uzyskać więcej informacji na temat architektury i zagadnienia dotyczące projektowania, hostingu formantów WPF w formularzach i formanty formularzy systemu Windows zobacz następujące tematy:  
  
-   [Architektura danych wejściowych współdziałania dla Windows Forms i WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)  
  
-   [Mapowanie właściwości Windows Forms i WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)  
  
-   [Współdziałanie WPF i Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)  
  
-   [Kontrolki formularzy Windows Forms i równoważne kontrolki WPF](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)  
  
 Aby uzyskać więcej informacji na temat dodawania formantów WPF formanty formularzy systemu Windows i formularzy w programie Visual Studio w czasie projektowania zobacz następujące tematy:  
  
-   [Przewodnik: tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)  
  
-   [Przewodnik: rozmieszczanie zawartości WPF na formularzach Windows Forms w czasie projektowania](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)  
  
-   [Przewodnik: nadawanie stylu zawartości WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Formanty formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Porady: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Instrukcje: Dodawanie regionu formularza do projektu dodatków w programie Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  