---
title: 'DA0013: Znaczące wykorzystanie String.Split lub String.Substring | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c218dd9a7ee3266de2cf9e07933ed69aa23e73e7
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749885"
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
 Wywołania metod System.String.Split lub System.String.Substring są znaczna część danych profilowania. Rozważ użycie System.String.IndexOf lub System.String.IndexOfAny w przypadku testowania istnienie substring w ciągu.  
  
## <a name="rule-description"></a>Opis reguły  
 Metody Split operuje na obiekt ciągu i zwraca nowy tablicy ciągów przechowujący podciągów oryginału. Funkcja przydziela pamięć dla obiekt array zwrócony i przydziela dla każdego elementu tablicy, który odnajdzie nowy obiekt ciągu. Podobnie Substr — metoda działa na obiekt ciągu i zwraca nowy ciąg, który jest odpowiednikiem żądanego podciąg.  
  
 Jeśli zarządzanie przydziału pamięci jest szczególnie ważne w aplikacji, należy rozważyć użycie alternatywnych metod String.Split i String.Substr. Na przykład służy metoda IndexOf lub IndexOfAny można znaleźć określonego substring w ciągu znaków ciągu bez tworzenia nowego wystąpienia klasy String.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w **listy błędów** okna, aby przejść do [widok szczegółów funkcji](../profiling/function-details-view.md) pobierania próbek danych profilu. Sprawdź wywoływanie funkcji można znaleźć w sekcjach programu, które wykorzystują najczęstsze metody System.String.Split lub System.String.Substr. Jeśli to możliwe użyj metody IndexOf lub IndexOfAny można znaleźć określonego substring w ciągu znaków ciągu bez tworzenia nowego wystąpienia klasy String.