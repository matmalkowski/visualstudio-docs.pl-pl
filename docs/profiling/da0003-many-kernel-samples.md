---
title: 'DA0003: Wiele przykładów jądra | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97e2e745b59a22110f6392e2cd6fec1aea0a667a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750236"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Wiele przykładów jądra
|||  
|-|-|  
|Identyfikator reguły|DA0003|  
|Kategoria|Użycie narzędzia profilowania|  
|Metod profilowania|Pobierania próbek|  
|Komunikat|Masz wysoki wskaźnik próbek w trybie jądra. Może to oznaczać wysoki poziom aktywności We/Wy lub wysokie tempo przełączania kontekstu. Należy rozważyć ponownym sprofilowaniem aplikacji z użyciem trybu instrumentacji.|  
|Typ reguły|Informacje|  
  
## <a name="cause"></a>Przyczyna  
 Znaczna część przykłady stos wywołań, które zostały zebrane dla aplikacji zostały wykonywania w trybie jądra. Należy rozważyć profilowania aplikacji przy użyciu innej metody profilowania.  
  
## <a name="rule-description"></a>Opis reguły  
 W systemie Windows można wykonać kodu w trybie jądra lub w trybie użytkownika. (Tryb jądra jest również nazywany trybie uprzywilejowanym.) Tylko kod systemu niskiego poziomu, takie jak sterownik urządzenia, zostanie uruchomiony w trybie jądra. Aplikacja w trybie użytkownika, można przejść do trybu jądra do wykonywania operacji We/Wy, oczekiwania wątku lub procesu elementy podstawowe synchronizacji, lub czy wywołań systemowych.  
  
 Próbkowanie jest najbardziej efektywne, gdy są profilowanie aplikacji, które spędzają większość czasu podczas pracy w trybie użytkownika. Liczba próbek, które zostały zebrane podczas wykonywania w trybie jądra aplikacji można określić częste operacji We/Wy lub może wskazywać tego kontekstu, w którym występują przełączników. Żadna z tych operacji należy zbadać za pomocą metody pobierania próbek. Podjęto zbyt wiele przykładów trybu jądra, dane z próbkowania nie może zawierać wystarczającej liczby próbek trybu użytkownika statystycznie znaczący.  
  
## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń  
 Należy rozważyć profilowania aplikację ponownie przy użyciu jednego z następujących opcji:  
  
-   Profilu przy użyciu metody instrumentacji.  
  
-   Zwiększyć częstotliwość próbkowania w celu próbuje zbierać więcej przykładów w trybie użytkownika.