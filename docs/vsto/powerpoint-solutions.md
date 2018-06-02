---
title: PowerPoint — rozwiązania
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c7436bbb7ce904f8c969652e3f4ff0a794116c9c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692710"
---
# <a name="powerpoint-solutions"></a>PowerPoint — rozwiązania
  Program Visual Studio udostępnia szablony projektów, które umożliwia tworzenie dodatków narzędzi VSTO dla programu Microsoft Office PowerPoint. Dodatków VSTO służy do automatyzacji programu PowerPoint, rozszerzenie funkcji programu PowerPoint lub dostosowanie interfejsu użytkownika (UI) programu PowerPoint.  
  
 Aby uzyskać więcej informacji na temat dodatków VSTO, zobacz [rozpocząć programowanie dodatków VSTO](../vsto/getting-started-programming-vsto-add-ins.md) i [dodatki architektura VSTO](../vsto/architecture-of-vsto-add-ins.md). Jeśli jesteś nowym użytkownikiem programowania w języku Microsoft Office, zobacz [wprowadzenie &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak: utworzyć dodatku dla programu Microsoft PowerPoint?](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>W programie PowerPoint można zautomatyzować za pomocą modelu obiektów programu PowerPoint  
 Model obiektów programu PowerPoint udostępnia wiele typów, które służą do automatyzacji programu PowerPoint. Te typy umożliwiają napisać kod, aby wykonać typowe zadania:  
  
-   Programowo utworzenia i sformatowania prezentacji.  
  
-   Dodawanie lub usuwanie slajdów z prezentacji.  
  
-   Dodawanie lub zmienianie kształtów na slajdzie.  
  
 Aby uzyskać dostęp do modelu obiektów programu PowerPoint z dodatku VSTO, użyj `Application` pole `ThisAddIn` klasy w projekcie. `Application` Pola zwraca <xref:Microsoft.Office.Interop.PowerPoint.Application> obiekt reprezentujący bieżące wystąpienie programu PowerPoint. Aby uzyskać więcej informacji, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
 Po wywołują modelu obiektów programu PowerPoint, należy użyć typów, które zostały opublikowane w podstawowego zestawu międzyoperacyjnego dla programu PowerPoint. Podstawowy zestaw międzyoperacyjny działa jako mostka między kodu zarządzanego w dodatku VSTO i model obiektów COM w programie PowerPoint. Wszystkie typy w programie PowerPoint podstawowy zestaw międzyoperacyjny są zdefiniowane w <xref:Microsoft.Office.Interop.PowerPoint> przestrzeni nazw. Aby uzyskać więcej informacji na temat podstawowe zestawy międzyoperacyjne zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Skorzystaj z dokumentacji modelu obiektów programu PowerPoint  
 Aby uzyskać pełne informacje o modelu obiektów programu PowerPoint mogą odwoływać się do programu PowerPoint odwołania podstawowego zestawu międzyoperacyjnego (PIA) i odwołania do modelu obiektu języka VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Odwołanie do podstawowego zestawu międzyoperacyjnego  
 Dokumentacja odwołania PowerPoint PIA opisano typy w podstawowego zestawu międzyoperacyjnego dla programu PowerPoint. Niniejsza dokumentacja jest dostępna z następującej lokalizacji: [odwołania podstawowego zestawu międzyoperacyjnego PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Aby uzyskać więcej informacji dotyczących projektu PIA PowerPoint, takie jak różnice między klasy i interfejsy PIA i implementowania zdarzeń w PIA, zobacz [Przegląd klasy i interfejsy w podstawowe zestawy międzyoperacyjne pakietu Office ](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### <a name="vba-object-model-reference"></a>Odwołania do modelu obiektu VBA  
 Odwołania do modelu obiektu VBA dokumentów modelu obiektów programu PowerPoint, jak jest narażony na język Visual Basic dla kodu aplikacji (VBA). Aby uzyskać więcej informacji, zobacz [odwołania do modelu obiektu programu PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 Wszystkie obiekty i elementów członkowskich w odwołania do modelu obiektu VBA odpowiadają typy i składniki w podstawowy zestaw międzyoperacyjny PowerPoint (PIA). Na przykład obiekt prezentacji odwołania do modelu obiektu VBA odpowiada <xref:Microsoft.Office.Interop.PowerPoint.Presentation> typu w PIA programu PowerPoint. Odwołania do modelu obiektu VBA zapewnia przykłady kodu dla większości właściwości, metod i zdarzeń, jednak należy translacji kod VBA w niniejszej dokumentacji Visual Basic lub Visual C#, jeśli chcesz używać ich w projekcie dodatku VSTO dla programu PowerPoint, który utworzono przy użyciu Program Visual Studio.  
  
## <a name="customize-the-user-interface-of-powerpoint"></a>Dostosowywanie interfejsu użytkownika programu PowerPoint  
 Interfejs użytkownika programu PowerPoint można zmodyfikować w następujący sposób.  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Tworzenie niestandardowego okienka zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|  
|Dodaj niestandardowe karty do wstążki.|[Wstążka ― omówienie](../vsto/ribbon-overview.md)|  
|Dodawanie niestandardowych grup wbudowanych kartę na Wstążce.|[Porady: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Aby uzyskać więcej informacji dotyczących dostosowywania interfejsu użytkownika programu PowerPoint i inne aplikacje Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wskazówki: Tworzenie pierwszego dodatek VSTO dla programu PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Program dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 w programowanie Office](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  