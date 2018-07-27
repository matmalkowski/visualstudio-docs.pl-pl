---
title: Ramek stosu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 21ef19e1eaf9e98da3e774f1d0038f03c131ec45
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276718"
---
# <a name="stack-frames"></a>Ramki stosu
W architekturze debugera *ramki stosu*:  
  
-   Jest klasą abstrakcyjną stosu, które dostarcza kontekst wykonanie wątku. Wątek jest zawsze wykonywane w ramach funkcji. Ramka stosu zawiera zmienne lokalne, funkcji i argumenty do niego. Aby debugować za pomocą programu Visual Studio, języka lub środowiska debugowania musi obsługiwać ramki stosu.  
  
-   Można zarówno zidentyfikować opisania siebie i może zwrócić skojarzonego wątku. Ramka stosu może również zwracać kontekst kodu, który reprezentuje bieżący wskaźnik instrukcji i skojarzone dokumentacji i konteksty oceny wyrażenia.  
  
-   Ma właściwości, które opisują nazwy, typu i wartości zmiennych lokalnych i argumenty, i które znajdują się w różnych oknach debugowania środowiska IDE.  
  
-   Jest reprezentowany przez [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfejsu, zazwyczaj tworzone przez aparat debugowania (DE) lub maszyny wirtualnej w wyniku wykonywania wątku.  
  
## <a name="see-also"></a>Zobacz także  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)