---
title: "Tworzenie pakiet VSPackage kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c3d414f1fcf6a7f4cd4155eb04e3696fb39740a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-source-control-vspackage"></a>Tworzenie pakiet VSPackage kontroli źródła
Ta dokumentacja zawiera łącza do Przegląd architektury pakietu kontroli źródła, zintegrowany z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], interfejs API, który jest zdefiniowany przez interfejsy do implementacji i usług, które mają być używane, a próbkę przedstawiono prosty źródła kontrolowanie wdrażania pakietu.  
  
 Z kontroli źródła pakiet VSPackage, można utworzyć ścieżkę ścisła integracja kontroli źródła do integracji z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Umożliwia korzystanie z pakietu do obejścia kontroli źródła domyślnego interfejsu użytkownika obsługiwanych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], odpowiadanie na żądania kontroli źródła z systemu projektów i interakcyjnie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] składniki, takie jak **Eksploratora rozwiązań**. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Upoważnia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] współpracuje z mechanizm umożliwiający Utwórz pakiet VSPackage, którą można zintegrować z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] za pomocą modelu usługi.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 W tym artykule omówiono pakiet kontroli źródła, który jest bardziej zaawansowanych alternatywą do kontroli źródła wtyczek do implementowania funkcji kontroli źródła w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Architektura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Przedstawia diagram i wyjaśniono składniki pakietu kontroli źródła.  
  
 [Funkcje](../../extensibility/internals/source-control-vspackage-features.md)  
 Zawiera opis różnych funkcji pakiet kontroli źródła.  
  
 [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Opisuje strukturę pakiet VSPackage, który głęboką integrację musi zaimplementować pakiet kontroli źródła.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 W tym artykule omówiono sposób tworzenia wtyczka do kontroli źródła dostarczającego funkcja kontroli źródła w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika kontroli źródła (UI).  
  
 [Kontrola źródła](../../extensibility/internals/source-control.md)  
 W tym artykule omówiono opcje implementacji jako funkcja zintegrowanego z kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].