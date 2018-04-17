---
title: Co&#39;s Nowość w kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b46730ab1acac6605af2e1ff1c418dbe8c886406
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-source-control"></a>Co&#39;s Nowość w kontroli źródła
W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] zapewniają rozwiązania kontroli źródła ściśle zintegrowane z zastosowaniem kontroli źródła pakiet VSPackage. Ta sekcja zawiera opis funkcji kontroli źródła VSPackages i omówiono kroki implementacji.  
  
## <a name="the-source-control-vspackage"></a>Pakiet VSPackage kontroli źródła  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje dwa typy systemów kontroli źródła. We wszystkich wersjach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], nadal można zintegrować oparty na interfejsach API dodatku typu Plug-in kontroli źródła wtyczek. Można również utworzyć pakiet VSPackage do kontroli źródła, która zapewnia integrację dokładnego, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ścieżka odpowiednie dla systemów kontroli źródła, które wymagają wysokiego poziomu wiedzy i autonomiczne.  
  
 Pakiet VSPackage można dodać niemal każdego rodzaju funkcje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Kontroli źródła pakiet VSPackage udostępnia funkcję kontroli źródła pełną [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], w interfejsie użytkownika proponowane użytkownikowi do wewnętrznej komunikacji z systemu kontroli źródła.  
  
 Wdrożenie kontroli źródła pakiet VSPackage wymaga strategii "wszystkie lub żadne". Twórca kontroli źródła pakiet VSPackage należy zakupić znaczną ilość nakładu pracy w przypadku implementowania interfejsów kontroli źródła i nowe elementy interfejsu użytkownika (okien dialogowych, menu i pasków narzędzi) dotyczą funkcji kontroli źródła całego, a także interfejsów wymagane pomyślnie integracji z dowolnego pakietu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Poniższe kroki zapewniają ogólne omówienie co jest potrzebne do zaimplementowania pakiet kontroli źródła. Aby uzyskać więcej informacji, zobacz [tworzenie pakiet VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Utwórz pakiet VSPackage, który proffers usługi kontroli źródła prywatnych.  
  
2.  Implementowanie interfejsów w usług związanych z kontroli źródła, które są proffered przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (na przykład <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interfejs).  
  
3.  Zarejestruj pakiet VSPackage do kontroli źródła.  
  
4.  Wdrażanie wszystkich kontroli źródła interfejsu użytkownika, w tym elementów menu, okna dialogowe Paski narzędzi i menu kontekstowe.  
  
5.  Wszystkie zdarzenia związane z kontroli źródła są przekazywane do VSackage do kontroli źródła, gdy jest aktywny, a musi być obsługiwane przez VSPackage.  
  
6.  Pakiet VSPackage do kontroli źródła musi nasłuchiwać zdarzeń, takich jak implementującej <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interfejsu oraz zdarzenia śledzenia dokumentu projektu (TPD) (zaimplementowanego przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfejsu) i podejmowania niezbędnych działań.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Omówienie](../../extensibility/internals/source-control-integration-overview.md)   
 [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)