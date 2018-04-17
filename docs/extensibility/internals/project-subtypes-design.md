---
title: Projekt podtypów projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a931d6509b5a8a90f371986f4ddb8955c64387d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="project-subtypes-design"></a>Podtypów projektu
Projekt podtypów umożliwiają VSPackages rozszerzanie projektów opartych na aparat kompilacji firmy Microsoft (MSBuild). Użycie agregacji umożliwia ponowne użycie zbiorczego podstawowego zarządzane systemu projektu w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jeszcze nadal dostosować zachowanie dla danego scenariusza.  
  
 Poniższe tematy przedstawiają szczegółowo podstawowy projekt i implementację podtypów projektu:  
  
-   Podtyp projektu.  
  
-   Wielopoziomowa agregacji.  
  
-   Obsługa interfejsów.  
  
## <a name="project-subtype-design"></a>Podtyp projektu  
 Inicjowanie podtypu projektu uzyskuje się przez agregowanie głównym <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> obiektów. Ta agregacja umożliwia podtypu projektu do przesłonięcia lub zwiększenia większości funkcji podstawowego projektu. Podtypów projektu uzyskać pierwszy możliwość obsługi przy użyciu właściwości <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, polecenia przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>i przy użyciu zarządzania elementu projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Można rozszerzać podtypów projektu:  
  
-   Obiekty konfiguracji projektu.  
  
-   Obiekty zależne od konfiguracji.  
  
-   Obiekty przeglądania niezależny od konfiguracji.  
  
-   Obiekty automatyzacji projektu.  
  
