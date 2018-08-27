---
title: 'CA1600: Nie używaj priorytetu procesu bezczynności | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b211c1ab646d27cf32290d3c5c306719ba7decff
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902569"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Nie używaj priorytetu procesu bezczynności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1600: nie używaj priorytetu procesu bezczynności](https://docs.microsoft.com/visualstudio/code-quality/ca1600-do-not-use-idle-process-priority).

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategoria|Microsoft.Mobility|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Ta reguła jest uruchamiana podczas procesów są ustawione na `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Opis reguły
 Nie należy ustawiać priorytetu procesu na Idle. Procesy, które mają `System.Diagnostics.ProcessPriorityClass.Idle` , zajmują Procesor, może być bezczynne, a zatem będą blokować stan wstrzymania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ustaw procesy `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Ta reguła ma być pomijana, tylko wtedy, gdy priorytetu procesu bezczynności jest wymagany i zagadnienia dotyczące mobilności można bezpiecznie zignorować.



