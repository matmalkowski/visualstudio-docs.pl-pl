---
title: Szablony elementu projektu SharePoint i projektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
ms.assetid: 54a7576f-d3f9-475d-8ed7-b675ad21cb53
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 513b2216a99f37ba3aff1174965470b20921072f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sharepoint-project-and-project-item-templates"></a>Projekt SharePoint oraz szablony elementów projektu
  W poniższych sekcjach opisano dostępne projektu SharePoint i elementu projektu szablonów i sposobu ich używania. 
  
##  <a name="project-and-project-item-templates-overview"></a>Omówienie szablony elementów projektu i projektu  
 Podczas tworzenia nowego projektu programu SharePoint w Visual Studio, projekt SharePoint jest dodane do rozwiązania wraz z wszystkich elementów projektu, wymagany przez ten typ projektu. Na przykład po utworzeniu projektu składnika Web Part Silverlight programu Visual Studio tworzy rozwiązanie, które zawiera element wizualnego składnika Web Part projektu i elementu projektu aplikacji Silverlight oraz wszystkie pliki wymagane przez te elementy projektu. Szablony elementów projektu są używane do dodawania elementów projektu do istniejącego projektu programu SharePoint, takie jak dodanie odbiorcy zdarzeń, kolumny witryny lub na liście.  
  
 Aby dowiedzieć się podstawowe informacje na temat programu SharePoint, zobacz [bloków konstrukcyjnych programu SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404). Użytkownicy wersji Advanced można utworzyć niestandardowy projekt oraz szablony elementów projektu. Aby uzyskać więcej informacji, zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
##  <a name="project-templates"></a>Szablony projektu  
 Poniżej znajduje się lista szablonów projektu programu SharePoint. Aby wyświetlić szablony projektów programu SharePoint w Visual Studio w **nowy projekt** okna dialogowego rozwiń **SharePoint** węźle albo **Visual C#** lub  **Visual Basic**, a następnie wybierz pozycję **2010**.  
  
### <a name="sharepoint-2010-project"></a>Projekt programu SharePoint 2010  
 Zawartość *projektu programu SharePoint 2010* znajdują się w każdym szablonie projektu programu SharePoint. Projekt programu SharePoint 2010 zawiera:  
  
-   Plik projektu.  
  
-   Strona właściwości projektu.  
  
-   A **odwołania** folder z listą wszystkich odwołania do zestawów w projekcie.  
  
-   A **funkcje** folder zawierający plik konfiguracyjny .feature, używany do wdrażania funkcji na serwerze programu SharePoint.  
  
-   A **pakietu** folder zawierający plik Package.package, aby wdrożyć rozwiązania programu SharePoint.  
  
