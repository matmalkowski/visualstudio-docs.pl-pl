---
title: Ramki stosu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2b225d84bfae6d182da86b2878a3761f67572be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="stack-frames"></a>Ramki stosu
Pod względem architektury debugera **ramki stosu**:  
  
-   To Abstrakcja stosu, który udostępnia Kontekst wykonywania wątku. Wątek jest zawsze wykonywana w obrębie funkcji. Ramka stosu przechowuje zmiennych lokalnych, funkcji i argumenty do niego. Aby debugować z programem Visual Studio, język i środowisko debugowanego musi obsługiwać ramki stosu.  
  
-   Można zarówno zidentyfikować opisania siebie i może zwrócić skojarzone wątku. Ramka stosu można także wrócić kontekst kodu, która reprezentuje bieżący wskaźnik instrukcji, oraz dokumentację skojarzone i konteksty Obliczanie wyrażenia.  
  
-   Ma właściwości opisują nazwy, typu i wartości zmiennych lokalnych i argumentów, a które znajdują się w różnych oknach debugowania IDE.  
  
-   Jest reprezentowana przez [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfejsu, zazwyczaj tworzone przez aparat debugowania (DE) lub maszyny wirtualnej w wyniku wykonania wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)