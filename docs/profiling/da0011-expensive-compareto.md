---
title: 'DA0011: Wykonanie funkcji CompareTo kosztowne | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 197d5402d935d7e1b377b6ec037535fbc2f65cfa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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