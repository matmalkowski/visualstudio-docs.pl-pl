---
title: Struktura pakietu VSPackage (VSPackage kontroli źródła) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13b811b504259bf10440419b3cb4029a4c239c5e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142792"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura pakietu VSPackage (VSPackage kontroli źródła)
Zestaw SDK pakietu kontroli źródła zawiera wytyczne dotyczące tworzenia pakiet VSPackage, który umożliwia implementujący kontroli źródła zintegrować swoje funkcje kontroli źródła z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska. Pakiet VSPackage jest składnik modelu COM, który jest zwykle ładowane na żądanie przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) na podstawie usług, które są rozgłaszane przez pakiet w nim wpisów rejestru. Każdy pakiet VSPackage musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Pakiet VSPackage zwykle zużywa usług oferowanych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE i proffers niektóre usługi własnych.  
  
 Pakiet VSPackage deklaruje elementy jego menu i ustanawia domyślny stan elementu za pomocą pliku vsct. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE przedstawia elementów menu w tym stanie do momentu załadowania pakiet VSPackage. Następnie pakiet VSPackage implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda jest wywoływana, aby włączyć lub wyłączyć elementów menu.  
  
## <a name="source-control-package-characteristics"></a>Właściwości pakietu kontroli źródła  
 Pakiet VSPackage jest ściśle zintegrowana z kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Semantyka pakiet VSPackage obejmują:  
  
-   Interfejs do zaimplementowania przez trwa pakiet VSPackage ( `IVsPackage` interfejsu)  
  
-   Wykonanie polecenia interfejsu użytkownika (pliku vsct i stosowania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu)  
  
-   Rejestracja pakiet VSPackage z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Pakiet VSPackage kontroli źródła muszą komunikować się z tych innych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jednostek:  
  
-   Projekty  
  
-   Edytory  
  
-   Rozwiązania  
  
-   Windows  
  
-   Uruchomionej tabeli dokumentów  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Usługi środowiska Visual Studio, które mogą być używane  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Usługa SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP interfejsy zaimplementowane i o nazwie  
 Pakiet kontroli źródła jest pakiet VSPackage i w związku z tym może współdziałać bezpośrednio z innych VSPackages, które są zarejestrowane w usłudze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby zapewnić rozmaitych funkcja kontroli źródła, kontroli źródła pakiet VSPackage można uwzględniać interfejsami projektów lub powłoki.  
  
 Każdy projekt w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> uznawana za projektu w ramach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Jednak ten interfejs nie jest przeznaczone wystarczająca do kontroli źródła. Wdrożenie kontroli projektów, które powinny być w sekcji źródłowej <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Ten interfejs jest używany przez pakiet VSPackage kontroli źródła do badania projekt do jego zawartości i do tego celu symboli i informacje o powiązaniu (informacje potrzebne do nawiązywania połączenia między lokalizacji serwera i lokalizację dysku projektu, który znajduje się w kontroli źródła).  
  
 Implementuje pakiet VSPackage kontroli źródła <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, co z kolei umożliwia projektów, aby zarejestrować się do kontroli źródła i pobrać symboli ich stan.  
  
 Aby uzyskać pełną listę interfejsów, które należy wziąć pod uwagę kontroli źródła pakiet VSPackage, zobacz [powiązanych usług i interfejsów](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)