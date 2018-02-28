---
title: "Ostrzeżenia mobilności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 36f6bddab2d53e4c76830cf0a88ff4f02dc23a75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mobility-warnings"></a>Mobilność — Ostrzeżenia
Ostrzeżenia mobilności obsługuje zużycia energii wydajne.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Reguła|Opis|  
|----------|-----------------|  
|[CA1600: Nie używaj priorytetu procesu bezczynności](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Nie należy ustawiać priorytetu procesu na Idle. Procesy, które mają System.Diagnostics.ProcessPriorityClass.Idle, zajmują procesor, gdy może on być bezczynny, a zatem będą blokować stan gotowości.|  
|[CA1601: Nie używaj czasomierzy, które uniemożliwiają zmiany stanu zasilania](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Wyższa częstotliwość działań okresowych sprawi, że procesor będzie zajęty, co zakłóci działanie czasomierzy bezczynności oszczędzających energię, które wyłączają ekran i dyski twarde.|