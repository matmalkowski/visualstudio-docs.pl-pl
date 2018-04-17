---
title: 'DA0026: Nadmierne Procesora w trybie jądra czasu przetwarzania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3f7ab000e4f63c96c91038546145b85004bcc1f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Nadmierne przetwarzanie czasu procesora CPU w trybie jądra
|||  
|-|-|  
|Identyfikator reguły|TODO|  
|Kategoria|Użycie narzędzia profilowania|  
|Metoda profilowania|Pobierania próbek|  
|Komunikat|Zmierzono dość wysokie zużycie czasu Procesora w trybie jądra. Należy rozważyć zbadanie kodu źródłowego z włączonym próbkowaniem SysCall.|  
|Typ reguły|Informacje|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Udział czasu Procesora, który został uruchomiony w trybie jądra przekracza ilość czasu w trybie użytkownika. Należy wziąć pod uwagę profilowanie ponownie i pobierania próbek liczby wywołań systemowych (syscalls), aby ustalić przyczynę czas wykonywania trybu jądra wysoki.  
  
## <a name="rule-description"></a>Opis reguły  
 Stosunkowo dużą część czas wykonywania w trybie jądra działania aplikacji mogą uzasadniać dalszego postępowania. Aplikacja w trybie użytkownika przechodzi do trybu jądra do wykonywania operacji We/Wy, oczekiwania wątku lub procesu elementy podstawowe synchronizacji, lub czy wywołań systemowych. Można zbadać rodzaje wywołań systemowych sprawia, że aplikacja i funkcje, które są odpowiedzialne za je po wybraniu opcji zbieranie stosy wywołań próbki oparte na wywołań systemowych.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby zbadać rodzaje wywołań systemowych, które dokonuje aplikacji, ponownie uruchom profil i wybierz opcję, aby zebrać przykłady oparte na wywołań systemowych. Zobacz [porady: Wybieranie zdarzeń pobierania próbek](../profiling/how-to-choose-sampling-events.md) w przypadku korzystania z narzędzi profilowania w IDE, aby uzyskać więcej informacji. Jeśli używasz narzędzi profilowania z wiersza polecenia, zobacz **opcje interwał próbkowania** sekcji [VSPerfCmd](../profiling/vsperfcmd.md) tematu w narzędziach profilowania wiersza polecenia narzędzia odwołania.