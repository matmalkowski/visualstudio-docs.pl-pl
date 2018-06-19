---
title: Ramki stosu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: feb2bc9d87486b6f83cf4b19ecec24c8c03edee5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128002"
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