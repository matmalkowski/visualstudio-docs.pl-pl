---
title: Projekt rozwiązania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8c30cb52c446268f96229e5665d8c5d1dcdb33b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="project-solutions"></a>Rozwiązania projektu
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] zawiera szablony projektów, które umożliwia tworzenie dodatków narzędzi VSTO dla programu Microsoft Office Project. Dodatków VSTO umożliwia automatyzację projektu, Rozszerz funkcje projektu lub dostosować projekt interfejsu użytkownika (UI).  
  
 Aby uzyskać więcej informacji na temat dodatków VSTO, zobacz [pobierania VSTO pracy programowania dodatków](../vsto/getting-started-programming-vsto-add-ins.md) i [architektura VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Jeśli jesteś nowym użytkownikiem programowania w języku Microsoft Office, zobacz [wprowadzenie &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
## <a name="automating-project-by-using-the-project-object-model"></a>Automatyzacja projektu za pomocą modelu obiektów programu Project  
 Model obiektów projektu udostępnia wiele typów, których można zautomatyzować projektu. Te typy umożliwiają napisać kod, aby wykonać typowe zadania, takie jak programowo tworzenie i modyfikowanie zadań w projekcie.  
  
 Aby uzyskać dostęp do modelu obiektowego projektu z dodatku VSTO, użyj `Application` pole `ThisAddIn` klasy w projekcie. `Application` Pole zwraca obiekt Microsoft.Office.Interop.MsProject.Application, reprezentujący bieżące wystąpienie projektu. Aby uzyskać więcej informacji, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Po wywołaniu do modelu obiektowego projektu można użyć typów, oferowane w ramach podstawowego zestawu międzyoperacyjnego dla projektu. Podstawowy zestaw międzyoperacyjny działa jako mostka między kodu zarządzanego w dodatku VSTO i model obiektów COM w projekcie. Wszystkie typy w projekcie podstawowy zestaw międzyoperacyjny jest zdefiniowany w przestrzeni nazw Microsoft.Office.Interop.MSProject. Aby uzyskać więcej informacji na temat podstawowe zestawy międzyoperacyjne zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="using-the-project-object-model-documentation"></a>Korzystając z dokumentacji modelu obiektu projektu  
 Aby uzyskać pełne informacje na temat modelu obiektowego projektu mogą odwoływać się do odwołania do modelu obiektu VBA projektu. Odwołania do modelu obiektu VBA dokumentów modelu obiektowego projektu, jak jest narażony na język Visual Basic dla kodu aplikacji (VBA). Aby uzyskać więcej informacji, zobacz [odwołania do modelu obiektu Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Wszystkie obiekty i elementów członkowskich w odwołania do modelu obiektu VBA odpowiadają typy i składniki w podstawowy zestaw międzyoperacyjny projektu (PIA). Na przykład obiekt kalendarza w odwołania do modelu obiektu VBA odnosi się do typu Microsoft.Office.Interop.MSProject.Calendar w PIA projektu. Odwołania do modelu obiektu VBA zapewnia przykłady kodu dla większości właściwości, metod i zdarzeń, jednak należy translacji kod VBA w niniejszej dokumentacji Visual Basic lub Visual C#, jeśli chcesz używać ich w projekcie dodatku narzędzi VSTO projektu utworzonego za pomocą Program Visual Studio.  
  
> [!NOTE]  
>  W tej chwili nie istnieje żadne dokumentacji dla podstawowego zestawu międzyoperacyjnego projektu.  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Typy infrastruktury w projekcie podstawowego zestawu międzyoperacyjnego  
 Podczas pisania kodu, który używa PIA projektu można zauważyć wiele typów, które nie zostały opisane w odwołaniu VBA. Te dodatkowe typy pomocy, Tłumaczenie obiektów w modelu obiektu oparte na modelu COM projektu do kodu zarządzanego, nie są przeznaczone do użycia bezpośrednio w kodzie.  
  
 Aby uzyskać więcej informacji, zobacz[Przegląd klasy i interfejsy w podstawowe zestawy międzyoperacyjne pakietu Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## <a name="customizing-the-user-interface-of-project"></a>Dostosowywanie interfejsu użytkownika programu Project  
 Projekt interfejsu użytkownika można dostosować w następujący sposób.  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Dodaj niestandardowe karty do wstążki w projekcie|[Wstążka — omówienie](../vsto/ribbon-overview.md)|  
  
 Aby uzyskać więcej informacji dotyczących dostosowywania interfejsu użytkownika projektu i inne aplikacje Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Project 2010 i Project Server 2010 w programowanie Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  