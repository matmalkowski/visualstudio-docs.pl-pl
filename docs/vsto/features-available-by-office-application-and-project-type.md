---
title: "Funkcje dostępne w aplikacji pakietu Office i typu projektu | Dokumentacja firmy Microsoft"
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
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
ms.assetid: 3e9aa4d3-affb-4f76-bc67-49fe5f26a6a1
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6a0f2e0b87e791618477ff6e11c9e180793d5495
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="features-available-by-office-application-and-project-type"></a>Funkcje dostępne w aplikacjach pakietu Office i typ projektu
  Visual Studio ma kilka typów szablonów projektu, które obsługują różne scenariusze aplikacji pakietu Microsoft Office, łącznie z następujących typów:  
  
-   Dostosowywanie na poziomie dokumentu.  
  
-   Dodatków VSTO.  
  
 Nie wszystkie aplikacje mogą używać każdego typu projektu. Na przykład projektów na poziomie dokumentu są dostępne tylko dla programu Microsoft Office Word i Microsoft Office Excel. Podobnie niektóre funkcje są dostępne tylko dla niektórych typów projektów lub aplikacji. Na przykład w okienku Akcje jest dostępne wyłącznie w projektach na poziomie dokumentu i wstążki rozszerzenia są dostępne tylko dla niektórych aplikacji. Aby uzyskać więcej informacji na temat typów inny projekt, zobacz [rozwój rozwiązań Office ― omówienie &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Szablony projektów pakietu Office są dostępne tylko w niektórych wersjach systemów [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera na potrzeby programowania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
## <a name="project-types-available-for-different-microsoft-office-applications"></a>Typy projektów dostępne dla aplikacji innego pakietu Microsoft Office  
 W poniższej tabeli przedstawiono aplikacje korzystające z każdego typu projektu.  
  
|Typy projektów|Aplikacja Microsoft Office|  
|-------------------|----------------------------------|  
|Dostosowania na poziomie dokumentów|Excel<br /><br /> Word|  
|Dodatków VSTO|Excel<br /><br /> InfoPath (InfoPath 2013 i InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|  
  
## <a name="features-available-in-different-project-types"></a>Funkcje dostępne w różnych typach projektów  
 Poniższej tabeli, które typy projektów Podaj każdej funkcji.  
  
|Funkcja|Typy projektów, które zapewniają funkcję|Dalsze informacje|  
|-------------|--------------------------------------------|---------------------|  
|W okienku Akcje.|Projektów na poziomie dokumentu.|[Okienko akcji — omówienie](../vsto/actions-pane-overview.md)|  
|Wdrożenie ClickOnce.|VS i projektów na poziomie dokumentu.|[Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)|  
|Niestandardowe okienka zadań.|Dodatek projektów VSTO dla następujących aplikacji:<br /><br /> -Programu Excel<br />-InfoPath (InfoPath 2013 i InfoPath 2010)<br />-Outlook<br />-Programu PowerPoint<br />-Word|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|  
|Niestandardowe elementy XML.|Projektów na poziomie dokumentu.<br /><br /> Projekty poziomu aplikacji dla następujących aplikacji:<br /><br /> -Programu Excel<br />-Programu PowerPoint<br />-Word|[Niestandardowe części XML — omówienie](../vsto/custom-xml-parts-overview.md)|  
|Pamięć podręczna danych.|Projektów na poziomie dokumentu.|[Dane z pamięci podręcznej dostosowywane na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)|  
|Udostępnianie obiektu w dodatku VSTO do innych rozwiązań Microsoft Office.|Dodatek projektów VSTO.|[Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|Następujące formanty hosta:<br /><br /> -Wykresu<br />-ListObject<br />-NamedRange<br />-Formanty zawartości<br />-Zakładki|Projektów na poziomie dokumentu.<br /><br /> Dodatek projektów VSTO dla programu Word i Excel.|[Przegląd obiektów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)|  
|Następujące formanty hosta:<br /><br /> -Xmlmappedrange —<br />-XMLNode<br />-XMLNodes|Projektów na poziomie dokumentu.|[Przegląd obiektów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)|  
|Wdrażanie wielu projektów.|Projektów na poziomie dokumentu.<br /><br /> Dodatek projektów VSTO.|[Wskazówki: Wdrażanie wielu rozwiązań pakietu Office w jednym Instalatorze ClickOnce](http://msdn.microsoft.com/en-us/051223c0-4082-4799-b78b-a4763a9def55)|  
|Regiony formularzy programu Outlook.|Dodatek projektów VSTO dla programu Outlook.|[Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md)|  
|Akcje po wdrożeniu.|Projektów na poziomie dokumentu.<br /><br /> Dodatek projektów VSTO.|[Wskazówki: Kopiowanie dokumentu na komputerze użytkownika końcowego po zakończeniu instalacji ClickOnce](http://msdn.microsoft.com/en-us/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|Dostosowywanie Wstążki.|Projektów na poziomie dokumentu.<br /><br /> Dodatek projektów VSTO dla następujących aplikacji:<br /><br /> -Programu Excel<br />-InfoPath (InfoPath 2013 i InfoPath 2010)<br />-Outlook<br />-Programu PowerPoint<br />— Projekt<br />-Programu Visio<br />-Word|[Wstążka — omówienie](../vsto/ribbon-overview.md)|  
|Projektant Visual dokumentu.|Projektów na poziomie dokumentu.|[Projekty pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie &#40; programowanie Office w Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Rozwój rozwiązań Office ― omówienie &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Buforowane dane w dostosowaniach na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
  
  