-   Kolekcje właściwości automatyzacji dla projektu.  
  
 Aby uzyskać więcej informacji na rozszerzalności przez podtypów projektu, zobacz [właściwości i metod przedłużony podtypów projektu](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>Pliki zasad  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Środowisko zawiera przykład rozszerzanie systemu projektu podstawowej z podtypu projektu w swojej implementacji pliki zasad. Plik zasad umożliwia przekształcanie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska zarządzania funkcjami, które obejmują Eksploratora rozwiązań **Dodawanie projektu** okno dialogowe **Dodaj nowy element** okno dialogowe i  **Właściwości** okno dialogowe. Podtyp zasad zastępuje i rozszerza te funkcje przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementacji.  
  
##### <a name="aggregation-mechanism"></a>Mechanizm agregacji  
 Mechanizm agregacji podtypu projektu w środowisku obsługuje wiele poziomów agregacji, dzięki czemu zaawansowane podtyp powinny być implementowane przez dalsze flavoring przeznaczonego projektu. Ponadto obiekty pomocnicze projektu podtypu, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, pozwalają wiele poziomów Tworzenie warstw. Zgodnie z ograniczeniami COM i COM reguły agregacji, podtypów projektu i projekty podstawowego konieczne programowane wspólnie, aby umożliwić podtyp wewnętrzny lub podstawowego projektu prawidłowo uczestniczyć w delegowanie wywołań metod i zarządzanie liczby odwołań . Oznacza to projektu zamiar agregowane musi być zaprogramowane w taki sposób, aby obsługiwać agregacji.  
  
 Na poniższej ilustracji przedstawiono schematyczny reprezentację agregacji podtyp wielopoziomowe projektu.  
  
 ![Grafika przedstawiająca wielopoziomowej projectflavor Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Podtyp wielopoziomowej projektu  
  
 Agregacji podtypu projektu wielopoziomowe składa się z trzech poziomach, podstawowego projektu, który jest agregowana przez podtypu projektu, a następnie połączone przez podtypu projektu zaawansowane. Rysunek koncentruje się na niektórych interfejsów pomocniczych, które są dostarczane jako część [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] architektura podtypu projektu.  
  
##### <a name="deployment-mechanisms"></a>Mechanizmy wdrażania  
 Wśród wielu systemu projektu podstawowe funkcje przez podtypu projektu są mechanizmy wdrożenia. Podtyp projektu wpływ mechanizmów wdrażania zaimplementowanie interfejsy konfiguracji (takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) który są pobierane przez wywołanie metody QueryInterface na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. W przypadku gdy zarówno podtypu projektu i podtypu projektu zaawansowane dodać implementacje innej konfiguracji podstawowej projektu wywołuje `QueryInterface` na podtyp projektu zaawansowane `IUnknown`. Jeśli podtypu projektu wewnętrzny zawiera implementację konfiguracji, która żąda podstawowego projektu, podtypu projektu zaawansowane deleguje do implementacji pochodzącymi podtypem projektu wewnętrzny. Jako mechanizm utrwalić stanu z poziomu agregacji do innego wdrożenia wszystkie poziomy podtypów projektu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> do utrwalenia kompilacji z systemem innym niż związane z danych XML w pliku projektu. Aby uzyskać więcej informacji, zobacz [przechowywanie danych w pliku projektu MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> jest implementowany jako mechanizmu pobierania rozszerzeń automatyzacji z podtypów projektu.  
  
 Poniższa ilustracja koncentruje się na implementacja rozszerzeń automatyzacji obiektu przeglądania konfiguracji projektu w szczególności używane przez projekt podtypów rozszerzenie systemu podstawowego projektu.  
  
 ![Grafika automatyczne rozszerzanie podtypu projektu programu VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Rozszerzenie automatyzacji podtypu projektu.  
  
 Podtypów projektu dalsze mogą rozszerzać system projektu podstawowej przez rozszerzanie modelu obiektu automatyzacji. Te są zdefiniowane jako część obiektu automatyzacji DTE i służą do rozszerzania obiekt Project `ProjectItem` obiektu i `Configuration` obiektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie modelu obiektów programu Base Project](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Wielopoziomowa agregacji  
 Implementacji podtypu projektu, który opakowuje niższe podtypu projektu musi programowane wspólnie umożliwia podtypu projektu wewnętrzny działać prawidłowo. Zawiera listę programowania obowiązki:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Implementacji podtyp projektu, do którego jest zawijany wewnętrzny podtypu musi przekazać <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementacji podtypu projektu wewnętrzny dla obu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metody.  
  
-   <xref:EnvDTE80.IInternalExtenderProvider> Implementacji podtypu projektu otoki musi przekazać z jego podtypu projektu wewnętrzny. W szczególności, wykonanie <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> musi uzyskać ciąg nazwy z podtypu projektu wewnętrznej, a następnie ciągów chce dodać jako rozszerzeń.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Implementacji podtypu projektu otoki musi utworzyć wystąpienia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> obiektu jego wewnętrzny podtypu projektu i przytrzymaj go jako Delegat prywatny, ponieważ tylko obiekt konfiguracji projektu podstawowego projektu bezpośrednio wie, że otoki istnieje obiekt konfiguracji podtypu projektu. Podtyp projektu zewnętrznego można początkowo wybrać interfejsy konfiguracji, które chce obsługiwać bezpośrednio, a następnie przekazać rest do wykonania podtypu projektu wewnętrzny <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Obsługa interfejsów  
 Podstawowy projekt deleguje wywołań obsługujące interfejsy dodane przez podtypu projektu, rozszerzenie różnych aspektów jego wykonania. W tym rozszerzanie obiektów konfiguracji projektu i różnych obiektów w przeglądarce właściwości. Te interfejsy są pobierane przez wywołanie metody `QueryInterface` na `punkOuter` (wskaźnik do `IUnknown`) agregatora podtypu projektu najbardziej zewnętrznego.  
  
|Interface|Podtyp projektu|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Umożliwia skonfigurowanie podtypu projektu:<br /><br /> — Udostępnij implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Kontrolowanie uruchamiania debugera, zezwalając podtypu projektu podać własną implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-Wyłączyć Obliczanie wyrażenia czasu projektowania przy odpowiednio obsługi `DBGLAUNCH_DesignTimeExprEval` wielkość jego wykonywania <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Umożliwia skonfigurowanie podtypu projektu:<br /><br /> -Rozszerzyć <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> projektu, aby dodać lub usunąć właściwości niezależne konfiguracji projektu.<br />-Rozszerzyć obiekt automatyzacji projektu (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) projektu.<br /><br /> Powyżej wartości właściwości są pobierane z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> wyliczenia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Umożliwia podtypu projektu do mapowania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> obiekt na podstawie obiektu przeglądania konfiguracji projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Umożliwia podtypu projektu do mapowania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> lub `VSITEMID` obiektu podany obiekt przeglądania konfiguracji projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Umożliwia podtypu projektu utrwalić dowolne dane XML strukturę do pliku projektu (vbproj lub .csproj). Te dane nie jest widoczny dla programu MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Umożliwia skonfigurowanie podtypu projektu:<br /><br /> -Dodaj nowe właściwości programu MSBuild utrwalenia.<br />— Usuń zbędne właściwości z programu MSBuild.<br />-Zapytanie dla bieżącej wartości właściwości programu MSBuild.<br />-Zmień bieżącą wartość właściwości programu MSBuild.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>