---
title: Wprowadzenie do programowania dodatków narzędzi VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7249c3971c8008f70b9e5add79adddde17fe6a82
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="get-started-programming-vsto-add-ins"></a>Wprowadzenie do programowania dodatków narzędzi VSTO
  Dodatków VSTO umożliwia automatyzowanie aplikacji Microsoft Office, Rozszerz funkcje aplikacji i dostosowania interfejsu użytkownika (UI) aplikacji. Aby dowiedzieć się jak Porównaj dodatków narzędzi VSTO z innych rozwiązań pakietu Office można tworzyć przy użyciu programu Visual Studio, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="create-vsto-add-in-projects"></a>Tworzenie projektów dodatku VSTO  
 Tworzenie projektów dodatku VSTO przy użyciu jednej z dodatku VSTO szablonów projektu w **nowy projekt** okno dialogowe. Te szablony zawierają odwołania do wymaganych zestawów i pliki projektu. Program Visual Studio udostępnia dodatku VSTO szablonów projektu dla większości aplikacji pakietu Office.  
  
 Aby uzyskać więcej informacji na temat tworzenia projektów dodatku VSTO, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Omówienie szablonów programu Office project](../vsto/office-project-templates-overview.md).  
  
## <a name="develop-vsto-add-in-projects"></a>Tworzenie projektów dodatku VSTO  
 Podczas tworzenia projektów dodatku VSTO programu Visual Studio automatycznie tworzy *ThisAddIn.vb* (w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) lub *ThisAddIn.cs* (w języku C#) code pliku. Ten plik zawiera `ThisAddIn` klasy, która stanowi podstawę sieci dodatku VSTO. Elementy członkowskie tej klasy można użyć do uruchomienia kodu po dodatku VSTO jest załadowany lub zwalnianie dostępu do modelu obiektu aplikacji hosta i rozszerzania funkcji aplikacji. Aby uzyskać więcej informacji, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-applications-by-using-the-object-models"></a>Automatyzowanie aplikacji przy użyciu modeli obiektów  
 Modele obiektów w aplikacji pakietu Microsoft Office ujawniać wiele typów, które można program względem w dodatku VSTO. Te typy umożliwia automatyczne stosowanie. Na przykład można programowo utworzyć i wysłać wiadomość e-mail w programie Outlook lub możesz otworzyć dokument i Dodaj zawartość w programie Word. Aby uzyskać więcej informacji na temat dostępu do modelu obiektu aplikacji hosta w kodzie, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
 Aby uzyskać więcej informacji na temat modeli obiektów określonych aplikacji pakietu Microsoft Office zobacz następujące tematy:  
  
-   [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)  
  
-   [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md)  
  
-   [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath — rozwiązania](../vsto/infopath-solutions.md)  
  
-   [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md)  
  
-   [Rozwiązania projektu](../vsto/project-solutions.md)  
  
-   [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)  
  
## <a name="customize-the-user-interface-of-applications"></a>Dostosowywanie interfejsu użytkownika aplikacji  
 Istnieją różne sposoby dostosowania interfejsu użytkownika aplikacji hosta przy użyciu dodatku VSTO:  
  
-   Dla programów Excel i Word można dodawać formanty zarządzanego do dokumentów. Aby uzyskać więcej informacji, zobacz [dokumentów rozszerzania programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Jeśli aplikacja obsługuje tę funkcję można dostosować wstążki. Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
-   Jeśli aplikacja obsługuje tę funkcję, można utworzyć niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [niestandardowego okienka zadań](../vsto/custom-task-panes.md).  
  
-   Dla programu Outlook można utworzyć regionu formularza niestandardowego. Aby uzyskać więcej informacji, zobacz [regionów formularzy Outlook utwórz](../vsto/creating-outlook-form-regions.md).  
  
-   Dla wszystkich aplikacji Microsoft Office można wyświetlić w dodatku VSTO z formularzy systemu Windows.  
  
 Aby uzyskać więcej informacji na temat sposobu dostosowywania aplikacji interfejsu użytkownika pakietu Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Aby dowiedzieć się, jak tworzenie dodatków narzędzi VSTO, zobacz następujące wskazówki:  
  
-   [Wskazówki: Tworzenie pierwszego dodatek VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Wskazówki: Tworzenie pierwszego VSTO dodatek dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Wskazówki: Tworzenie pierwszego dodatek VSTO dla programu PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Wskazówki: Tworzenie pierwszego VSTO dodatek dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Wskazówki: Tworzenie pierwszego dodatek VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 Te wskazówki przedstawiono narzędzi programowania pakietu Office w Visual Studio i modelu programowania dla dodatków VSTO.  
  
 Aby uzyskać listę tematów, które umożliwia przeprowadzenie niektórych typowych zadań w projektach pakietu Office, zobacz [typowe zadania w programowaniu pakietu Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Program dodatków VSTO](../vsto/programming-vsto-add-ins.md)  
  
  