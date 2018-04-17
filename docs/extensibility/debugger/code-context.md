---
title: Kontekst kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a84596246ae930cdffc0265f2f2e09652661819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="code-context"></a>Kontekst kodu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania, **kontekst kodu**:  
  
-   Udostępnia abstrakcję pozycji w kodzie, ponieważ znana aparat debugowania (DE). Dla większości architektur środowiska wykonawczego dzisiaj, kontekst kodu można traktować jako adresu w strumieniu instrukcji programu. Nietradycyjnych języków, w którym kod nie może być reprezentowany przez instrukcje, kontekst kodu mogą być reprezentowane w inny sposób.  
  
-   Opisuje bieżącą pozycję w strumieniu wykonywania debugowany program.  
  
-   Istnieje tylko, gdy program zostało zatrzymane w punkcie przerwania.  
  
-   Ma kontekst skojarzonego dokumentu.  
  
-   Jest implementowany przez [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontekstu dokumentu](../../extensibility/debugger/document-context.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)