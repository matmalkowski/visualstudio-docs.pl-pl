---
title: Projekt modelu podstawowe składniki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2cfb9db9c354eb4c10ece0f5a8259f3d4a104e28
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133134"
---
# <a name="project-model-core-components"></a>Projekt modelu podstawowe składniki
Rozwiń poniższe tabele w modelu projektu. Tabele przedstawiają krótkie opisy interfejsów i usług, które zostały zidentyfikowane w modelu oraz interfejsów i skojarzone z określonymi obiektami usługi. Ponadto tabele Szczegóły inne interfejsy, które są opcjonalne tworzenie projektu i konserwację w zależności od wymagań danego typu określonego projektu.  
  
 Aby uzyskać więcej informacji, zobacz [przeglądanie Symbol obsługi narzędzia](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Obiekt Package  
  
|Interface|Komentarze|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicjuje pakiet VSPackage w IDE i udostępnia jej usługi do środowiska IDE.|  
  
### <a name="project-factory-object"></a>Obiekt fabryki projektu  
  
|Interface|Komentarze|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Zarządza tworzenia nowych projektów i otworzyć istniejące projekty.|  
  
### <a name="project-objects"></a>Obiekty projektu  
  
|Interfejsy|Komentarze|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Zarządza Dodawanie i usuwanie elementów projektu, otwiera edytory, a także obsługuje mapowanie między krótkiej nazwy każdego dokumentu i `VSITEMID`. Dziedziczy `IVsProject` i `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Zarządza właściwości nawigacji i wyświetlania i dostarcza zdarzenia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Umożliwia polecenie podobne do wykonywania `IOleCommandTarget` dla polecenia takie jak wycinanie i zmiany nazwy, które mają zastosowanie tylko wtedy, gdy fokus jest w Eksploratorze rozwiązań.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Służy jako interfejs docelowy polecenia głównej w hierarchii projektu. Jest standardowym interfejsem do wykonywania zapytań obiektów dla ich stanu lub stanu i uruchamiania poleceń. Dostępne, gdy nie skupia się w oknie projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Współrzędne trwałości stanu projektu. Zazwyczaj stan projektu jest przechowywana jako plik projektu, ale mogą być dostosowywane do systemów pamięci masowej, które nie są oparte na pliku.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Umożliwia projektu, aby zarządzać wszystkimi aspektami trwałości dla elementów projektu, albo jako plików na dysku lub obiektów w innych systemach magazynu. `IVsPeristHierarchyItem2` Używany jest interfejs dla elementów, które nie implementują <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfejsu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Współrzędne interakcji z kontroli kodu źródłowego.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Umożliwia projekty do zarządzania informacjami o konfiguracji.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Zarządza projektu konfiguracji obiekty, takie jak konfiguracje Debug i wersji. Tworzenie, wdrażanie i debugowanie operacje są skoordynowane za pośrednictwem obiektów konfiguracji projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementowana przez hierarchie na kontrolowanie delete (destrukcyjnego) lub Usuń (nieszkodliwe) opcji elementów hierarchii. Wywołanie interfejsu zapytania na `IVsHierarchyDeleteHandler` interfejsu z `IVsHierarchy` interfejsu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Udostępnia opcję wykonania obiekt, który obsługuje `IVsCfgProvider2` interfejsu na inną tożsamość COM niż obiekt projektu, który implementuje `IVsHierarchy` interfejsu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Opcjonalny interfejs zaimplementowana dokonanie extensible projektu przez innych. `IVsProjectStartupServices` Interfejs umożliwia pakiet VSPackage innej firmy można zarejestrować identyfikator GUID, który można utrwalić w pliku projektu, aby za każdym razem, gdy ładowania projektu załadować identyfikator GUID usługi innej firmy do pliku projektu i wywołanie `QueryService` dla tego identyfikatora GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementowany przez hierarchii źródłowej w `UIHierarchy` okna do koordynowania operacji schowka, takich jak wycinania, kopiowania i wklejania. Użyj `AdviseClipboardHelperEvents` interfejsu do rejestrowania zdarzeń do Schowka.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Zawiera informacje o przeciąganego elementu względem źródła danych podczas operacji przeciągania i upuszczania w oknie hierarchii interfejsu użytkownika. Wywoływana z `IVsHierarchy` interfejsu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Zawiera informacje o przeciąganego elementu względem jego miejsca docelowego podczas operacji przeciągania i upuszczania w oknie hierarchii interfejsu użytkownika. Wywoływana z `IVsHierarchy` interfejsu.|  
  
### <a name="configuration-object"></a>Obiekt konfiguracji  
  
|Interfejsy|Komentarze|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Zawiera informacje o konfiguracji.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Umożliwia projekty do zarządzania informacjami o konfiguracji.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Umożliwia projektu działać pod kontrolą debugera.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementowana przez projekty wdrażania, które wykonują operacje wdrażania w innych projektach.|  
  
### <a name="configuration-builder-object"></a>Obiekt konfiguracji konstruktora  
  
|Interfejsy|Komentarze|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Zarządza operacji tworzenia konfiguracji projektu.|  
  
### <a name="additional-project-objects"></a>Dodatkowe obiekty projektu  
  
|Interfejsy|Komentarze|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Wyświetla elementu właściwości w **właściwości** okna.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Wyświetla dane wyjściowe do wdrożenia.|  
  
 W poniższej tabeli przedstawiono krótkie opisy usług określonych w modelu projektu.  
  
### <a name="services"></a>Usługi  
  
|Usługa|Komentarze|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Używane przez pakiety VSPackage, który implementuje typów projektów, aby zarejestrować istnienie ich fabrykę projektów z IDE. Należy wywołać VSPackage `QueryService` dla tej usługi, a następnie zarejestrować jego fabryki projektu podczas `IVsPackage::SetSite` metoda jest wywoływana. Jeśli `SetSite` metoda nie jest wywoływana, projekt nie zostanie uruchomiony.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Zapewnia dostęp do programu IDE wewnętrzne, wbudowanego pojęcia bieżącego rozwiązania, takie jak możliwość wyliczyć projektów, tworzenie nowych projektów, wykonać powiadomienia o zmianach projektu i tak dalej.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Metoda wywoływana przez projektów, które chcesz uczestniczyć w kontroli źródła.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Zachowuje tabelę otwartych dokumentów, aby określić, czy co najmniej jeden z elementów projektu jest już otwarty.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Zawiera interfejsy i metody o nazwie faktycznie otworzyć element projektu za pomocą edytora standardowego lub określonego edytora.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Wymagane, wywoływana przez wszystkie projekty, gdy ich dodać, usunąć lub zmienić ich elementów.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Zarządza zmiany pliku lub katalogu i powiadamia klientów, gdy wybrane pliki zostały zmienione na dysku.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Wymagany do wywołania przez wszystkie projekty i edytory przed dirty elementów lub Zapisz je.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Zarządza kolejność operacji kompilacji i wdrażania dla konfiguracji projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Zapewnia dostęp do usługi niskiego poziomu debugera używane przez większość formantów debugowania.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Umożliwia VSPackages dostęp do informacji na temat bieżący wybór i komunikacji z **właściwości** okna.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Udostępnia podstawowe funkcje związane z interfejsu użytkownika IDE, takie jak możliwość tworzenia i wyliczyć narzędzia windows lub windows dokumentu lub zgłosić błąd dla użytkownika.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Zapewnia dostęp do paska stanu IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Używane do implementowania model automatyzacji. W modelu projektu, nastąpi powrót obiektu właściwości, które umożliwia tworzy wystąpienie tego obiektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Używane do implementowania zdarzenia Schowka w obiekcie projektu w hierarchii. `SVsUIHierWinClipboardHelper` Umożliwia poprawnie dojścia wycinania, kopiowania i wklejania działań.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Nie w kompilacji: Używanie klas projektu HierUtil7 do zaimplementowania typ projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Obsługa narzędzia do przeglądania Symbol](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)