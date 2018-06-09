---
title: Tworzenie rozwiązań przepływu pracy programu SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: 68f7bc59a47d6288f54d7bf1a5373b87acf7d993
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238127"
---
# <a name="create-sharepoint-workflow-solutions"></a>Tworzenie rozwiązań przepływu pracy programu SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] udostępnia narzędzia do tworzenia niestandardowych przepływów pracy, które Zarządzanie cyklem życia dokumenty i elementy listy w witrynie sieci Web programu SharePoint. Elementy dostarczone obejmują projektanta, zestaw kontrolek działania i niezbędne odwołania zestawów. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zawiera również **Kreator dostosowania programu SharePoint**, aby utworzyć i skonfigurować przepływy pracy.

 Aby uzyskać listę wymagań wstępnych dotyczących tworzenia projektów programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md). Aby uzyskać więcej informacji na temat programu SharePoint, zobacz [Microsoft produktów i technologii SharePoint](http://go.microsoft.com/fwlink/?LinkId=178470).

## <a name="workflows-in-sharepoint"></a>Przepływy pracy w programie SharePoint
 Podczas dodawania przepływu pracy do listy lub biblioteki programu SharePoint, można wymusić proces biznesowy dla wszystkich elementów w bibliotece lub na liście. Przepływ pracy zawiera opis akcji, które system lub użytkowników, należy wykonać na każdym elemencie, takie jak wysyłanie element, aby edytować, a następnie przejrzeć. Te działania, znane jako *działania*, są blokami konstrukcyjnymi przepływu pracy.

 Można utworzyć przepływów pracy programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i wdrażać je dla witryny sieci Web programu SharePoint. Po wdrożeniu przepływu pracy w programie SharePoint, należy ją skojarzyć z biblioteki lub listy. Może następnie być uruchamiany automatycznie przez proces, lub ręcznie przez użytkownika. Aby uzyskać więcej informacji na temat operacji przepływu pracy, zobacz [tworzenie przepływów pracy programu SharePoint przy użyciu programu Visual Studio](https://docs.microsoft.com/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Tworzenie niestandardowych przepływów pracy programu SharePoint
 Dwa projekty przepływu pracy programu SharePoint są dostępne w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **sekwencyjnego przepływu pracy** i **przepływ pracy automatu stanów**.

 A *sekwencyjnego przepływu pracy* reprezentuje serię kroków. Kroki są wykonywane po kolei, do czasu ukończenia ostatniego działania. Sekwencyjny przepływ pracy są zawsze ściśle sekwencyjnych ich wykonanie. Ponieważ one odbieranie zdarzeń zewnętrznych, a obejmują przepływów parallel logic, może się różnić na kolejność wykonywania. Na poniższej ilustracji przedstawiono przykład sekwencyjnego przepływu pracy.

 ![Sekwencyjny przepływ pracy](../sharepoint/media/sp-sequential.png "sekwencyjnego przepływu pracy")

 A *przepływ pracy automatu stanów* reprezentuje zestaw stanów, przejścia i akcje. Kroki opisane w przepływ pracy automatu stanów wykonywane asynchronicznie. Oznacza to, że nie są zawsze wykonywane po kolei, ale zamiast tego są wyzwalane przez działania i stanów. Jednego stanu jest przypisany jako stan początkowy, a następnie, na podstawie zdarzenia, przejście następuje do innego stanu. Komputer stanu może mieć stanu końcowego, który określa koniec przepływu pracy. Na poniższym diagramie przedstawiono przykład przepływ pracy automatu stanów.

 ![Stan przepływu pracy maszyny](../sharepoint/media/sp-state.png "stanu komputera przepływu pracy")

 Aby uzyskać więcej informacji na temat typów przepływu pracy, zobacz [typów przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=178995).

### <a name="use-the-wizard"></a>Za pomocą Kreatora
 Po utworzeniu projektu przepływu pracy programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], należy najpierw określić jej ustawienia w **Kreator dostosowania programu SharePoint**. Kreator używa tych ustawień, aby utworzyć projekt w **Eksploratora rozwiązań**. Ten projekt zawiera plik kodu, kilka plików, które są używane do wdrażania przepływu pracy, i odwołuje się do zestawów, które są wymagane do utworzenia niestandardowego przepływu pracy programu SharePoint.

 Po utworzeniu przepływu pracy, można zmodyfikować jego właściwości w oknie właściwości. Mimo że większość właściwości przepływu pracy można zmienić bezpośrednio w oknie właściwości, niektóre wymagają kliknij przycisk wielokropka (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")) do modyfikowanie ich wartości. Uruchamia ponownie ten przycisk **Kreator dostosowania programu SharePoint**. Po wprowadzeniu właściwości wartość zmiany, wybierz **Zakończ** przycisk, aby zakończyć je.

> [!NOTE]
>  **Typu przepływu pracy** właściwość jest tylko do odczytu i nie można zmienić. Jeśli chcesz zmienić typ przepływu pracy, należy utworzyć inny przepływ pracy.

## <a name="design-a-sharepoint-workflow"></a>Projektowanie przepływu pracy programu SharePoint
 Po zdefiniowaniu wszystkie kroki procesu biznesowego użyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta przepływów pracy do projektowania przepływu pracy programu SharePoint. Aby otworzyć projektanta, kliknij dwukrotnie Workflow1.cs lub Workflow1.vb w **Eksploratora rozwiązań**, lub Otwórz menu skrótów dla dowolnego z tych plików, a następnie wybierz pozycję **Otwórz**.

### <a name="activities"></a>Kategoria Activities
 Projektowanie przepływu pracy, Dodaj działania z **przybornika** do *harmonogram przepływów pracy* w projektancie. Harmonogram przepływ pracy zawiera sekwencję działań w kolejności, że powinno zostać wykonane.

 Istnieją dwa typy działań:

-   *Proste działania* wykonać pojedynczą jednostkę pracy, takich jak "opóźnienie za 1 dzień" lub "Uruchom usługę sieci Web."

-   *Działań złożonych* zawierać innych działań; na przykład działanie warunkowy może zawierać dwóch gałęziach.

 Oba typy działań są dostępne w **przybornika**.

 Działania może mieć właściwości, metod i zdarzeń. Użyj **właściwości** okna do ustawiania właściwości działania.

 Można również utworzyć niestandardowe działania. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie niestandardowego działania przepływu pracy witryny](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

 Działania są pogrupowane w następującej karcie we **przybornika**:

-   **Przepływ pracy programu SharePoint**

-   **Windows Workflow 3.0**

-   **Windows Workflow 3.5**

 Nie wszystkie działania przepływu pracy core są obsługiwane przez program SharePoint. Aby uzyskać więcej informacji, zobacz [działań dla Windows SharePoint przegląd usług przepływu pracy](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="sharepoint-workflow-activities"></a>Działania przepływu pracy programu SharePoint
 **Przepływu pracy SharePoint** karty zawierają wyspecjalizowanych działań służących do użycia w [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Te działania uprościć i usprawnić tworzenia przepływów pracy cyklu życia dokumentu. Aby uzyskać więcej informacji o działaniach na liście **przepływu pracy SharePoint** karcie, zobacz [działań dla Windows SharePoint przegląd usług przepływu pracy](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="windows-workflow-activities"></a>Działania przepływu pracy systemu Windows
 **Windows Workflow** karty zawierają działania, które są udostępniane przez [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. Te działania służy do tworzenia harmonogramów przepływu pracy dla dowolnego rodzaju aplikacji przepływu pracy systemu Windows.

 Aby uzyskać więcej informacji o działaniach na liście **przepływów pracy programu Windows** karcie, zobacz [działań w systemie Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=156096). Aby uzyskać więcej informacji na temat programu Windows Workflow Foundation, zobacz [Omówienie programu Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=128632).

### <a name="work-with-activities-in-the-designer"></a>Praca z działaniami w Projektancie
 Harmonogram przepływu pracy mogą zawierać kombinację działań przepływu pracy systemu Windows i działań przepływu pracy programu SharePoint.

 Projektant wyświetla wizualnych ułatwiających pozycji i działań jest prawidłowo skonfigurowane. Przeciągnij lub skopiuj działania na harmonogram przepływu pracy, Projektant wyświetla ikony zielony znak plus (+), które Pokaż prawidłowych lokalizacji dla tego działania w przepływie pracy. Nie możesz umieścić działania w lokalizacji, w którym nie jest prawidłowy. Na przykład nie można określić położenia działanie Send jako pierwsze działanie w gałęzi działania nasłuchiwania. Aby uzyskać więcej informacji, zobacz [Centrum deweloperów SharePoint Designer](http://go.microsoft.com/fwlink/?LinkId=178476).

## <a name="collect-information-during-the-workflow"></a>Zbieranie informacji o podczas przepływu pracy
 Można zbierać informacje od użytkowników na wstępnie zdefiniowane razy w przepływie pracy. Można zbierać informacje przy użyciu formularzy i właściwości elementu.

### <a name="forms"></a>Formularze
 Formularze są podobne do okien dialogowych, zawiera pytania, które umożliwiają użytkownikom udzielić odpowiedzi.

 Istnieją cztery typy formularzy, które mogą być używane w przepływie pracy:

-   Skojarzenie

-   Inicjowanie

-   Modyfikowanie

-   Zadanie

 Z powyższych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obejmuje szablony elementów formularzy skojarzenia i inicjowania. Przykład *formularz skojarzenia* jest taki, który umożliwia administratorowi zainstalowanie przepływu pracy wprowadź parametry, które odnoszą się do przepływu pracy, takie jak limit wydatków dla przepływu pracy wydatków. Przykład *formularza inicjowania* to taki, który umożliwia użytkownikowi wydatków przepływu pracy, wprowadź kwotę ich działania w przepływie pracy. Aby uzyskać więcej informacji o tych typach formularzy, zobacz [projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Właściwości elementu.
 Może również zbierać informacje od użytkowników przy użyciu właściwości elementu w bibliotece programu SharePoint lub na liście. Plik kodu głównego (Workflow1.cs lub Workflow1.vb) deklaruje wystąpienia klasy Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties o nazwie `workflowProperties`. Użyj `workflowProperties` obiekt, aby uzyskać dostęp do właściwości biblioteki lub listy w kodzie. Na przykład zobacz [wskazówki: tworzenie i debugowanie rozwiązania przepływu pracy SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Debugowanie szablonu przepływu pracy programu SharePoint
 Można debugować projektu przepływu pracy SharePoint takie same jak debugować innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty oparte na sieci Web. Po rozpoczęciu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugera, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] korzysta z ustawień określonych w **Kreator dostosowania programu SharePoint** Otwórz odpowiednią witrynę sieci Web programu SharePoint i automatyczne kojarzenie szablonu przepływu pracy z odpowiednią bibliotekę lub listę. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza również [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debuger [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] proces o nazwie *w3wp.exe*.

 Aby przetestować przepływ pracy, należy go ręcznie uruchomić. Aby uzyskać więcej informacji, zobacz sekcję "Debugowanie przepływach pracy" w [debugowanie rozwiązań SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Aby uzyskać więcej informacji na temat [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugowaniem aplikacji sieci Web, zobacz [debugowanie aplikacji sieci Web i skryptu](../debugger/debugging-web-applications-and-script.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Wdrażanie szablonu przepływu pracy programu SharePoint
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Wdrażanie projektów przepływu pracy programu SharePoint podobnie jak inne [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint — projekty. Aby uzyskać więcej informacji, zobacz [pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importuj globalnie wielokrotnych przepływów danych
 Oprócz tworzenia wielokrotnych przepływów danych specyficzne dla lokacji, programu SharePoint Designer umożliwia tworzenie *globalnie wielokrotnych przepływów danych*, które są przepływy pracy, które mogą być używane przez wszystkie witryny programu SharePoint. Projekt importowania przepływu pracy wielokrotnego użytku w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aktualnie nie importuje globalny wielokrotnych przepływów danych. Jednak można albo użyj programu SharePoint Designer do konwertowania do wielokrotnego użytku globalnego przepływu pracy do przepływu pracy wielokrotnego użytku, lub importowanie przepływu pracy jako nieprzekonwertowane deklaracyjnego przepływu pracy. Aby uzyskać więcej informacji, zobacz [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: Tworzenie i debugowanie rozwiązania przepływu pracy SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Zawiera instrukcje dotyczące tworzenia i debugowania prostą [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przepływu pracy.|
|[Przewodnik: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Instrukcje prowadzi do tworzenia zaawansowanych funkcji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ukończenia przepływu pracy z formularzami skojarzenia i inicjowania.|
|[Przewodnik: Dodawanie strony aplikacji do przepływu pracy](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Opiera się na temat [wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) przez dodanie dodatkowych *.aspx* strony aplikacji, która raportuje na dane wprowadzane w przepływie pracy.|
|[Przewodnik: Tworzenie niestandardowego działania przepływu pracy witryny](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Pokazuje, jak wykonać dwa kluczowe zadania: Utwórz przepływu pracy z poziomu witryny, a działania niestandardowego przepływu pracy.|
|[Przewodnik: Importowanie przepływu danych wielokrotnego użytku programu SharePoint Designer do Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Demonstracja importowania wielokrotnych przepływów deklaratywne utworzone w programie SharePoint Designer 2010 do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.|

## <a name="see-also"></a>Zobacz także

- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Tworzenie stron aplikacji dla SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)