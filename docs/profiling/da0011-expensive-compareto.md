---
title: 'DA0011: Wykonanie funkcji CompareTo kosztowne | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f7ef867fc40a93948e4de4f5410609ef03aff19
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="da0011-expensive-compareto"></a>DA0011: Expensive CompareTo
|||  
|-|-|  
|Identyfikator reguły|DA0011|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metod profilowania|Pobierania próbek<br /><br /> Pamięci platformy .NET|  
|Komunikat|Funkcje CompareTo powinny być tanie i nie alokować wszystkie pamięci. Zmniejszyć złożoność funkcji CompareTo, jeśli to możliwe.|  
|Typ reguły|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 CompareTo — metoda typu jest kosztowna lub przydziela pamięć.  
  
## <a name="rule-description"></a>Opis reguły  
 Metody CompareTo powinny być skuteczne i nie należy przydzielić pamięci.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Upraszczanie CompareTo — metoda.