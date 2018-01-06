---
title: 'DA0010: GetHashCode kosztowne | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ff2dbc1d98375b7199ab710412639fe4333c342d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Expensive GetHashCode
|||  
|-|-|  
|Identyfikator reguły|DA0010|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metod profilowania|Pobierania próbek<br /><br /> Pamięci platformy .NET|  
|Komunikat|Funkcje GetHashCode powinny być tanie i nie alokować wszystkie pamięci. Jeśli to możliwe zmniejszyć złożoność funkcji wartości skrótu.|  
|Typ komunikatu|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 Wywołania metody GetHashCode typu są znaczna część danych profilowania lub metoda przydziela pamięć.  
  
## <a name="rule-description"></a>Opis reguły  
 Tworzenie skrótu jest technika szybko lokalizowanie określonego elementu w kolekcji duże. Ponieważ tabele hash mogą być bardzo duże i trzeba obsługuje bardzo dużej szybkości dostępu, tabele hash powinny być bardzo wydajny. Możliwa tego wymagania jest, że metody GetHashCode w programie .NET Framework nie należy przydzielić pamięci. Przydzielanie pamięci zwiększa obciążenie moduł garbage collector i udostępnia metodę potencjalnych opóźnienia, jeśli stają się niezbędne do uruchomienia wyrzucanie elementów bezużytecznych w wyniku żądania alokacji.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Upraszczanie metody.