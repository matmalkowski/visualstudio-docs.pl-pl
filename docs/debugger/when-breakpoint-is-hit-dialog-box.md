---
title: "Po osiągnięciu punktu przerwania — okno dialogowe trafień | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e91841f1146d23305577cc00059f0bf9d505a90
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Okno dialogowe wyświetlane po osiągnięciu punktu przerwania
Za pomocą tego okna dialogowego można dostosowywać akcję, która występuje, gdy punkt przerwania zostaje trafiony.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Drukowanie wiadomości**  
 Drukuje wiadomości, przy użyciu składni DebuggerDisplay. Aby uzyskać więcej informacji, zobacz [za pomocą atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 To pole tekstowe obsługuje również specjalnych słów kluczowych (na przykład $ADDRESS), które mogą być używane samodzielnie lub w nawiasy klamrowe DebuggerDisplay wyrażenia. Słowa kluczowe dostępne są wyświetlane w oknie dialogowym.  
  
 **Kontynuować wykonywania**  
 Ten formant jest włączona tylko wtedy, gdy **Drukuj komunikat** jest zaznaczone. Z tym formantem wybrany punkt przerwania jako śledzenia służy do śledzenia sieci wykonania programu, zamiast przerywanie, gdy zostaje trafiony lokalizacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)   
 [Za pomocą atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)