---
title: "CA2004: Usuń wywołania do wykazu Globalnego. KeepAlive | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dd6cc8b51ddd8f9e8813229cf66b9facb52e4668
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Usuń wywołania do GC.KeepAlive
|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|CheckId|CA2004|  
|Kategoria|Microsoft.Reliability|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Użyj klasy `SafeHandle` , ale nadal zawierać wywołania `GC.KeepAlive`.  
  
## <a name="rule-description"></a>Opis reguły  
 Jeśli są konwertowane na `SafeHandle` użycia, Usuń wszystkie wywołania `GC.KeepAlive` (obiekt). W takim przypadku klasy nie powinny wywoływać `GC.KeepAlive`, zakładając, że nie ma finalizator, ale korzystają z `SafeHandle` do ukończenia dojścia systemu operacyjnego dla nich.  Mimo że koszt pozostawienie w wywołaniu `GC.KeepAlive` może być niewielka, mierzony wydajności, z punktu widzenia użytkownika który wywołanie `GC.KeepAlive` jest konieczne lub wystarczające, aby rozwiązać problem, który nie istnieje już sprawia, że kod jest trudniej okres istnienia Obsługa.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Usuń wywołania `GC.KeepAlive`.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 To ostrzeżenie można pominąć tylko wtedy, gdy jest ona nieprawidłowa technicznie można przekonwertować na `SafeHandle` użycia w klasie.