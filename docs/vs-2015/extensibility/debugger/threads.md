---
title: Wątki | Dokumentacja firmy Microsoft
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
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8070107a1befab999f2edd47d32e25e84266b86d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679548"
---
# <a name="threads"></a>Wątki
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wątków](https://docs.microsoft.com/visualstudio/extensibility/debugger/threads).  
  
Pod względem architektury debugera **wątku**:  
  
-   Jest podstawową jednostką obliczeń. Wątek sekwencyjnie wykonuje instrukcji w ramach pojedynczego wywołania stosu, przechodzenia z jednego kodu kontekstu do następnego.  
  
-   Można zidentyfikować sam, jak i program go jest uruchomiona i można o nazwie, wstrzymana, a wznowione. Wątek również wyliczyć jego ramek stosu skojarzone oraz w niektórych warunkach mogą zostać przeniesione do innej ramki stosu. Podany kontekst ramkę stosu, wątek może zwrócić skojarzony wątek logiczne ewentualne. Wątek ma właściwości, takie jak liczba Wstrzymaj, mogą być wyświetlane w oknie wątki w IDE.  
  
-   Jest reprezentowany przez [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfejsu, zazwyczaj tworzone przez aparat debugowania (DE) lub maszyny wirtualnej w wyniku wykonywania programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Programy](../../extensibility/debugger/programs.md)   
 [Ramki stosu](../../extensibility/debugger/stack-frames.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)

