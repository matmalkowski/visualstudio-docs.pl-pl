---
title: "Program węzłów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6deae60a8e7863e19ec0624ff6452bf41816070
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="program-nodes"></a>Węzły programu
Pod względem architektury debugera **węzła programu**:  
  
-   Jest to lekkie opis programu.  
  
-   Można zidentyfikować się i proces działa, a można dołączyć zostać odłączony i opisano aparat debugowania (DE), której został utworzony, jeśli istnieje.  
  
-   Jest reprezentowana przez [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu, zwykle tworzony przy DE lub portu. Program węzły są dodawane do portu przez wywołanie metody [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Gdy węzeł program zostanie dodany do portu, jest ona dodawana do procesu zawierający program, który reprezentuje ten węzeł programu.  
  
 Jakiś czas, po uruchomieniu sesji debugowania, w zależności od wdrożenia pakietu debugowania programu węzły są używane do tworzenia odpowiednich programów. Jeśli proces jest poddawany kwerendzie dla swoich programów, programy są wyliczone, po jednej dla każdego węzła program.  
  
 Zanim program jest dołączony do, IDE musi lekkie opis programu. Te informacje można znaleźć w węźle programu. Program dołączone do musi IDE wyświetlić bardziej szczegółowe informacje, takie jak lista wszystkie wątki uruchomione w programie. Te informacje są uzyskiwane z sam program.  
  
## <a name="see-also"></a>Zobacz też  
 [Programy](../../extensibility/debugger/programs.md)   
 [Procesy](../../extensibility/debugger/processes.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)