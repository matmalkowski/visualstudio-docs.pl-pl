---
title: Rozwiązania projektu
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
ms.openlocfilehash: c3364c778b8dfc290ef06b7daa5ba063ac31f3db
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692603"
---
# <a name="project-solutions"></a>Rozwiązania projektu
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] zawiera szablony projektów, które umożliwia tworzenie dodatków narzędzi VSTO dla programu Microsoft Office Project. Dodatków VSTO umożliwia automatyzację projektu, Rozszerz funkcje projektu lub dostosować projekt interfejsu użytkownika (UI).  
  
 Aby uzyskać więcej informacji na temat dodatków VSTO, zobacz [rozpocząć programowanie dodatków VSTO](../vsto/getting-started-programming-vsto-add-ins.md) i [dodatki architektura VSTO](../vsto/architecture-of-vsto-add-ins.md). Jeśli jesteś nowym użytkownikiem programowania w języku Microsoft Office, zobacz [wprowadzenie &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
## <a name="automate-project-by-using-the-project-object-model"></a>Zautomatyzować projektu za pomocą modelu obiektów programu project  
 Model obiektów projektu udostępnia wiele typów, których można zautomatyzować projektu. Te typy umożliwiają napisać kod, aby wykonać typowe zadania, takie jak programowo tworzenie i modyfikowanie zadań w projekcie.  
  
 Aby uzyskać dostęp do modelu obiektowego projektu z dodatku VSTO, użyj `Application` pole `ThisAddIn` klasy w projekcie. `Application` Pola zwraca `Microsoft.Office.Interop.MsProject.Application` obiekt reprezentujący bieżące wystąpienie projektu. Aby uzyskać więcej informacji, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
 Po wywołaniu do modelu obiektowego projektu można użyć typów, oferowane w ramach podstawowego zestawu międzyoperacyjnego dla projektu. Podstawowy zestaw międzyoperacyjny działa jako mostka między kodu zarządzanego w dodatku VSTO i model obiektów COM w projekcie. Wszystkie typy w podstawowy zestaw międzyoperacyjny projektu są zdefiniowane w `Microsoft.Office.Interop.MSProject` przestrzeni nazw. Aby uzyskać więcej informacji na temat podstawowe zestawy międzyoperacyjne zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="use-the-project-object-model-documentation"></a>Skorzystaj z dokumentacji modelu obiektu projektu  
 Aby uzyskać pełne informacje na temat modelu obiektowego projektu mogą odwoływać się do odwołania do modelu obiektu VBA projektu. Odwołania do modelu obiektu VBA dokumentów modelu obiektowego projektu, jak jest narażony na język Visual Basic dla kodu aplikacji (VBA). Aby uzyskać więcej informacji, zobacz [odwołania do modelu obiektu Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Wszystkie obiekty i elementów członkowskich w odwołania do modelu obiektu VBA odpowiadają typy i składniki w podstawowy zestaw międzyoperacyjny projektu (PIA). Na przykład obiekt kalendarza w odwołania do modelu obiektu VBA odpowiada `Microsoft.Office.Interop.MSProject.Calendar` typu w PIA projektu. Odwołania do modelu obiektu VBA zapewnia przykłady kodu dla większości właściwości, metod i zdarzeń, jednak należy translacji kod VBA w niniejszej dokumentacji Visual Basic lub Visual C#, jeśli chcesz używać ich w projekcie dodatku narzędzi VSTO projektu utworzonego za pomocą Program Visual Studio.  
  
> [!NOTE]  
>  W tej chwili nie istnieje żadne dokumentacji dla podstawowego zestawu międzyoperacyjnego projektu.  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Typy infrastruktury w projekcie podstawowego zestawu międzyoperacyjnego  
 Podczas pisania kodu, który używa PIA projektu można zauważyć wiele typów, które nie zostały opisane w odwołaniu VBA. Te dodatkowe typy pomocy, Tłumaczenie obiektów w modelu obiektu oparte na modelu COM projektu do kodu zarządzanego, nie są przeznaczone do użycia bezpośrednio w kodzie.  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd klasy i interfejsy w podstawowe zestawy międzyoperacyjne pakietu Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## <a name="customize-the-user-interface-of-project"></a>Dostosowywanie interfejsu użytkownika programu project  
 Projekt interfejsu użytkownika można dostosować w następujący sposób.  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Dodaj niestandardowe karty do wstążki w projekcie|[Wstążka ― omówienie](../vsto/ribbon-overview.md)|  
  
 Aby uzyskać więcej informacji dotyczących dostosowywania interfejsu użytkownika projektu i inne aplikacje Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wskazówki: Tworzenie pierwszego VSTO dodatek dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Program dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Project 2010 i Project Server 2010 w programowanie Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  