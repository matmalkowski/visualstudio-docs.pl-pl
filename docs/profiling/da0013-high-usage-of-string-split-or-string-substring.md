---
title: "DA0013: Znaczące wykorzystanie String.Split lub String.Substring | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1101457388b5ba54752f47014c9c389fcb2cb073
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Znaczące wykorzystanie String.Split lub String.Substring
|||  
|-|-|  
|Identyfikator reguły|DA0013|  
|Kategoria|Wskazówki dotyczące użycia programu .NET framework|  
|Metod profilowania|Pobierania próbek|  
|Komunikat|Rozważ ograniczenie użycia funkcji String.Split i String.Substring.|  
|Typ reguły|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 Wywołania metod System.String.Split lub System.String.Substring są znaczna część danych profilowania. Rozważ użycie System.String.IndexOf lub System.String.IndexOfAny, jeśli testujesz istnienie substring w ciągu.  
  
## <a name="rule-description"></a>Opis reguły  
 Metody Split operuje na obiekt ciągu i zwraca nowy tablicy ciągów zawierającą podciągów oryginału. Funkcja przydziela pamięć dla obiekt array zwrócony i przydziela dla każdego elementu tablicy, który odnajdzie nowy obiekt ciągu. Podobnie Substr — metoda działa na obiekt ciągu i zwraca nowy ciąg, który jest odpowiednikiem podciąg, którego zażądano.  
  
 Jeśli zarządzanie przydziału pamięci jest szczególnie ważne w aplikacji, należy rozważyć użycie alternatywnych metod String.Split i String.Substr. Na przykład służy metoda IndexOf albo IndexOfAny można znaleźć określonego substring w ciągu znaków ciągu bez tworzenia nowego wystąpienia klasy String.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widok szczegółów funkcji](../profiling/function-details-view.md) pobierania próbek danych profilu. Sprawdź wywoływanie funkcji można znaleźć w sekcjach programu, które wykorzystują najczęstsze metody System.String.Split lub System.String.Substr. Jeśli to możliwe, należy użyć metody IndexOf albo IndexOfAny można znaleźć określonego substring w ciągu znaków ciągu bez tworzenia nowego wystąpienia klasy String.