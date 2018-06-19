---
title: Ułatwienia dostępu w projektach pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 34a1ea090e85168b5fd0bf2e55c22d0a38ff331f
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262321"
---
# <a name="accessibility-in-office-projects"></a>Ułatwienia dostępu w projektach pakietu Office
  Microsoft Visual Studio i Microsoft Office, zawierają wiele funkcji ułatwień dostępu, które umożliwiają tworzenie niestandardowych rozwiązań, które spełniają wymagania standardowe ułatwień dostępu. Firma Microsoft publikuje wytyczne dotyczące ułatwień dostępu w sieci Web. Aby uzyskać więcej informacji, zobacz [dostępności witryny sieci Web](http://go.microsoft.com/fwlink/?LinkID=37113).  

 W większości przypadków projektów pakietu Office w Visual Studio spełnia właściwości standardów lub ujawnia ułatwień dostępu, które można ustawić, aby udostępnić rozwiązań. Istnieją jednak niektóre funkcje, które mają ograniczoną dostępność.  

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  

## <a name="accessibility-at-design-time"></a>Ułatwienia dostępu w czasie projektowania  

### <a name="use-shortcut-keys-in-document-level-projects"></a>Klawisze skrótów w projektach na poziomie dokumentu  
 Gdy dokument programu Microsoft Word pakietu Office lub programu Microsoft Office Excel jest otwarty w programie Visual Studio, tylko jedną aplikację naraz odbiera poleceń klawiszy skrótów. Domyślnie program Visual Studio odbiera wszystkie polecenia klawiszy skrótu, ale możesz wprowadzić Word czy Excel ich odbierania, gdy dokument ma fokus, wybierając **schemat klawiatury dynamiczne** na **ustawienia klawiatury** strony z **opcje** okno dialogowe. Aby uzyskać więcej informacji, zobacz [program Klawiatura Microsoft Office Word, ustawienia klawiatury Microsoft Office, opcje — Okno dialogowe](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) i [program Klawiatura Microsoft Office Excel, ustawienia klawiatury Microsoft Office, opcje — Okno dialogowe](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Wyświetlanie klawiszy skrótów do wstążki w projektach na poziomie dokumentu  
 Gdy dokument programu Word lub skoroszyt programu Excel jest otwarty w programie Visual Studio, nie można nacisnąć **Alt** klawisz, aby wyświetlić skróty klawiaturowe kart i kontrolek na Wstążce. Aby wyświetlić klawisze skrótów, gdy dokument lub skoroszyt jest otwarty w projektancie, wykonaj następujące kroki.  

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Aby wyświetlić klawisze skrótu dla karty Wstążki i formantów w Projektancie  

1.  W programie Visual Studio na **narzędzia** menu, kliknij przycisk **opcje**.  

2.  Rozwiń węzeł **narzędzia Office** , a następnie wybierz węzeł **Microsoft Office Excel klawiatury** lub **Microsoft Office Word klawiatury**odpowiednio.  

3.  Wybierz **schemat klawiatury dynamiczne**.  

     Pojawi się komunikat z informacją o ponowne uruchomienie programu Visual Studio aby zmiany zaczęły obowiązywać.  

4.  Kliknij przycisk **OK**.  

5.  Uruchom ponownie program Visual Studio i ponownie otwórz projekt.  

6.  Otwórz dokument lub skoroszyt projektanta projektu.  

7.  Naciśnij klawisz **F6** do wyświetlenia klawiszy skrótów dla wstążki.  

## <a name="accessibility-at-runtime"></a>Ułatwienia dostępu w czasie wykonywania  

### <a name="windows-forms-controls-on-office-documents"></a>Formanty formularzy systemu Windows w dokumentach pakietu Office  
 Formanty formularzy systemu Windows udostępniają właściwości ułatwień dostępu, aby podać informacje dotyczące sterowania do narzędzi ułatwień dostępu, takich jak czytniki. Możliwość korzystania z tych właściwości ułatwień dostępu, gdy formanty znajdują się w dokumencie programu Word w dostosowaniu poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [zawierają informacje ułatwień dostępu dla formantów w formularzu systemu Windows](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).  

 Istnieją pewne ograniczenia ułatwień dostępu w czasie wykonywania, gdy formanty formularzy systemu Windows znajdują się w skoroszycie programu Excel lub dokumentu programu Word:  

-   Z jednego formantu nie karcie do innego.  

-   Formanty w dokumencie są wyłączone, jeśli zmienisz ustawienie powiększenia dokumentu na inny niż 100%.  

 Aby uzyskać informacje o ograniczeniach formanty formularzy systemu Windows w dokumentach, zobacz [formanty ograniczenia formularzy systemu Windows w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  

### <a name="actions-panes-and-custom-task-panes"></a>Okienka akcji i niestandardowych okienek zadań  
 Gdy okienka Akcje lub niestandardowego okienka zadań ma fokus, możesz uzyskać dostęp do formantów taki sam sposób czy dostęp do formantów w aplikacji formularzy systemu Windows. Aby przenieść kursor między panelu actions i dokumentu, można nacisnąć klawisz **F6**.  

 Aby uzyskać więcej informacji na temat okienka akcji i niestandardowych okienek zadań, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md) i [niestandardowego okienka zadań](../vsto/custom-task-panes.md).  

### <a name="display-modes"></a>Wyświetlanie trybów  
 Visual Studio ma następujące ograniczenia związane z tryby wyświetlania:  

-   Formantów w arkuszu programu Excel lub dokumentu programu Word są wyłączone, gdy zmienisz ustawienie powiększenia dokumentu na inny niż 100%.  

-   **Nowy projekt** okno dialogowe wyświetlane formanty nieprawidłowo, jeśli użytkownik zmieni opcje ułatwień dostępu komputera **Użyj funkcji Duży kontrast**.  

 Program Lupa można użyć, aby wyeliminować te ograniczenia. Lupa jest narzędziem wyświetlania w systemie Windows, która tworzy osobne okno wyświetlający powiększony części ekranu.  

## <a name="see-also"></a>Zobacz także  
 [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Ułatwienia dostępu dla osób niepełnosprawnych](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Funkcje ułatwień dostępu programu Visual Studio](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  
