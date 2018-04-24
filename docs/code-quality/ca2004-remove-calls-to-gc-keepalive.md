---
title: 'CA2004: Usuń wywołania do GC.KeepAlive'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2f05764f5147a064815cdb744420686fb6a5a7c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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