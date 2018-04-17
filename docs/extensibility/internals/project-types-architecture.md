---
title: Architektura typów projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6ef7fe6fbf4a8899606dca35c10745e68e3cbfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="project-types-architecture"></a>Architektura typy projektu
Ta sekcja zawiera szczegółowe informacje o architekturze typów projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)  
 Wyświetla listę usług, z których można korzystać z typu projektu i musi on implementować interfejs.  
  
 [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)  
 Opisuje interfejsy typów projektów musi implementować i opcjonalnie można zaimplementować w celu zapewnienia dodatkowych funkcji.  
  
 [Kiedy należy tworzyć typy projektów](../../extensibility/internals/when-to-create-project-types.md)  
 Ułatwia podjęcie decyzji, kiedy należy utworzyć projekt typu i kiedy może użyć innej [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkcja rozszerzalności, takie jak pakiety VSPackage i edytory, aby osiągnąć tego samego.  
  
 [Hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md)  
 Opisuje sposób [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używa hierarchii i kontekst zaznaczenia, aby zapewnić spójne i uproszczonego użytkowników.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Podtypy projektów](../../extensibility/internals/project-subtypes.md)  
 Wyjaśniono, jak podtypów projektu pozwalają dostosować zachowanie systemów projektu [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera omówienie projektów jako podstawowe bloki konstrukcyjne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE). Zostały podane linki do dodatkowych tematów, które opisano metody kontrolowania projektów, kompilowania i kompilowanie kodu.