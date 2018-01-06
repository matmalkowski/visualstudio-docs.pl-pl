---
title: Programy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 03b4885e653d879e3aaec1d9a68bc9be144cb676
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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