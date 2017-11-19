---
title: "CA1600: Nie używaj priorytetu procesu bezczynności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e52a658bd6161542ce909b8294f33d6e4bf140ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Nie używaj priorytetu procesu bezczynności
|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|Kategoria|Microsoft.Mobility|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Tej reguły występuje, gdy procesy są ustawione na `ProcessPriorityClass.Idle`.  
  
## <a name="rule-description"></a>Opis reguły  
 Nie należy ustawiać priorytetu procesu na Idle. Procesy, które mają `System.Diagnostics.ProcessPriorityClass.Idle` będą używać Procesora, gdy byłby bezczynności i w związku z tym będzie blokować stan wstrzymania.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Ustaw procesy `ProcessPriorityClass.BelowNormal`.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Ta reguła ma być pomijana, tylko wtedy, gdy jest wymagane priorytetu procesu bezczynności i zagadnienia mobilności można bezpiecznie zignorować.