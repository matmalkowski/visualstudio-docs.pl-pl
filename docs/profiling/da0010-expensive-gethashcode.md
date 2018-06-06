---
title: 'DA0010: GetHashCode kosztowne | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a670eb3145f3fd2ab9478dc68e0490cdeda8ac56
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749963"
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
 Tworzenie skrótu jest technika szybko lokalizowanie określonego elementu w kolekcji duże. Tabele hash może być duży i trzeba obsługuje bardzo dużej szybkości dostępu, tabele hash należy wydajne. Możliwa tego wymagania jest, że metody GetHashCode w programie .NET Framework nie należy przydzielić pamięci. Przydzielanie pamięci zwiększa obciążenie moduł garbage collector i udostępnia metody do potencjalnych opóźnienia, jeśli okaże się konieczne uruchomienie wyrzucanie elementów bezużytecznych w wyniku żądania alokacji.  
  
## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń  
 Upraszczanie metody.