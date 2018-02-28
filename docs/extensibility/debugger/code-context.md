---
title: Kontekst kodu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 97a4c8f8a9a710fab70760d9cb6eabb61de7a26f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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