---
title: "Rozwiązania programu Outlook | Dokumentacja firmy Microsoft"
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
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e0784662a1c48602dd8f93f5ae97c0a69192c3a5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="outlook-solutions"></a>Rozwiązania programu Outlook
  Program Visual Studio udostępnia szablony projektów, które umożliwia tworzenie dodatków narzędzi VSTO dla programu Microsoft Office Outlook. Dodatków VSTO umożliwia automatyzowanie programu Outlook, rozszerzenie funkcji programu Outlook lub dostosowanie interfejsu użytkownika (UI) programu Outlook. Aby uzyskać więcej informacji na temat dodatków VSTO zobacz [dodatki architektura VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
## <a name="creating-an-outlook-vsto-add-in-project"></a>Tworzenie VSTO dodatku projektu programu Outlook  
 Tworzenie projektów programu Outlook przy użyciu **dodatek programu Outlook** szablonu projektu w **nowy projekt** okno dialogowe. Ten szablon zawiera odwołania do wymaganych zestawów i pliki projektu.  
  
 Aby uzyskać więcej informacji na temat tworzenia projektów dodatku VSTO zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Omówienie szablonów programu Office Project](../vsto/office-project-templates-overview.md).  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO dodatku Model programowania  
 Podczas tworzenia projektów dodatku VSTO dla programu Outlook, Visual Studio wygeneruje klasy o nazwie `ThisAddIn`, która stanowi podstawę rozwiązania. Ta klasa stanowi punkt wyjścia do pisania kodu, a także przedstawia model obiektów programu Outlook do Twojej dodatku VSTO.  
  
 Aby uzyskać więcej informacji na temat `ThisAddIn` klasy i innych funkcji można używać w dodatku VSTO zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automating-outlook-by-using-the-outlook-object-model"></a>Automatyzowanie programu Outlook za pomocą modelu obiektów programu Outlook  
 Model obiektów programu Outlook udostępnia wiele typów, które służą do automatyzacji programu Outlook. Te typy umożliwiają napisać kod, aby wykonać typowe zadania:  
  
-   Programowe tworzenie i wysyłanie wiadomości e-mail.  
  
-   Wyślij nowe wezwania.  
  
-   Wyszukiwanie elementów w folderach programu Outlook.  
  
 Aby uzyskać więcej informacji, zobacz [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md).  
  
## <a name="customizing-the-user-interface-of-an-outlook-application"></a>Dostosowywanie interfejsu użytkownika aplikacji Outlook  
  
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
|[Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Pokazuje, jak utworzyć dodatku VSTO dla programu Microsoft Office Outlook.|  
|[Outlook 2010 w programowanie Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Części biblioteki MSDN, gdzie można znaleźć artykuły i odwołać dokumentacji informacje o opracowywaniu rozwiązań programu Outlook (nie odnoszą się do rozwoju pakietu Office przy użyciu programu Visual Studio).|  
  
  