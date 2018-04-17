---
title: Plan do rozszerzania debuger | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 46c5a8a995644d6876457836674152eb3b3ccad7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="roadmap-for-extending-the-debugger"></a>Przewodnik po rozszerzanie debugera
Ta dokumentacja zawiera informacje o przewodnik i odwołanie do rozszerzania [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] debugera z [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie dokumentacji zawiera przykłady, kompleksowe odwołanie i kilka scenariuszy reprezentatywny, które przedstawiają typowe sposoby dostosowania debugera.  
  
 Kompilujący i jego dane wyjściowe ustalić, co należy zrobić, aby zaimplementować debugowania w programie. Jeśli Twoje kompilatora:  
  
-   Celem natywnego systemu operacyjnego Windows i zapisuje. Plik PDB można debugować programy z aparatu debugowania kodu natywnego (DE), który jest zintegrowany z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Nie musisz wdrożyć ewaluatora DE lub wyrażenie. Ewaluator wyrażeń są zapisywane na składni języka programowania C++.  
  
-   Tworzy Microsoft output języka pośredniego (MSIL), można debugować programy z aparatu debugowania kodu zarządzanego DE, który jest w pełni zintegrowany [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W związku z tym należy zaimplementować tylko ewaluatora wyrażeń. Ewaluator wyrażeń próbki jest dostarczany. Więcej informacji znajduje się w następujących tematach:  
  
     [Szacowanie wyrażeń](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Ocenianie wyrażeń](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Kontekst oceny wyrażeń](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Ocena wyrażeń w trybie przerwania](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Pisanie ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Obiekty docelowe, a system operacyjny lub inne środowisko wykonawcze zastrzeżonych, należy napisać własny DE. Samouczek, który tworzy prosty DE, przy użyciu ATL COM jest dostępne. Więcej informacji znajduje się w następujących tematach:  
  
     [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Samouczek: Tworzenie aparat debugowania, za pomocą biblioteki ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Przykłady](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)