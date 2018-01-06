---
title: "Zasady użycia narzędzi profilowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5585f6828677387d07f00039634fdfe904216ef2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-tools-usage-rules"></a>Reguły korzystania z narzędzi profilowania
Reguły wydajności w kategorii profilowania użycia narzędzia zapewniają wskazówek dotyczących używania profilera do zbierania danych najbardziej efektywny sposób.  
  
|||  
|-|-|  
|[DA0002: Brak biblioteki VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|Profilowanie wiersza polecenia może zawierać niekompletne dane dla [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] plików binarnych. Może to być spowodowane nie ustawienia zmiennych środowiskowych poprawne.|  
|[DA0003: Wiele przykładów jądra](../profiling/da0003-many-kernel-samples.md)|Zarejestrowano wiele próbek profilowania, które wystąpiło poza wykonywania docelowy plik binarny. Aby zbierać dane dokładniejsze, należy wziąć pod uwagę przy użyciu metody instrumentacji.|  
|[DA0004: Znaczące wykorzystanie procesora](../profiling/da0004-high-processor-usage.md)|Dane profilowania sugeruje, że podczas przebiegu profilowania były stale zajęte procesorów. Aby zbierać dane dokładniejsze, należy wziąć pod uwagę przy użyciu metody próbkowania.|  
|[DA0008: Kilka zebranych próbek](../profiling/da0008-few-samples-collected.md)|Liczba próbek zebranych podczas przebiegu profilowania nie jest wystarczająco wysoka, aby być statystycznie istotna. Należy wziąć pod uwagę profilowanie ponownie i uruchamiania aplikacji przez dłuższy czas. Można także rozważyć użycie metody Instrumentacji do zbierania danych.|  
|[DA0026: Nadmierne zużycie czasu procesora CPU w trybie jądra](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|Wystąpił znaczną ilość czasu w przebiegu profilowania w trybie jądra procesora. Przy użyciu wywołań systemowych Metryka zamiast używać jako metrykę czasu, należy wziąć pod uwagę próbkowania.|  
|[DA0029: Nieobsługiwana wersja środowiska CLR](../profiling/da0029-unsupported-clr-version.md)|PROFILOWANEGO danych binarnych jest używana jest wersja [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nie jest obsługiwana przez profiler. Raportów profilera nie można rozpoznać nazwy symbolu.|  
|[DA0030: Zbieraj pomiary interakcji warstw dla projektów bazy danych](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Duża liczba wywołań metod w <xref:System.Data?displayProperty=fullName> zebrano przestrzeni nazw. Aby dołączyć dane o wywołania bazy danych, należy wziąć pod uwagę uruchamia zbieranie danych o interakcji z warstwami w Twoim profilu.|