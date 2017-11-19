---
title: "CA1601: Nie używaj czasomierzy, które uniemożliwiają zmianę stanu zasilania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5fc42c15beda68472f4a980fe96b0055b70a01cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Nie używaj czasomierzy, które uniemożliwiają zmianę stanu zasilania
|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Kategoria|Microsoft.Mobility|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Czasomierz ma interwał ustawić występuje więcej niż jeden raz na sekundę.  
  
## <a name="rule-description"></a>Opis reguły  
 Nie wykonuj sondowania częściej niż raz na sekundę lub użyj czasomierzy, które częściej niż jeden czasu na sekundę. Wyższa częstotliwość działań okresowych sprawi, że procesor będzie zajęty, co zakłóci działanie czasomierzy bezczynności oszczędzających energię, które wyłączają ekran i dyski twarde.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Ustaw czasomierz interwałów występuje mniej niż jeden raz na sekundę.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Ta reguła ma być pomijana, tylko wtedy, gdy wyzwalania czasomierza więcej niż jeden raz na sekundę jest wymagany i zagadnienia dotyczące mobilności można bezpiecznie zignorować.