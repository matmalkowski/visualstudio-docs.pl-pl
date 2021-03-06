---
title: Program węzły | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 27007773cfe8d8a8b595ee9b1921f35376bf2231
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251065"
---
# <a name="program-nodes"></a>Węzły programu
W architekturze debugera *węzła programu*:  
  
-   Jest uproszczone opis programu.  
  
-   Można zidentyfikować wraz z procesu, który jest uruchomiony w. Można dołączyć węzła programu można odłączyć od oraz opisywania aparatu debugowania (DE), której został utworzony, jeśli istnieje.  
  
-   Jest reprezentowany przez [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu, zwykle tworzony przy DE lub port. Węzły programu są dodawane do portu przez wywołanie metody [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Gdy węzeł programu zostanie dodany do portu, jest dodawany do procesu, zawierające program, który reprezentuje ten węzeł programu.  
  
 Później, po rozpoczęciu sesji debugowania, w zależności od implementacji pakietu debugowania węzły programu są używane do tworzenia odpowiednich programów. Gdy proces jest poddawany kwerendzie jego programów, te programy są wyliczane, jeden dla każdego węzła program.  
  
 Zanim program jest dołączony do, IDE wymaga uproszczone opis programu. Te informacje można uzyskać z poziomu węzła programu. Gdy program jest dołączony do, środowisko IDE Wyświetla szczegółowe informacje, takie jak lista wszystkie wątki uruchomione w programie. Te informacje są uzyskiwane z samego programu.  
  
## <a name="see-also"></a>Zobacz także  
 [Programy](../../extensibility/debugger/programs.md)   
 [Procesy](../../extensibility/debugger/processes.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)