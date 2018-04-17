---
title: Tworzenie rozwiązań programu SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cf4e6f10d76b29c5bf70ce01d99a2103672ae213
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="developing-sharepoint-solutions"></a>Opracowywanie rozwiązań SharePoint
  Kilka szablonów typ projektu programu SharePoint są dostępne w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do tworzenia witryn programu SharePoint i elementy lokacji. Aby uzyskać listę typów projektów dostępne w temacie [projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md). Poniżej przedstawiono opis elementów i właściwości elementu projektu SharePoint.  
  
 Aby informacji na temat programu SharePoint 2013 i dodatki programu SharePoint, zobacz [programu SharePoint 2013](http://msdn.microsoft.com/library/jj162979.aspx) i [dodatki kompilacji programu SharePoint](http://msdn.microsoft.com/library/office/apps/jj163230%28v=office.15%29.aspx).  
  
## <a name="elements-of-a-sharepoint-project"></a>Elementy projektu SharePoint  
 Węzły w projekcie programu SharePoint są określane jako *SharePoint — elementy*. SharePoint — elementy mogą także zawierać jeden lub więcej plików podrzędnych, określany jako *pliki elementu programu SharePoint*, takich jak [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliki konfiguracji, formularze aspx i inne.  
  
 Zamiast tworzenia projektów przy użyciu szablonów projektu, które są już wypełnione z plikami elementu projektu, możesz użyć **pusty projekt** szablon, Utwórz pusty projekt programu SharePoint, a następnie ręcznie Dodaj elementy projektu. SharePoint — projekty również opcjonalnie może zawierać jeden lub więcej plików funkcji (dla aktywacji w programie SharePoint) i plik pakietu, w którym do dystrybucji projektu.  
  
### <a name="special-nodes"></a>Specjalne węzłów  
 Każdy projekt programu SharePoint zawiera dwa węzły, które nie może być zmieniona, usunięty, Wytnij, skopiowany lub przeciągnięte z projektu. Te węzły są następujące:  
  
-   Funkcje  
  
-   Package  
  
 Oba węzły są wyświetlane we wszystkich projektach SharePoint zawsze, nawet jeśli nie funkcji lub pakietów, które są zdefiniowane dla projektu.  
  
#### <a name="features-node"></a>Funkcje węzła  
 **Funkcje** węzeł zawiera jedną lub więcej funkcji projektu programu SharePoint. Funkcja jest kontenerem rozszerzeń dla programu SharePoint. Po wdrożeniu funkcji programu SharePoint server można w definicjach lokacji lub indywidualnie aktywowany przez administratorów programu SharePoint w witrynach programu SharePoint. Aby uzyskać więcej informacji, zobacz [pracy z funkcjami](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
 Po dodaniu elementu, takiego jak typ zawartości lub wystąpienia listy, do projektu SharePoint, jest ona dodawana do funkcji w **funkcje** węzła. Zakres element określa, czy jest ona dodawana do nowej lub istniejącej funkcji. Jeśli nowy element jest tym samym zakresie co istniejących funkcji, następnie jest ona dodawana do tej funkcji. W przeciwnym razie element został dodany do nowej funkcji.  
  
 Aby ręcznie dodać funkcję, należy wykonać **dodać funkcję** polecenia menu skrótów węzła funkcji. Można wyświetlić lub zmienić treść funkcji przy użyciu narzędzia Projektant funkcji. Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
 Gdy funkcja zostanie dodany do projektu SharePoint, pojawi się w **Eksploratora rozwiązań** węzła przy użyciu domyślnego nazwij funkcji*x*.feature, gdzie *x* to unikatowa liczba. Po wdrożeniu funkcji programu SharePoint Server administratorem programu SharePoint można aktywować, udostępniając użytkowników witryny programu SharePoint.  
  
#### <a name="package-node"></a>Węzeł pakietów  
 **Pakietu** węzła zawiera pojedynczy plik, która służy jako mechanizm dystrybucji projektu SharePoint. Ten plik, znany jako *rozwiązania ** pakietu*, jest. Na podstawie pliku CAB z. Rozszerzenie WSP. Pakiet rozwiązania jest możliwe, wielokrotnego użytku plik, który zawiera zestaw funkcji, definicje witryny i zestawy, które są stosowane do witryny programu SharePoint i że można włączyć lub wyłączyć indywidualnie. **Pakietu** węzła zawsze zawiera plik o nazwie Package.wspdef, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliku definicji pakietu. Po wdrożeniu pakietu na serwerze z programem SharePoint administratora programu SharePoint można go zainstalować i aktywować jego funkcje.  
  
 Można wyświetlić lub zmienić zawartość pakietu w Projektancie pakiet, klikając węzeł pakietu lub otwieranie menu skrótów, a następnie wybierając **Otwórz**. Aby uzyskać więcej informacji, zobacz [tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).  
  
## <a name="sharepoint-project-and-project-item-properties"></a>Projekt programu SharePoint i właściwości elementu projektu  
 SharePoint — projekty, podobnie jak inne [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów, Wyświetl właściwości w oknie właściwości i strony właściwości. Właściwości, które są wyświetlane zależą od węzła, który jest zaznaczone.  
  
 Po projektu programu SharePoint, element projektu lub węzeł pliku element projektu jest zaznaczona w **Eksploratora rozwiązań**, w oknie właściwości lub na stronie właściwości są wyświetlane następujące właściwości:  
  
### <a name="project-properties"></a>Właściwości projektu  
  
|Nazwa właściwości|Opis|  
|-------------------|-----------------|  
|Konfiguracja Active wdrożenia|Określa serii czynności wykonywanych podczas wdrażania. Aby uzyskać więcej informacji, zobacz [porady: edytowanie konfiguracji wdrażania SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|  
|Cel wdrożenia zestawu|Określa, gdzie *zestawów aplikacji SharePoint* znajdują się. Wartości lokalizacji prawidłowy zestaw to *GlobalAssemblyCache* (ustawienie domyślne) lub *WebApplication*.<br /><br /> Jeśli *rozwiązania typu piaskownica* właściwość jest ustawiona na **true**, następnie właściwość ta jest wyłączona.|  
|Wycofać automatycznie po debugowaniu|Określa, czy wdrożone rozwiązanie automatycznie wycofuje z programu SharePoint po uruchomieniu aplikacji w trybie debugowania w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Po wybraniu rozwiązania wycofuje podczas IDE wraca do widoku po debugowaniu projektu. Po wyczyszczeniu rozwiązania nie wycofać. Aby uzyskać więcej informacji, zobacz [odwołaniem rozwiązania](http://go.microsoft.com/fwlink/?LinkId=183819).|  
|Edycja konfiguracji|Określa konfigurację wdrożenia do użycia dla projektu. Aby uzyskać więcej informacji, zobacz [porady: edytowanie konfiguracji wdrażania SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) i [wdrażanie, publikowanie i uaktualnianie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|  
|Włączyć debugowanie Silverlight (zamiast debugowanie skryptów)|Po wybraniu debugera Silverlight dołącza do debugowania procesu. Po wyczyszczeniu Script debugger dołącza do debugowania procesu. Aby uzyskać więcej informacji, zobacz [przegląd debugowania Silverlight](http://go.microsoft.com/fwlink/?LinkId=179826).|  
|Zawiera zestaw w pakiecie|Określa, czy zestaw projektu jest dostarczana w czasie kompilacji lub nie.|  
|Po wdrożeniu wiersza polecenia|Określa polecenie do uruchomienia, po wdrożeniu rozwiązania programu SharePoint. Ten wiersz obsługuje wszystkie pliki wsadowe, a także rozpoznawania zmiennych MSBuild. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie poleceń wdrażania SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Przed wdrożeniem wiersza polecenia|Określa polecenia do uruchomienia przed wdrożeniem rozwiązania programu SharePoint. Ten wiersz obsługuje wszystkie pliki wsadowe, a także rozpoznawania zmiennych MSBuild. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie poleceń wdrażania SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Plik projektu|Nazwa pliku zawierającego kompilację, konfigurację i inne informacje o projekcie.|  
|Folder projektu|Lokalizacja pliku projektu w systemie. (Tylko do odczytu).|  
|Rozwiązania piaskownicy|Określa, czy projekt powinien być wdrożony jako *rozwiązania typu piaskownica*, znanej także jako *utworzonych przez użytkownika rozwiązania*. Rozwiązania piaskownicy nie są zawsze godne zaufania. Wartość **true** oznacza, że projekt jest wdrażany jako rozwiązania typu piaskownica wartość **false** oznacza, że projekt jest wdrażany jako rozwiązanie farmy. Aby uzyskać więcej informacji, zobacz [uwagi dotyczące rozwiązania piaskownicy](../sharepoint/sandboxed-solution-considerations.md) i [różnice między rozwiązaniami w trybie piaskownicy oraz rozwiązaniami farmy](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|  
|Adres URL witryny|Określa [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] lokacji docelowej dla tego projektu.|  
|Element startowy|Określa pierwszy element w projekcie do uruchomienia.|  
  
 Po wybraniu pliku elementu programu SharePoint (na przykład przepływu pracy lub funkcji w węźle funkcje) w oknie właściwości są wyświetlane następujące właściwości:  
  
### <a name="project-item-properties"></a>Właściwości elementu projektu  
  
|Nazwa właściwości|Opis|  
|-------------------|-----------------|  
|Rozwiązywanie konfliktów wdrożenia|Określa akcję do wykonania podczas wdrażania elementu projektu, którego właściwości są identyczne z właściwościami elementu znajdującego się już na serwerze. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|  
|Właściwości funkcji|Określa zbiór wartości (przechowywane jako pary klucz/wartość), która jest zawarta w funkcji podczas wdrażania w programie SharePoint. Po wdrożeniu funkcji można uzyskać dostępu do wartości właściwości, w kodzie. Aby uzyskać więcej informacji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Odbiorca funkcji|Zawiera kod wykonywany po wystąpieniu określonego zdarzenia na element projektu zawierającego funkcji. Aby uzyskać więcej informacji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Nazwa folderu|Nazwa folderu elementu projektu SharePoint.|  
|Preferencje danych wyjściowych projektu|Określa zależność, takich jak zestawu, który tego elementu projektu musi być uruchamiane. Aby uzyskać więcej informacji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Wpisy kontroli bezpieczne|Określa formantów, które są bezpieczne dla niezaufanym użytkownikom do edycji. Aby uzyskać więcej informacji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
  
### <a name="project-item-file-properties"></a>Właściwości pliku element projektu  
  
|Nazwa właściwości|Opis|  
|-------------------|-----------------|  
|Akcja kompilacji|Określa, jak plik odnosi się do procesów kompilacji i wdrożenia. Aby uzyskać więcej informacji, zobacz [właściwości pliku](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Kopiuj do katalogu wyjściowego|Określa, czy pliki źródłowego zostaną skopiowane do katalogu wyjściowego. Może to być jedna z następujących wartości:<br /><br /> -   *Nie Kopiuj*<br />-   *Zawsze Kopiuj*<br />-   *Kopiuj, jeśli nowszy*<br /><br /> Aby uzyskać więcej informacji, zobacz [właściwości pliku](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Narzędzie niestandardowe|Określa nazwę narzędzia, jeśli istnieje, które przekształca plik w czasie projektowania i umieszcza wynik przekształcenia w innym pliku. Na przykład zestawu danych (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) plik ma domyślne narzędzie niestandardowe. Aby uzyskać więcej informacji, zobacz [właściwości pliku](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Namespace narzędzie niestandardowe|Przestrzeń nazw, do którego zostanie skopiowana dane wyjściowe narzędzia niestandardowego. Aby uzyskać więcej informacji, zobacz [właściwości pliku](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Lokalizacja wdrożenia|Pełna ścieżka pliku na serwerze programu SharePoint. Ta ścieżka składa się z właściwości podrzędnych główny wdrożenia i ścieżka do wdrożenia.|  
|Ścieżka do wdrożenia|Względna ścieżka pliku do pliku programu SharePoint Server, takich jak Workflow1\\. Pełna ścieżka pliku jest tworzony przez łączenie *Deployment ścieżkę* wartość na koniec *główny wdrożenia* wartość.<br /><br /> Wybranie wartości *RootFile* dla *typu wdrożenia* zmiany właściwości *główny wdrożenia* właściwości {SharePointRoot}\\, co Pełna ścieżka \Workflow1 {SharePointRoot}\\. Aby uzyskać więcej informacji, zobacz [pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|  
|Główny wdrożenia|Ciąg. Folder główny, gdy plik jest wdrożony na serwerze programu SharePoint. Na przykład {SharePointRoot} \Template\Features\\{FeatureName}\\.<br /><br /> Wartość *główny wdrożenia* właściwość jest określana przez *typu wdrożenia* ustawienie.|  
|Typ wdrożenia|Typ wdrożenia pliku, który określa jego *główny wdrożenia* wartość. Może to być jedna z następujących wartości:<br /><br /> NoDeployment: \<żadnej wartości ><br /><br /> ElementManifest: {SharePointRoot} \Template\Features\\{FeatureName}\\<br /><br /> ElementFile: {SharePointRoot} \Template\Features\\{FeatureName}\\<br /><br /> TemplateFile: {SharePointRoot} \Template\\<br /><br /> RootFile: {SharePointRoot}\\<br /><br /> GlobalResource: \Resources {SharePointRoot}\\<br /><br /> ClassResource: {ClassResourcePath}\\<br /><br /> Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|  
|Nazwa pliku|Nazwa pliku lub folderu dla pliku elementu.|  
|Pełna ścieżka|Lokalizacja pliku dla elementu. (Tylko do odczytu).|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md)|W tym artykule opisano projekt SharePoint oraz szablony elementów projektu jest dostępne w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Instrukcje: Dodawanie elementów do projektu SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Opisuje sposób dodawania nowych lub istniejących elementów do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.|  
|[Przewodnik: Tworzenie kolumny witryny, typu zawartości oraz listy dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Prowadzi instrukcje tworzenia klienta pola, typu zawartości, definicji listy i wystąpienia listy.|  
|[Instrukcje: Tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)|Opisuje sposób dodawania obsługiwanego odbiornika dla projektu utworzonych w [wskazówki: Tworzenie kolumny witryny, typu zawartości i listy dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|  
|[Tworzenie rozwiązań przepływu pracy SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)|Opisuje sposób tworzenia projektów przepływu pracy, który zawiera formularze przypisania przepływu pracy i formularze inicjalizacji przepływu pracy.|  
|[Tworzenie stron dla SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Opisuje sposób tworzenia stron, takich jak stron aplikacji, stron w witrynie, stron wzorcowych i układy stron dla programu SharePoint.|  
|[Tworzenie części sieciowych dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Opisuje sposób dodawania kontrolek, które użytkownicy mogą bezpośrednio modyfikować zawartość, wyglądu i zachowania stron w witrynie programu SharePoint za pomocą przeglądarki.|  
|[Tworzenie kontrolek wielokrotnego użytku dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Opisuje sposób tworzenia kontrolki użytkownika, które mogą być używane przez stron aplikacji i składników Web Part, które są uruchamiane w programie SharePoint.|  
|[Integrowanie danych biznesowych z SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Opisuje sposób integrowania danych z usług sieci Web i aplikacji serwera zaplecza do aplikacji programu SharePoint.|  
|[Tworzenie definicji witryny dla SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Opisuje sposób tworzenia definicji witryny: szablonów, które są używane do tworzenia witryny programu SharePoint.|  
|[Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Opisuje sposób importowania elementów, takich jak typy zawartości i moduły z istniejącej witryny SharePoint do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.|  
|[Stosowanie modułów podczas dołączania plików do rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Informacje dotyczące używania modułów do wdrażania plików z Twojej [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu do witryny programu SharePoint.|  
|[Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Opisuje sposób przeglądania lokalnych witryn programu SharePoint za pomocą Eksploratora serwera.|  
|[Zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|W tym artykule opisano sposób użycia właściwości elementu projektu o podanie informacji pakowania i wdrażania dla projektów, takich jak wpisy kontroli bezpieczne, preferencje danych wyjściowych projektu i właściwości funkcji.|  
|[Instrukcje: Dodawanie i usuwanie folderów mapowanych](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Opisuje sposób zmapowane katalogi do dodania do projektu w celu zapewnienia dostępu do zasobów programu SharePoint.|  
|[Uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md)|W tym artykule opisano problemy związane z rozwiązań w trybie piaskownicy.|  
|[Zabezpieczenia dla rozwiązań SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|W tym artykule opisano zagadnienia dotyczące zabezpieczeń związane z opracowywaniem rozwiązań SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Okno dialogowe selektora URL &#40;programowanie SharePoint w Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|W tym artykule opisano okno dialogowe, którego można użyć, aby dodać ścieżkę odwołania do zasobów w projekcie, lub na lokalnym serwerze programu SharePoint.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie &#40;programowanie SharePoint w Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)   
 [Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Rozwiązania pakowania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  