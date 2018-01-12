---
title: "Rozwiązania InfoPath | Dokumentacja firmy Microsoft"
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
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4e59b91ff6159af8f6e5736621c0443d3d96c8b5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="infopath-solutions"></a>InfoPath — Rozwiązania
  Program Visual Studio udostępnia szablony projektów, które umożliwia tworzenie dodatków narzędzi VSTO dla programu Microsoft Office InfoPath 2013 i InfoPath 2010. InfoPath nie jest dostępna w pakiety Office 2016.  
  
> [!NOTE]  
>  Można tworzyć dodatku VSTO dla programu InfoPath nawet, jeśli po zainstalowaniu pakietu Office 2016. Po prostu zainstaluj InfoPath 2013 lub Office 2013 side-by-side z pakietu Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
 Dodatków narzędzi VSTO dla programu InfoPath są podobne do dodatków narzędzi VSTO dla innych aplikacji Microsoft Office. Tego rodzaju rozwiązań składają się z zestawu, który jest ładowany przez aplikację. Użytkownicy końcowi mają dostęp do funkcji tego zestawu, niezależnie od tego, które tworzą lub formularza szablonu jest otwarty. Aby uzyskać więcej informacji na temat dodatków VSTO, zobacz [pobierania VSTO pracy programowania dodatków](../vsto/getting-started-programming-vsto-add-ins.md) i [architektura VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 nie ma projektów szablonu InfoPath formularza, które zostały podane w poprzednich wersjach programu Visual Studio. Możesz również nie można użyć programu Visual Studio 2015 do otwarcia lub edycji InfoPath projektu szablonu formularza, który został utworzony w poprzedniej wersji programu Visual Studio. Można jednak otworzyć i edytować InfoPath formularza szablonu projektu za pomocą narzędzi Visual Studio Tools dla aplikacji. Aby uzyskać więcej informacji, zobacz [Praca z projektami 2008 VSTO w InfoPath 2010.](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## <a name="automating-infopath-by-using-an-add-in"></a>Automatyzowanie programu InfoPath za pomocą dodatku  
 Aby uzyskać dostęp do modelu obiektów programu InfoPath z dodatku VSTO dla pakietu Office utworzone za pomocą narzędzi programowania pakietu Office w Visual Studio, użyj `Application` pole `ThisAddIn` klasy w projekcie. `Application` Pola zwraca <xref:Microsoft.Office.Interop.InfoPath.Application> obiekt reprezentujący bieżące wystąpienie programu InfoPath. Aby uzyskać więcej informacji, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Podczas wywoływania InfoPath object model z dodatku VSTO używasz typy, które zostały opublikowane w podstawowego zestawu międzyoperacyjnego dla programu InfoPath. Podstawowy zestaw międzyoperacyjny działa jako mostka między kodu zarządzanego w dodatku VSTO i model obiektów COM w InfoPath. Wszystkie typy w podstawowy zestaw międzyoperacyjny InfoPath są zdefiniowane w <xref:Microsoft.Office.Interop.InfoPath> przestrzeni nazw. Aby uzyskać więcej informacji na temat InfoPath podstawowy zestaw międzyoperacyjny zobacz [o Microsoft Office InfoPath podstawowego zestawu międzyoperacyjnego](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Aby uzyskać więcej informacji na temat podstawowe zestawy międzyoperacyjne ogólnie rzecz biorąc, zobacz [rozwój rozwiązań Office ― omówienie &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) i [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="customizing-the-user-interface-of-infopath-by-using-an-add-in"></a>Dostosowywanie interfejsu użytkownika programu InfoPath za pomocą dodatku  
 Podczas tworzenia dodatku VSTO dla programu InfoPath istnieje kilka różnych opcji dostosowania interfejsu użytkownika. W poniższej tabeli wymieniono niektóre z tych opcji.  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Tworzenie niestandardowego okienka zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|  
|Dodaj niestandardowe karty na Wstążce w programie InfoPath.|[Dostosowywanie Wstążki do InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Aby uzyskać więcej informacji dotyczących dostosowywania interfejsu użytkownika programu InfoPath i inne aplikacje Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Zobacz też  
 [O zestawu międzyoperacyjnego pakietu Microsoft Office InfoPath podstawowej](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Rozwój rozwiązań Office ― omówienie &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [InfoPath 2010 w programowanie Office](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  