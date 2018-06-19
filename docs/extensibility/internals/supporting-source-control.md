---
title: Obsługa kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ae3590a5d02c2b3f1d4b67f724d0177f671f7d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130690"
---
# <a name="supporting-source-control"></a>Obsługa kontroli źródła
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje wyewidencjonowania pliku, zaewidencjonowania i innych operacji kontroli źródła dla projektu lub edytora. Jako klient kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] służy do interakcji z pakietem kontroli źródła, takich jak [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], które obejmują archiwizacji, przechowywanie wersji i urządzeń do sterowania dynamicznie zdefiniowanego zestawu plików.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Model pakietów kontroli kodu źródłowego](../../extensibility/internals/model-for-source-control-packages.md)  
 Opisuje typ projektu musi implementować interfejsy do obsługi kontroli źródła.  
  
 [Decyzje dotyczące projektu](../../extensibility/internals/source-control-design-decisions.md)  
 Udostępnia pytania, na których odpowiedzi zmiany sposobu implementacji typu projektu.  
  
 [Szczegóły konfiguracji](../../extensibility/internals/source-control-configuration-details.md)  
 Opisuje sposób obsługi kontroli źródła zmiany implementacji typu projektu.  
  
 [Dodatkowe zalecenia dla projektów i edytory](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 W tym artykule omówiono najlepsze rozwiązania dotyczące typów projektów i edytory.  
  
 [Szczegóły czasu wykonywania](../../extensibility/internals/source-control-runtime-details.md)  
 Opisuje sposób rejestrowania projektu, gdy użytkownik dodaje go do systemu kontroli źródła.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Wskazuje, że w środowisku lub plik ma zostać zmienione w pamięci lub zapisany pakiet kontroli źródła.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Umożliwia projektów i hierarchie rejestrują się z kontroli źródła i uzyskanie informacji na temat stan kontroli źródła.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Wdrożone w systemie projektu w celu zapewnienia kontroli źródła dla plików projektów i elementów projektu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Używany przez projekty do badania środowiska pod kątem uprawnienia do dodawania, usuwania lub zmień nazwę pliku lub katalogu w rozwiązaniu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Powiadamia klientów o zmianach wprowadzonych do projektu plików lub katalogów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera omówienie projektów jako podstawowe bloki konstrukcyjne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE). Zostały podane linki do dodatkowych tematów, które opisano metody kontrolowania projektów, kompilowania i kompilowanie kodu.