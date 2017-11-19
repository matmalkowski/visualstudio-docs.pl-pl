---
title: Kontekst kodu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92d6ed317bcf6ceead42db850ee61969409eb136
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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