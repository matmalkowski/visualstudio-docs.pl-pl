---
title: 'DA0006: Zastąp metodę Equals typami wartości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5e0d79b164c521bd3e0da53738d49451ff2a7af
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749986"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Przesłoń metodę equals typami wartości
|||  
|-|-|  
|Identyfikator reguły|DA0006|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metody Profiiling|Pobierania próbek|  
|Komunikat|Przesłoń metodę Equals i operator równości w typach wartości.|  
|Typ Messge|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 Wywołania do metody Equals i operatory równości typu publicznego wartości są znaczna część danych profilowania. Rozważ zaimplementowanie bardziej efektywną metodą.  
  
## <a name="rule-description"></a>Opis reguły  
 Dla typów wartości używa dziedziczone wykonania Equals <xref:System.Reflection> biblioteki i porównuje wartości wszystkich pól w typie. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli użytkownicy do porównywania lub sortowanie wystąpień lub używać ich jako tabeli klawiszy skrótów, danego typu wartości powinny implementować równości. Jeśli język programowania obsługuje przeciążania operatorów, należy również zapewniać implementację elementu Operatory równości i nierówności.  
  
 Aby uzyskać więcej informacji o sposobie Przesłoń metodę Equals i operatory równości, zobacz [wskazówki dotyczące implementowania metodę Equals i Operator równości (==)](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Na przykład wykonawczych Equals i operatory równości, zobacz reguł analizy kodu [CA1815: Przesłoń metodę equals i operator równości dla typów wartości](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)