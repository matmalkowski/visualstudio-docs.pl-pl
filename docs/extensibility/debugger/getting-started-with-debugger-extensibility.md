---
title: Wprowadzenie do rozszerzalności debugera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1a812575d14ef6595d58cc3ecc5d9f94b8f5635
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231291"
---
# <a name="get-started-with-debugger-extensibility"></a>Wprowadzenie do rozszerzalności debugera
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Zawiera informacje potrzebne do tworzenia i dostosowywania składniki debugera, używane do debugowania programów z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie dodano ulepszenia pochodną użyteczność obszerne testy wykonywane na poprzednim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugery. Możesz użyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania do kroku za pośrednictwem aplikacji wielojęzycznych, lub można zaimplementować na bieżąco edytowanie zmiennych podczas debugowania aplikacji i rozwiązań dla wielu języków.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie jest wykonywany poza procesem z debugowanego i dlatego ta opcja jest mniej pożądana w przestrzeni procesu aplikacji. W związku z tym łatwiej jest zapis składników współdziałających z debugerem bez wywierania wpływu na debugowania programu.  
  
 Aby optymalnie wykorzystać [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], należy zapoznać się z następującymi elementami:  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zintegrowanego środowiska programistycznego (IDE)  
  
-   Język programowania w języku C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Plan rozwoju rozszerzania debugera](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Zawiera opis procesu wdrażania, debugowanie w programie, w zależności od kompilatora i jego dane wyjściowe.  
  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)  
 Zawiera omówienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie składników, które obejmują aparat debugowania (DE), Ewaluator wyrażeń (EE) i obsługi symboli (SH).  
  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 W tym artykule opisano główne pojęcia dotyczące architektury debugowania.  
  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)  
 W tym artykule wyjaśniono, jak aparat debugowania (DE) działa jednocześnie w ramach kodu, dokumentację i konteksty oceny wyrażenia. W tym artykule opisano, dla każdego z trzech kontekstów, lokalizacji, pozycja lub oceny odpowiednie do niego.  
  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera łącza do różnych zadań debugowania, takie jak uruchamianie programu i wyrażeń.