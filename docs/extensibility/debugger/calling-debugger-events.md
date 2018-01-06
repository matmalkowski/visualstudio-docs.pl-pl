---
title: "Wywoływanie zdarzeń debugera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4a3870921fab82c92b57b9c64dd30bda109c3bcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="calling-debugger-events"></a>Wywoływanie zdarzeń debugera
Zdarzenia w sesji debugowania występują w żadnej określonej kolejności.  
  
## <a name="discussion"></a>Omówienie  
 Aby poznać wzorzec wywołań między aparat debugowania (DE) i Menedżer debugowania sesji (SDM), następujące reprezentuje wywołanie kolejność zdarzeń występujących w typowej sesji debugowania:  
  
1.  [Dołączanie i odłączanie do programu](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [Uruchamianie debugera](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [Trwa przerywanie wykonywania programu](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [Tworzenie punktu przerwania](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Gdy jest powiązany punkt przerwania lub staje się niepowiązanych](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Błędy punktu przerwania](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Aktywując punkt przerwania](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [Usuwanie punktu przerwania](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Wprowadzanie tryb przerwania](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Wykonywanie krok po kroku, w trybie przerwania](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Szacowanie wyrażeń w trybie przerwania](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Obsługa wyjątków](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)