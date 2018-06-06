---
title: Formularz pomocy technicznej w przepływach pracy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7214a472eff3b9181362932828f3ffee2f4fbe48
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767400"
---
# <a name="form-support-in-workflows"></a>Obsługa formularzy w przepływach pracy
  W przepływie pracy można użyć czterech typów formularzy: skojarzenie, inicjowanie, zadań i modyfikacji. Te typy formularza może być oparta na formularzu ASPX lub formularz programu InfoPath. Poziom obsługi, który [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zapewnia dla danego formularza zależy od wielu czynników, które zostały opisane w poniższych tabelach. Aby uzyskać więcej informacji na temat typów formularza przepływu pracy, zobacz [Przegląd formularzy przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=185228) w witrynie MSDN.  
  
## <a name="xml-refactoring"></a>Refaktoryzacja XML
 Po dodaniu ASPX skojarzenie lub inicjowania formularza [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementu projektu przepływu pracy, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automatycznie refaktoryzuje kod XML w pliku Elements.xml przepływu pracy, aby zachować atrybut, który odwołuje się do formularza skojarzenia lub rozpoczęcia synchronizacji zawsze, gdy jest aktualizowana formularza nazwę lub deployment ścieżkę lub formularza zostanie usunięta. Jednak podczas korzystania z innych typów formularza w przepływie pracy, takich jak formularz zadania lub modyfikacji pliku Elements.xml nie został zrefaktoryzowany.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Obsługa formularzy w nowych przepływów pracy programu Visual Studio
 W poniższej tabeli wymieniono [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pomocy technicznej dla różnych typów ASPX lub InfoPath formularzy w przepływach pracy, które są tworzone w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Typ formularza|Przepływ pracy utworzony w programie Visual Studio z formularzem ASPX|Przepływ pracy utworzony w programie Visual Studio za pomocą formularza programu InfoPath|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Skojarzenie|-Formularz skojarzenia ASPX można dodać do przepływu pracy za pomocą **formularz skojarzenia przepływu pracy** szablon elementu.<br />-Plik Elements.xml przepływu pracy został zrefaktoryzowany po dodaniu, zmieniono jego nazwę lub usunąć formularz lub zmianie jego ścieżka do wdrożenia.<br />— Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Brak szablonu formularza skojarzenia InfoPath w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Brak Brak integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i projektanta programu InfoPath.<br />-Plik Elements.xml przepływu pracy nie został zrefaktoryzowany.|  
|Inicjowanie|-Formularz inicjowania ASPX można dodać do przepływu pracy za pomocą **formularza inicjowania przepływu pracy** szablon elementu.<br />-Plik Elements.xml przepływu pracy został zrefaktoryzowany po dodaniu, zmieniono jego nazwę lub usunąć formularz lub zmianie jego ścieżka do wdrożenia.<br />— Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Brak szablonu formularza skojarzenia InfoPath w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Brak Brak integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i projektanta programu InfoPath.<br />-Plik Elements.xml przepływu pracy nie został zrefaktoryzowany.|  
|Zadanie|— Szablon Brak ASPX zadań formularza jest dostępna w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Należy utworzyć strony aplikacji i Dodaj do niej kod.<br />-Plik Elements.xml przepływu pracy nie został zrefaktoryzowany.<br />— Aby uzyskać więcej informacji, zobacz [formularze zadania przepływu pracy (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-Brak szablonu programu InfoPath zadań formularza w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Brak Brak integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i projektanta programu InfoPath.<br />-Plik Elements.xml przepływu pracy nie został zrefaktoryzowany.|  
|Modyfikowanie|— Szablon Brak ASPX modyfikacji formularza jest dostępna w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby dodać formularz modyfikacji, możesz Tworzenie strony aplikacji i Dodaj do niej kod.<br />-Plik Elements.xml przepływu pracy nie został zrefaktoryzowany. Należy ręcznie zmodyfikować zależnie od potrzeb.<br />— Aby uzyskać więcej informacji, zobacz [formularze modyfikacji przepływu pracy (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-Brak szablonu programu InfoPath modyfikacji formularza w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Brak Brak integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i projektanta programu InfoPath.<br />-Plik Elements.xml przepływu pracy nie został zrefaktoryzowany.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Obsługa formularzy w zaimportowanych przepływach pracy wielokrotnego użytku programu SharePoint
 W poniższej tabeli wymieniono [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pomocy technicznej dla różnych typów ASPX lub InfoPath formularzy w przepływach pracy wielokrotnego użytku programu SharePoint, które są importowane do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Typ formularza|Przepływu pracy wielokrotnego użytku, zawierający formularz ASPX importowane z programu SharePoint Designer|Przepływu pracy wielokrotnego użytku, zawierający formularz programu InfoPath importowane z programu SharePoint Designer|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Skojarzenie|-Formularza odwołuje się do pliku Elements.xml przepływu pracy.<br />-Plik Elements.xml przepływu pracy został zrefaktoryzowany podczas zmiany nazwy lub usunąć formularz lub zmianie jego ścieżka do wdrożenia.|-Formularza jest zaimportowane, ale nie odwołuje się do Elements.xml przepływu pracy.<br />-Plik Elements.xml przepływu pracy nie został zrefaktoryzowany.|  
|Inicjowanie|-Formularza jest wywoływany przez przepływ pracy w pliku Elements.xml przepływu pracy.<br />-Plik Elements.xml przepływu pracy został zrefaktoryzowany podczas zmiany nazwy lub usunąć formularz lub zmianie jego ścieżka do wdrożenia.|-Formularza jest zaimportowane, ale nie odwołuje się do Elements.xml przepływu pracy.<br />-Plik Elements.xml przepływu pracy nie został zrefaktoryzowany. **Uwaga:** reguł i właściwości musi być dodawania i modyfikowania dla tego scenariusza.|  
|Zadanie|-Formularza odwołuje się do pliku Elements.xml przepływu pracy.<br />-Plik Elements.xml przepływu pracy nie został zrefaktoryzowany.|-Formularza jest zaimportowane, ale nie odwołuje się do Elements.xml przepływu pracy.<br />-Plik Elements.xml przepływu pracy nie został zrefaktoryzowany. **Uwaga:** reguł i właściwości musi być dodawania i modyfikowania dla tego scenariusza.|  
|Modyfikowanie|Nie dotyczy. Nie można utworzyć ASPX modyfikacji formularzy w programie SharePoint Designer.|Nie dotyczy. InfoPath forms modyfikacji nie można utworzyć w programie SharePoint Designer, z wyjątkiem wbudowanych programu SharePoint Server przepływu pracy, który nie jest zawarty w pliku wsp po wyeksportowaniu przepływ pracy.|  
  
## <a name="see-also"></a>Zobacz także
 [Wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  
