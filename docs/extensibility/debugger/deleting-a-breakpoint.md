---
title: Usuwanie punktu przerwania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2789fd46942a9b54ca3d6efb082a6b21511969ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="deleting-a-breakpoint"></a>Usuwanie punktu przerwania
Poniżej opisano proces usuwania oczekującym punktem przerwania:  
  
## <a name="deletion-process"></a>Proces usuwania  
 Wywołuje Menedżera debugowania sesji (SDM) [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) metodę, aby usunąć oczekującym punktem przerwania i wszystkie powiązane punkty przerwania powiązany z niego.  
  
> [!NOTE]
>  Pojedynczy punkt przerwania powiązania mogą być również usuwane przez wywołanie do [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)