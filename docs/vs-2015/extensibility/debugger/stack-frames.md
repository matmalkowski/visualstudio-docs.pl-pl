---
title: Ramek stosu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1efbc05528dd009098749fbe75316c0261b1b20
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679676"
---
# <a name="stack-frames"></a>Ramki stosu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [ramek stosu](https://docs.microsoft.com/visualstudio/extensibility/debugger/stack-frames).  
  
Pod względem architektury debugera **ramki stosu**:  
  
-   Jest klasą abstrakcyjną stosu, które dostarcza kontekst wykonanie wątku. Wątek jest zawsze wykonywane w ramach funkcji. Ramka stosu zawiera zmienne lokalne, funkcji i argumenty do niego. Aby debugować za pomocą programu Visual Studio, języka lub środowiska debugowania musi obsługiwać ramki stosu.  
  
-   Można zarówno zidentyfikować opisania siebie i może zwrócić skojarzonego wątku. Ramka stosu może również zwracać kontekst kodu, który reprezentuje bieżący wskaźnik instrukcji, jak również skojarzony dokumentacji i konteksty oceny wyrażenia.  
  
-   Ma właściwości, które opisują nazwy, typu i wartości zmiennych lokalnych i argumenty, i które znajdują się w różnych oknach debugowania środowiska IDE.  
  
-   Jest reprezentowany przez [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfejsu, zazwyczaj tworzone przez aparat debugowania (DE) lub maszyny wirtualnej w wyniku wykonywania wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)

