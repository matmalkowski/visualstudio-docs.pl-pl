---
title: rozwiązania programu Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 07a7917e1c33da2151abaeba7dc4f684ca0d067b
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572949"
---
# <a name="outlook-solutions"></a>rozwiązania programu Outlook
  Program Visual Studio udostępnia szablony projektów, które umożliwia tworzenie dodatków narzędzi VSTO dla programu Microsoft Office Outlook. Dodatków VSTO umożliwia automatyzowanie programu Outlook, rozszerzenie funkcji programu Outlook lub dostosowanie interfejsu użytkownika (UI) programu Outlook. Aby uzyskać więcej informacji na temat dodatków VSTO zobacz [dodatki architektura VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
## <a name="create-an-outlook-vsto-add-in-project"></a>Tworzenie VSTO dodatku projektu programu Outlook  
 Tworzenie projektów programu Outlook przy użyciu **dodatek programu Outlook** szablonu projektu w **nowy projekt** okno dialogowe. Ten szablon zawiera odwołania do wymaganych zestawów i pliki projektu.  
  
 Aby uzyskać więcej informacji na temat tworzenia projektów dodatku VSTO, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Omówienie szablonów programu Office project](../vsto/office-project-templates-overview.md).  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Outlook dodatku VSTO model programowania  
 Podczas tworzenia projektów dodatku VSTO dla programu Outlook, Visual Studio wygeneruje klasy o nazwie `ThisAddIn`, która stanowi podstawę rozwiązania. Ta klasa stanowi punkt wyjścia do pisania kodu, a także przedstawia model obiektów programu Outlook do Twojej dodatku VSTO.  
  
 Aby uzyskać więcej informacji na temat `ThisAddIn` klasy i innych funkcji można używać w dodatku VSTO zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Automatyzowanie programu Outlook za pomocą modelu obiektów programu Outlook  
 Model obiektów programu Outlook udostępnia wiele typów, które służą do automatyzacji programu Outlook. Te typy umożliwiają napisać kod, aby wykonać typowe zadania:  
  
-   Programowe tworzenie i wysyłanie wiadomości e-mail.  
  
-   Wyślij nowe wezwania.  
  
-   Wyszukiwanie elementów w folderach programu Outlook.  
  
 Aby uzyskać więcej informacji, zobacz [model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md).  
  
## <a name="customize-the-user-interface-of-an-outlook-application"></a>Dostosowywanie interfejsu użytkownika aplikacji Outlook  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Dodaj niestandardowe karty do wstążki inspektora programu Outlook.|[Wstążka ― omówienie](../vsto/ribbon-overview.md)|  
|Dodaj niestandardowe grupy do wbudowanej karty inspektora programu Outlook.|[Porady: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)|  
|Dodawanie niestandardowego okienka zadań wyświetlane w inspektora programu Outlook|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md).|  
|Dodawanie regionu formularza, który rozszerza lub zamienia istniejące formularzy programu Outlook.|[Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Aby uzyskać więcej informacji dotyczących dostosowywania interfejsu użytkownika programu Outlook i inne aplikacje Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)|Zawiera omówienie obiektów, które są udostępniane przez model obiektów programu Outlook.|  
|[Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)|W tym artykule wyjaśniono narzędzi dostarczonych przez program Visual Studio, ułatwiające projektowanie, tworzenie i debugowania regionów formularzy.|  
|[Wskazówki: Tworzenie pierwszego VSTO dodatek dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Pokazuje, jak utworzyć dodatku VSTO dla programu Microsoft Office Outlook.|  
|[Outlook 2010 w programowanie Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Części biblioteki MSDN, gdzie można znaleźć artykuły i odwołać dokumentacji informacje o opracowywaniu rozwiązań programu Outlook (nie odnoszą się do rozwoju pakietu Office przy użyciu programu Visual Studio).|  
  
  