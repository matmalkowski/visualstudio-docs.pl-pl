---
title: "Odwołanie do reguły wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bec05a24a932816374766c107c1aab6f018e77cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="performance-rules-reference"></a>Zasady wydajności — Odwołanie
Zasady wydajności narzędzi profilowania zapewniają dodatkowe ostrzeżenia i informacje o wydajności aplikacji. Reguły wydajności analizowanie danych w przebiegu profilowania, zebrane ze źródeł, takich jak liczniki wydajności procesora i systemu Windows. Reguła komunikaty są wyświetlane w oknie dane wyjściowe błędów [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] zintegrowane środowisko deweloperskie. Komunikaty są wyświetlane z jedną z następujących poziomów reguły:  
  
|||  
|-|-|  
|**Błąd**|Kilka reguł generowanie komunikatów o błędach, ponieważ większość problemów z wydajnością nie są bezpośrednie błędy. Komunikat o błędzie może oznaczać błąd zbierania danych profilowania.|  
|**Ostrzeżenie**|Ostrzeżenia wskazują obszar aplikacji, które potencjalnie może być źródłem problemów z wydajnością lub które mogą korzystać z optymalizacji.|  
|**Informacje**|Komunikaty informacyjne wskazują, że analiza warunek reguły nie Osiągnięto próg, aby wygenerować komunikat o błędzie, albo że informacje w wiadomości jest przydatne, ale nie odzwierciedla problem z wydajnością.|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zasady wydajności według ID](../profiling/performance-rules-by-id.md)  
  
 Zasady wydajności narzędzi profilowania są zorganizowane w czterech kategorii:  
  
|||  
|-|-|  
|[Zasady wydajności użycia programu .NET framework](../profiling/dotnet-framework-usage-performance-rules.md)|Zasady, które ułatwiają efektywnie korzystać z programu .NET Framework.|  
|[Pamięci oraz stronicowanie reguły wydajności](../profiling/memory-and-paging-performance-rules.md)|Reguły, które analizowanie zarządzanego pamięci i stronicowania działanie aplikacji.|  
|[Reguły korzystania z narzędzi profilowania](../profiling/profiling-tools-usage-rules.md)|Zasady, które ułatwiają efektywnie korzystać z narzędzia profilowania.|  
|[Reguły wydajności monitorowania zasobu](../profiling/resource-monitoring-performance-rules.md)|Uruchom wiadomości informacji o wykorzystaniu procesora i pamięci w profilowania.|