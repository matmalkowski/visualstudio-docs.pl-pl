---
title: 'DA0026: Nadmierne Procesora w trybie jądra czasu przetwarzania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 4a571b0eee0a0cdd4b6e232dc13bd8e8923da805
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750184"
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
  
## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń  
 Aby zbadać rodzaje wywołań systemowych, które dokonuje aplikacji, ponownie uruchom profil i wybierz opcję, aby zebrać przykłady oparte na wywołań systemowych. Zobacz [porady: Wybieranie zdarzeń pobierania próbek](../profiling/how-to-choose-sampling-events.md) w przypadku korzystania z narzędzi profilowania w IDE, aby uzyskać więcej informacji. Jeśli używasz narzędzi profilowania z wiersza polecenia, zobacz **opcje interwał próbkowania** sekcji [VSPerfCmd](../profiling/vsperfcmd.md) artykułu w odwołaniu do narzędzia wiersza polecenia narzędzi profilowania.