---
title: "Wątki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f611284584b091fca390f660b3e840f6cebe048c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="threads"></a>Wątki
Pod względem architektury debugera **wątku**:  
  
-   Jest podstawową jednostkę obliczeń. Wątek sekwencyjnie wykonuje jego instrukcje w kontekście stosu wywołań pojedynczego, przenoszenie z kontekstu jeden kod do następnego.  
  
-   Można zidentyfikować się i program go jest uruchomiona i można je o nazwie, zawieszone i wznawiać. Wątek można także wyliczać jego ramki stosu skojarzone, a w niektórych warunkach, można przenieść do innej ramki stosu. Podany kontekst ramki stosu, wątku może zwrócić logicznego wątku skojarzony, jeśli istnieje. Wątek ma właściwości, takie jak liczba wstrzymania, które mogą być wyświetlane w oknie wątków IDE.  
  
-   Jest reprezentowana przez [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfejsu, zazwyczaj tworzone przez aparat debugowania (DE) lub maszyny wirtualnej w wyniku wykonania programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Programy](../../extensibility/debugger/programs.md)   
 [Ramki stosu](../../extensibility/debugger/stack-frames.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)