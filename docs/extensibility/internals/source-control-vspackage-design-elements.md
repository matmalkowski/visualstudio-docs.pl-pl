---
title: "Elementy projektu pakiet VSPackage kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 234346aba360d70d3bbc673067d2634a5112d0f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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