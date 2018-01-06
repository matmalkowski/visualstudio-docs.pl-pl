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
ms.workload: multiple
ms.openlocfilehash: 2d1646cd587295f2854399cfc24603ce1f1910e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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