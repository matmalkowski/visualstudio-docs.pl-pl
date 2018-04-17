---
title: Rozwiązania programu Visio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5cf82776989d21be60c38aff280d7f9613327c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="visio-solutions"></a>Rozwiązania programu Visio
  Program Visual Studio udostępnia szablony projektów, które umożliwia tworzenie dodatków narzędzi VSTO dla programu Microsoft Office Visio. Dodatków VSTO umożliwia automatyzowanie programu Visio, rozszerzania funkcji programu Visio lub dostosowania interfejsu użytkownika (UI) programu Visio.  
  
 Aby uzyskać więcej informacji na temat dodatków VSTO, zobacz [pobierania VSTO pracy programowania dodatków](../vsto/getting-started-programming-vsto-add-ins.md) i [architektura VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Jeśli jesteś nowym użytkownikiem programowania w języku Microsoft Office, zobacz [wprowadzenie &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **Dotyczy:** informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla programu Visio 2010. Aby uzyskać więcej informacji, zobacz [dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
## <a name="automating-visio-by-using-the-visio-object-model"></a>Automatyzowanie programu Visio za pomocą modelu obiektów programu Visio  
 Model obiektów programu Visio udostępnia wiele klas, których można zautomatyzować Visio do tworzenia diagramów schematów organizacyjnych, blokowych, osi czasu projektów, diagramy sieciowe, spacje pakietu office i więcej. Interfejs API umożliwia pisanie kodu w celu wykonywania typowych zadań:  
  
-   Konstrukcja i położenie kształty i tekst w diagramach.  
  
-   Zarządzanie zachowanie kształtu opartych na logice biznesowej i danych wprowadzonych przez użytkownika.  
  
-   Kontrolowanie wizualizacji diagramu, takich jak przesuwać i powiększać.  
  
-   Dostosowywanie interfejsu użytkownika aplikacji.  
  
-   Importowanie danych zewnętrznych do programu Visio, połączyć kształty i graficznej na stronie.  
  
 Możesz wyświetlić procedury krok po kroku i przykłady dotyczące używania modelu obiektów programu Visio do pracy z dokumentami i kształtów w kodu [Praca z dokumentami Visio](../vsto/working-with-visio-documents.md) i [pracy dotyczące kształtów programu Visio](../vsto/working-with-visio-shapes.md).  
  
 Aby uzyskać dostęp do modelu obiektów programu Visio z dodatku VSTO, użyj `Application` pole `ThisAddIn` klasy w projekcie. `Application` Pole zwraca obiekt Microsoft.Office.Interop.Visio.Application, reprezentujący bieżące wystąpienie programu Visio. Aby uzyskać więcej informacji, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Podczas wywoływania w modelu obiektów programu Visio, można użyć typów, oferowane w ramach podstawowego zestawu międzyoperacyjnego (PIA) dla programu Visio. PIA działa jako mostka między kodu zarządzanego w dodatku VSTO i model obiektów COM w programie Visio. Wszystkie typy w programie Visio PIA są zdefiniowane w obszarze nazw Microsoft.Office.Interop.Visio. Aby uzyskać więcej informacji na temat podstawowe zestawy międzyoperacyjne zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="visio-object-model-overview"></a>Model obiektu Visio ― Omówienie  
 Można znaleźć omówienie modelu obiektów programu Visio w [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md), który zawiera łącza do odwołania do modelu obiektu programu Visio i zestawy SDK.  
  
## <a name="customizing-the-user-interface-of-visio"></a>Dostosowywanie interfejsu użytkownika programu Visio  
 Interfejs użytkownika programu Visio ma następujące opcje dostosowywania.  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Dostosowywanie Wstążki.|[Wstążka — omówienie](../vsto/ribbon-overview.md)|  
  
 Informacje dotyczące dostosowywania interfejsu użytkownika programu Visio, zobacz dokumentację odwołania VBA dla [Visio.UIObject](https://msdn.microsoft.com/library/office/ff765763.aspx) klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Visio 2010 w programowanie Office](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  