---
title: Programy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd3d1c1e72524c393fdb3adc4477ea9ae374fbfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102275"
---
# <a name="programs"></a>Programy
Pod względem architektury debugera **program**:  
  
-   To kontener dla zestawu wątków i zestaw modułów. Program nie ma żadnych pojedynczego odpowiednio w systemu operacyjnego Windows.  
  
     Program jest rodzajem proces podrzędny. Na przykład podczas debugowania witryny sieci Web, skrypt może być widoczny jako program. Podczas wykonywania skryptu w procesie aparatu skryptów niezależnie od innych skryptów również ma swój własny zestaw wątków. Aparat debugowania (DE) dołączona do programu, a nie proces lub wątek.  
  
-   Można zidentyfikować się i proces działa, a można dołączyć zostać odłączony i opisano DE, w której został utworzony, jeśli istnieje. Program można wykonać, Zatrzymaj, nadal i zakończone.  
  
-   Można wyliczyć wszystkich wątków. Program może też podawać własną strumienia dezasemblacji i może wyliczyć wszystkie konteksty kod pozycji danego dokumentu.  
  
-   Jest reprezentowana przez [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfejsu utworzone przed program jest podłączony lub jako część procesu dołączania, w zależności od implementacji. Gdy port wylicza programy procesu, każdy program jest tworzony zgodnie z odpowiednią [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu przekazany jako argument [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Aparaty debugowania również tworzyć `IDebugProgram2` interfejsy do reprezentowania programy, te programy nie są tworzone zgodnie z węzła programu. `IDebugProgramNode2` Interfejsów utworzone przez URZ są używane do rzeczywistego debugowania utworzone przez port są używane tylko w przypadku wykrywania, które programy są uruchomione w procesie.  
  
## <a name="see-also"></a>Zobacz też  
 [Procesy](../../extensibility/debugger/processes.md)   
 [Węzły programu](../../extensibility/debugger/program-nodes.md)   
 [Moduły](../../extensibility/debugger/modules.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [Położenie dokumentu](../../extensibility/debugger/document-position.md)   
 [Kontekst kodu](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)