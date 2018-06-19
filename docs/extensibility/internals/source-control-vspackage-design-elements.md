---
title: Elementy projektu pakiet VSPackage kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb741a7dc7423c27baed2cd79476239f4e41a170
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130230"
---
# <a name="source-control-vspackage-design-elements"></a>Elementy projektu pakiet VSPackage kontroli źródła
Tematy w tej sekcji opisano strukturę pakiet VSPackage musi zaimplementować głębokiej integracji kontroli źródła. Wyświetla listę również interfejsów usług, który źródła formantu pakiet VSPackage można zaimplementować i interfejsów i usług kontroli źródła pakiet VSPackage mogą korzystać z innych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] składników w celu obsługi źródła kontrolować modelu i funkcjonalność.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Struktura pakietu VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Definiuje strukturę pakiet VSPackage kontroli źródła.  
  
 [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Wyświetla listę usług i interfejsów związanych z pakietem kontroli źródła.  
  
 [Usług](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Zawiera opis usługi kontroli źródła, które są udostępniane przez pakiet VSPackage kontroli źródła.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 W tym artykule omówiono sposób tworzenia kontroli źródła pakiet VSPackage, który nie tylko udostępnia funkcje kontroli źródła, ale może być używana do dostosowywania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] źródła formantu interfejsu użytkownika.