-   Plik key.snk (klucz silnej nazwy), który jest używany do podpisywania zestawu o silnej nazwie, dla zwiększenia bezpieczeństwa.  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>Składnik Silverlight Web Part programu SharePoint 2010  
 *Składnik Web Part Silverlight programu SharePoint 2010* projektów umożliwiają tworzenie składników web Part programu SharePoint, które wyświetlają aplikacji Silverlight. Podczas tworzenia tego projektu, można określić, czy Dodaj nową aplikację Silverlight do niej, czy odwołanie już istniejący. Aby uzyskać więcej informacji, zobacz [tworzenia składników Web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) i [wskazówki: Tworzenie składnika Web Part Silverlight ten wyświetla OData dla programu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="sharepoint-2010-visual-web-part"></a>Składnik Visual Web Part programu SharePoint 2010  
 A *składnika Web Part programu SharePoint 2010 Visual* projekt zawiera plik definicji Elements.xml **składnika Web Part** elementu, a **kontrolki użytkownika** elementu. Wygląd wizualny składnik web part można zaprojektować przez przeciąganie lub kopiowanie formanty z przybornika programu Visual Studio do powierzchni kontrolki użytkownika. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie składnika Web Part programu SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) i [bloków konstrukcyjnych: części sieci Web](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="import-sharepoint-2010-solution-package"></a>Importowanie pakietu rozwiązania programu SharePoint 2010  
 *Importowanie pakietu rozwiązania programu SharePoint 2010* projektów pozwalają zaimportować całości lub części istniejącej witryny SharePoint 2010, wyeksportowane do pliku rozwiązania (wsp) programu SharePoint w Visual Studio. Po importowane do programu Visual Studio, można dostosować jego elementów i wdróż je ponownie. Aby uzyskać więcej informacji, zobacz [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>Importowanie przepływu pracy wielokrotnego użytku programu SharePoint 2010  
 *Importowanie wielokrotnego przepływu pracy programu SharePoint 2010* projektów pozwalają zaimportować przepływu pracy wielokrotnego użytku, deklaratywne utworzonych w programie SharePoint Designer 2010 do programu Visual Studio. Przepływ pracy zostanie wyeksportowana z witryny programu SharePoint jako plik wsp. Po importowane do programu Visual Studio, dostosować go, Dodaj do niej kod, a następnie wdrożyć go w witrynie programu SharePoint. Aby uzyskać więcej informacji, zobacz [wskazówki: Importowanie przepływu pracy wielokrotnego użytku z wersji programu SharePoint Designer do Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
##  <a name="project-item-templates"></a>Szablony elementów projektu  
 Poniżej znajduje się lista szablonów elementów projektu SharePoint. Szablony elementów projektu dodać pliki do rozwiązania programu SharePoint do obsługi funkcji programu SharePoint, takich jak kolumny witryny, listy i typy zawartości. Na przykład dodać kolumnę lokacji do rozwiązania dodaje projekt kolumny witryny, który zawiera plik definicji Elements.xml. Dodawanie wizualny składnik web part dodaje projektu programu visual web part do rozwiązania, zawierający plik Elements.xml, element kontrolki użytkownika i elementu wizualnego składnika web part.  
  
 Aby wyświetlić szablony elementów projektu SharePoint, w **Eksploratora rozwiązań**, otwórz menu skrótów projektu programu SharePoint, a następnie wybierz **Dodaj**, **nowy element**. Rozwiń węzeł **SharePoint** węźle albo **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010**.  
  
### <a name="application-page-farm-solution-only"></a>Strona aplikacji (tylko rozwiązanie farmy)  
 **Strony aplikacji (farmy rozwiązania tylko)** elementu pozwala projektować [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony sieci web dla witryny programu SharePoint. Strony aplikacji mogą służyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md) i [_layouts aplikacji typu strony](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>Model usługi łączności danych biznesowych (tylko rozwiązanie farmy)  
 A **modelu łączności danych biznesowych (farmy rozwiązania tylko)** elementu pozwala na integrowanie danych biznesowych programu SharePoint. Dane biznesowe mogą pochodzić z wewnętrznego serwera aplikacji, takich jak [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel i Service Advertising Protocol (SAP). Modele usługi łączności danych biznesowych mogą służyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie modelu BDC](../sharepoint/how-to-create-a-bdc-model.md), [porady: Korzystanie z pliku zasobu do określenia zlokalizowanych nazw, właściwości i uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), i [What's New: łączności biznesowej Usługi](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### <a name="content-type"></a>Typ zawartości  
 *Typ zawartości* elementy pozwalają tworzyć niestandardowe typy zawartości na podstawie istniejącego typu zawartości (podstawowy) takie jak anonsu, zadania lub dokumentu. Niestandardowy typ zawartości zapewnia te same atrybuty i pola jako podstawowym typem zawartości oraz definiowania kolumn witryny (pól). Na przykład można utworzyć niestandardowy skontaktuj się z typem zawartości opartego na podstawowym typem zawartości kontaktu, wchodzącej w programie SharePoint. Typ zawartości można dostosować, zmieniając istniejące kolumny witryny lub dodając większą liczbę kolumn witryny te już uwzględniony w podstawowym typem zawartości.  
  
> [!NOTE]  
>  Ze względu na ograniczenie programu SharePoint nie można utworzyć farmę rozwiązania typu zawartości, oparty na typie zawartości rozwiązania w trybie piaskownicy.  
  
 Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie kolumny witryny, typu zawartości i listy dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) i [bloków konstrukcyjnych: typ zawartości](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### <a name="empty-element"></a>Pusty Element  
 *Puste elementy* są najczęściej używane do definiowania elementów projektu SharePoint, których brakuje projektu lub szablonu elementu projektu w programie Visual Studio. Po dodaniu pustego elementu do projektu, węzeł o nazwie EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] zawiera pojedynczy plik o nazwie Elements.xml. Użyj [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrukcje, aby zdefiniować odpowiednie elementy w Elements.xml.  
  
### <a name="event-receiver"></a>Odbiorcy zdarzeń  
 *Odbiorcy zdarzeń* obsługi zdarzeń dla elementów w witrynie programu SharePoint, na przykład gdy element zostanie dodany do listy, po usunięciu elementu sieci web lub podczas uruchamiania przepływu pracy. Szablon elementu projektu odbiorcy zdarzeń umożliwia obsługi  
  
-   Lista zdarzeń  
  
-   Element listy zdarzeń  
  
-   Lista zdarzeń wiadomości e-mail  
  
-   Zdarzenia sieci Web  
  
-   Lista zdarzeń przepływu pracy  
  
 Tworzy element projektu odbiorcy zdarzeń **odbiorcy zdarzeń** folderu pliku jednej klasy, który zawiera wszystkie zdarzenia obsługi zdarzeń można określić podczas tworzenia projektu w **dostosowywania programu SharePoint Kreator**. Klasy odbiorcy zdarzeń może obsłużyć zdarzenia występujące w witrynie programu SharePoint, gdy elementy takie jak pliki, pola, elementy, list, załączniki, części sieci web i przepływy pracy są dodawane, zaktualizować, usunięte lub usunięte. Aby uzyskać więcej informacji, zobacz [porady: tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md) i [bloków konstrukcyjnych: Obsługa zdarzeń](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### <a name="list"></a>Lista  
 Lista jest wystąpieniem wielokrotnego użytku podstawowej SharePoint listy definicji, takich jak kalendarz lub listy zadań. Po dodaniu listy do rozwiązania, Projektant listy pozwala na dodawanie kolumn witryn do listy i tworzenie niestandardowej listy kolumn. W tym kolumn witryny z typów zawartości. Można określić *widoku* dla listy, która określa zakres kolumn, które będą wyświetlane na liście. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie kolumny witryny, typu zawartości i listy dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) i [bloków konstrukcyjnych: list i bibliotek dokumentów](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### <a name="module"></a>Moduł  
 *Moduły* (nie należy mylić z [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modułów) zawiera wszystkie pliki, które chcesz wdrożyć na serwerze programu SharePoint, taką jak obrazy lub notatki. Element projektu modułu zawiera **modułu** węzła. Węzeł modułu zawiera dwa szablony elementów projektu: pliku definicji XML, która działa jako manifestu dla modułu, a pliku przykład.txt Plik zastępczy. Aby uzyskać więcej informacji, zobacz [przy użyciu modułów pliki dołączane w rozwiązaniu](../sharepoint/using-modules-to-include-files-in-the-solution.md) i [modułów](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### <a name="sequential-workflow-farm-solution-only"></a>Sekwencyjny przepływ pracy (tylko rozwiązanie farmy)  
 A *sekwencyjnego przepływu pracy* jest serii kroków logiki biznesowej, wykonywane w sekwencji, dopóki nie zostanie zakończona w ostatnim kroku. Sekwencyjny przepływ pracy są używane do zarządzania procesów obejmujących SharePoint — elementy takie jak listy i dokumenty. Możesz utworzyć przepływy pracy (globalne) poziomie witryny lub przepływów pracy (local) poziom listy, a następnie można określić, czy przepływ pracy jest uruchamiany automatycznie lub ręcznie. Tego elementu projektu można użyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [przepływów pracy w programie SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), i [What's New: ulepszenia przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="silverlight-web-part"></a>Składnik Web Part Silverlight  
 *Składnik web part Silverlight* elementy projektu umożliwiają tworzenie składników web Part programu SharePoint, które wyświetlają aplikacji Silverlight. Po dodaniu tego elementu projektu do rozwiązania, można wybrać, czy Dodaj nową aplikację Silverlight, czy odwołanie już istniejący później. Aby uzyskać więcej informacji, zobacz [tworzenia składników Web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) i [wskazówki: Tworzenie składnika Web Part Silverlight ten wyświetla OData dla programu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="site-column"></a>Kolumny witryny  
 A *kolumny witryny*, znanej także jako *pola*, jest jednym z najbardziej podstawowe elementy, które można dodać do projektu programu SharePoint. Kolumny witryny reprezentuje typ danych, takich jak numer telefonu, tekst komentarza lub nazwę miejscowości kontaktu w listy kontaktów. Aby uzyskać więcej informacji, zobacz [Tworzenie kolumn witryn, typów zawartości oraz list dla SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) i [kolumn](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### <a name="site-definition-farm-solution-only"></a>Definicja witryny (tylko rozwiązanie farmy)  
 *Definicji witryny* elementy projektu zawiera folder definicji lokacji, który zawiera następujące pliki:  
  
-   .Aspx stronę domyślną, używane jako domyślnej strony sieci web dla witryny.  
  
-   Plik onet.xml, który definiuje składników lokacji.  
  
-   Webtemp pliku xml, który określa konfiguracje definicji lokacji, które są wyświetlane w **Wybieranie szablonu** sekcji **nową witrynę programu SharePoint** strony.  
  
 Po dodaniu definicji witryny, należy dodać kodu i pliki, aby dodać funkcje. Tego elementu projektu można użyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [Tworzenie definicji witryny dla SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) i [definicje witryny i konfiguracje](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### <a name="state-machine-workflow-farm-solution-only"></a>Przepływ pracy automatu stanów (tylko rozwiązanie farmy)  
 A *przepływ pracy automatu stanów* to zbiór akcji, przejścia i stanów logiki biznesowej. Kroki opisane w przepływ pracy automatu stanów nie są wykonywane w kolejności; Zamiast tego są wyzwalane przez działania i stanów. Podobnie jak sekwencyjnego przepływu pracy stan komputera w przepływach pracy są skojarzone z SharePoint — elementy takie jak listy i dokumenty. Ponownie możesz utworzyć przepływy pracy (globalne) poziomie witryny lub przepływów pracy (local) poziom listy. Możesz też wybrać, czy przepływ pracy jest uruchamiany automatycznie lub ręcznie. Tego elementu projektu można użyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [przepływów pracy w programie SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), i [What's New: ulepszenia przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="user-control-farm-solution-only"></a>Kontrolki użytkownika (tylko rozwiązanie farmy)  
 A *kontrolki użytkownika* jest formantem niestandardowych, wielokrotnego użytku, do której można dodać inne formanty ASP.NET i programu SharePoint. Kontrola użytkownika można dodać do strony aplikacji i składników web Part, które są uruchamiane w programie SharePoint. Tego elementu projektu można użyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [tworzenia kontrolki do ponownego użycia dla części sieciowych lub stron aplikacji](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### <a name="visual-web-part"></a>Wizualny składnik Web Part  
 A *wizualny składnik web part* element projekt zawiera plik definicji Elements.xml **składnika Web Part** elementu, a **kontrolki użytkownika** elementu. Wygląd wizualny składnik web part można zaprojektować przez przeciąganie lub kopiowanie formanty z przybornika programu Visual Studio do powierzchni kontrolki użytkownika. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie składnika Web Part programu SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) i [bloków konstrukcyjnych: części sieci Web](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="web-part"></a>Web Part  
 A *składnik web part* jest formantem po stronie serwera, które działają w obrębie specjalny typ strony o nazwie strony sieci Web. Są one bloków konstrukcyjnych stron, które znajdują się w witrynie programu SharePoint. Element składnika web part zawiera pliki, które umożliwiają zaprojektowanie składnika web part w witrynie programu SharePoint. Aby uzyskać więcej informacji, zobacz [porady: tworzenie SharePoint Web Part](../sharepoint/how-to-create-a-sharepoint-web-part.md) i [bloków konstrukcyjnych: części sieci Web](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Produktów i technologii SharePoint](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
