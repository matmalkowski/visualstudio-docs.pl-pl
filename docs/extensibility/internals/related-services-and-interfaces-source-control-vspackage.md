---
title: Powiązane usługi i interfejsy (VSPackage kontroli źródła) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f9e8e90fdda61524a9af107df452bc2b13cd90c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Powiązane usługi i interfejsy (VSPackage kontroli źródła)
Ta sekcja zawiera listę wszystkich powiązanych pakiet VSPackage interfejsów w kontroli źródła [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Kontroli źródła pakiet VSPackage implementuje niektóre z tych interfejsów i używa innych użytkowników do wykonywania zadań kontroli źródła.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfejsy implementowane przez i VSPackages kontroli źródła  
 Następujące interfejsy są opisane w [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], i kontroli źródła pakiet VSPackage implementuje podzbiór je w zależności od jego zestaw żądaną funkcji. Niektóre interfejsy są oznaczone jako wymagany i musi być implementowana przez każdy pakiet VSPackage kontroli źródła.  
  
 Dla tych interfejsów, które pakiet nie implementuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnia domyślną implementację. Należy pamiętać, że domyślna implementacja jest przeznaczony dla przypadku, gdy nie pakiet VSPackage jest zarejestrowany i żaden projekt jest kontrolowany. Kontroli źródła poprawnie zapisany pakiet VSPackage implementuje interfejsy wszystkie potrzebne, a nie w gestii domyślną implementację tych interfejsów.  
  
 Kontroli źródła pakiet VSPackage musi implementować prywatnych usługi, który hermetyzuje niektóre lub wszystkie z poniższych interfejsów.  
  
 Interfejsy są:  
  
-   Wymagane: Odpowiednie jednostki (projektu kontroli źródła pakiet VSPackage, Stub kontroli źródła,) musi implementować interfejs.  
  
-   Zalecane: Jednostki należy zaimplementować ten interfejs; w przeciwnym razie funkcja kontroli źródła może być ograniczony.  
  
-   Opcjonalnie: jednostki można zaimplementować ten interfejs, aby zapewnić bogaty zestaw funkcji.  
  
|Interface|Cel|Implementowany przez|Wdrożenie?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Edytory wywołać tego interfejsu przed zmodyfikowaniem lub zapisywanie pliku. Pakiet VSPackage kontroli źródła można wyewidencjonować pliku lub odrzucać operacji, jeśli wyewidencjonowanie nie powiedzie się.|Pakiet VSPackage do kontroli źródła|Zalecane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Ten interfejs zapewnia funkcje kontroli podstawowego źródła dla projektów, takie jak rejestrowanie i wyrejestrowywanie projektów z kontrolą źródła i zapewniania obsługi symboli kontroli źródła podstawowych.|Pakiet VSPackage do kontroli źródła|Wymagane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Ten interfejs jest uzyskiwany z <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> przy użyciu <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> funkcji, lub po prostu rzutowanie obiekt implementujący `IVsHierarchy` do `IVsSccProject2`. Służy do pobierania plików pod kontrolą źródła w projekcie lub informowania projektu bieżący stan kontroli źródła lub miejsca.|Projekt|Wymagane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|Moduł integracji używa tego interfejsu można ustawić bieżącego aktywnego pakiet VSPackage.|Pakiet VSPackage do kontroli źródła|Wymagane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Ten interfejs jest oparty na modelu subskrypcji. Żadnych pakiet VSPackage można sygnalizować, że chce otrzymywać zdarzeń dokumentów i jest zalecana przez powłokę na zdarzenia, które mają być. Wdrożenie i obsługiwane przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], który z kolei przekazuje zdarzenia implementowania `IVsTrackProjectDocumentsEvents2` do pakiet VSPackage.|Stub kontroli źródła|Wymagane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Ten interfejs oferuje przetwarzanie wsadowe, operacji odczytu/zapisu zsynchronizowane i zaawansowane `OnQueryAddFiles` metody.|Stub kontroli źródła|Wymagane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Eksplorator rozwiązań** i projekty Wywołaj ten interfejs, po dodaniu nowych plików do projektów lub zmieniono jego nazwę lub usuwane z projektów plików i folderów. Pakiet VSPackage kontroli źródła można wyewidencjonować plik projektu lub anulować operację.|Pakiet VSPackage do kontroli źródła|Zalecane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Eksplorator rozwiązań** i projekty wywołać tego interfejsu w odpowiedzi na wywołania metody interfejsu IVstrackProjectDocuments3. Kontroli źródła, pakiet VSPackage można śledzić operacji wsadowych synchronizowane operacje odczytu i zapisu oraz pracować z bardziej zaawansowanych `OnQueryAddFiles` metody.|Pakiet VSPackage do kontroli źródła|Zalecane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Ten interfejs umożliwia obsługę zarządzania rejestracji dla projektów sieci Web.|Pakiet VSPackage do kontroli źródła|Zalecane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Ten interfejs jest używany do pobierania etykietki narzędzi dla projektów plików pod kontrolą źródła.|Pakiet VSPackage do kontroli źródła|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Ten interfejs zapewnia obsługę rozszerzenie przestrzeni nazw.|Pakiet VSPackage do kontroli źródła|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|Pakiet VSPackage używa tego interfejsu do integracji rozszerzenie przestrzeni nazw do **nowy**, **Otwórz**, lub **zapisać** okien dialogowych. W rezultacie projekty mogą być automatycznie dodane do kontroli źródła po utworzeniu lub dodane do kontroli źródła podczas zapisywania działania jest włączona.|Pakiet VSPackage do kontroli źródła|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|Pakiet VSPackage używa tego interfejsu, aby zdefiniować dodatkowe symboli jako symbole kontroli źródła dla węzłów w **Eksploratora rozwiązań**.|Pakiet VSPackage do kontroli źródła|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**Dodaj** okno dialogowe dla projektów sieci Web używa tego interfejsu. Zapewnia metody do przeglądania dla lokalizację kontroli źródła i otwarcie projektu sieci Web uprzednio dodanych w repozytorium kontroli źródła w tej lokalizacji.|Pakiet VSPackage do kontroli źródła|Zalecane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Ten interfejs obsługuje ładowanie asynchroniczne (tła) projektów z kontrolą źródła.|Pakiet VSPackage do kontroli źródła|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Ten interfejs umożliwia projektów obserwowanie asynchroniczne ładowanie inicjowane przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.|Projekt|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Ten interfejs umożliwia IDE w celu kontroli źródła active pakiet VSPackage zapytania. Wartość ustawienia kontroli źródła, które mają znaczenie, nawet wtedy, gdy kontrolka nie active źródła zarejestrowana pakiet VSPackage wysyła zapytanie do środowiska IDE. Ten interfejs jest implementowany i obsługiwane przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|Stub kontroli źródła|Wymagane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Ten interfejs jest używany podczas rejestrowania pakiet VSPackage kontroli źródła.|Stub kontroli źródła|Wymagane|  
|<xref:EnvDTE.SourceControl>|Ten interfejs jest używany w automatyzacji. W efekcie ujawnia on tylko funkcje, które mogą być wykonywane bez wyświetlania elementów interfejsu użytkownika.|Pakiet VSPackage do kontroli źródła|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Ten interfejs jest używany do zapisania ustawień kontroli źródła w pliku rozwiązania (sln). Ustawienia obejmują lokalizację kontroli źródła i flagi stanu kontroli źródła.|Pakiet VSPackage do kontroli źródła|Zalecane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Ten interfejs jest używany do zapisywania ustawień kontroli źródła w pliku rozwiązania opcje (.suo). Może to obejmować ustawienia kontroli źródła specyficzne dla użytkownika, takie jak lokalizacja rejestracji bieżącego użytkownika.|Pakiet VSPackage do kontroli źródła|Zalecane|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Ten interfejs jest używany do monitorowania zdarzeń w celu wykonywania operacji, takich jak sprawdzanie w plikach projektu przed zamknięciem rozwiązania lub wprowadzenie nowych plików z kontroli źródła, podczas otwierania projektu.|Pakiet VSPackage do kontroli źródła|Zalecane|  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)