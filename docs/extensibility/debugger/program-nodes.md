---
title: Program węzłów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50ab93c31a340bf8a2f4e2deb5f202707d7826b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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