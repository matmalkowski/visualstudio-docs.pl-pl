---
title: "Ostrzeżenia niezawodności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d3ac06911009a24640031fd3a2306110f289014f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="reliability-warnings"></a>Ostrzeżenia niezawodności
Ostrzeżenia niezawodności obsługuje niezawodności biblioteki i aplikacji, takich jak odpowiednie użycie pamięci i wątku.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Reguła|Opis|  
|----------|-----------------|  
|[CA2000: Usuwanie obiektów przed utratą zakresu](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Ze względu na to, że może wystąpić wyjątkowe zdarzenie, które uniemożliwi uruchomienie finalizatora obiektu, obiekty powinny być jawnie usuwane, zanim wszystkie odwołania do niego znajdą się poza zakresem.|  
|[CA2001: Unikaj wywoływania problematycznych metod](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Element członkowski wywołuje potencjalnie niebezpieczną lub problematyczną metodę.|  
|[CA2002: Nie blokuj obiektów o słabej tożsamości](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu.|  
|[CA2003: Nie Traktuj włókien jako wątków](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Zarządzanego wątku jest traktowana jako wątku Win32.|  
|[CA2004: Usuń wywołania do wykazu Globalnego. Utrzymywania aktywności](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Jeśli są konwertowane na użycie klasy SafeHandle, należy usunąć wszystkie wywołania GC. KeepAlive (obiekt). W takim przypadku klas nie powinna mieć wywołać GC. Obsługa KeepAlive, zakładając, że nie ma finalizator, ale zależne od klasy SafeHandle w celu zakończenia systemu operacyjnego dla nich.|  
|[CA2006: Użyj SafeHandle, aby hermetyzować zasoby natywne](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Wykorzystanie elementu IntPtr w kodzie zarządzanym może wskazywać na potencjalny problem dotyczący bezpieczeństwa i niezawodności. Wszystkie użycia elementu IntPtr muszą być przejrzane w celu ustalenia, czy użycie elementu SafeHandle lub podobnej technologii jest w tym miejscu wymagane.|