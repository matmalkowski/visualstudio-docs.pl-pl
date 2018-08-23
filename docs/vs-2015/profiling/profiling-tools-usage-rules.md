---
title: Reguły korzystania z narzędzi profilowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d508fdfe1845a75f0ef7e0ba36730afbaa4e157
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685306"
---
# <a name="profiling-tools-usage-rules"></a>Reguły korzystania z narzędzi profilowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [reguły korzystania z narzędzi profilowania](https://docs.microsoft.com/visualstudio/profiling/profiling-tools-usage-rules).  
  
Reguły wydajności w kategorii użycia narzędzia profilowania zapewniają wskazówki dotyczące używania programu profilującego do zbierania danych w najbardziej efektywny sposób.  
  
|||  
|-|-|  
|[DA0002: Brak biblioteki VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|Profilowanie wiersza polecenia może być zawiera niepełne dane dla [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] plików binarnych. Może to być spowodowane nie Ustawianie zmiennych środowiskowych poprawne.|  
|[DA0003: Wiele przykładów jądra](../profiling/da0003-many-kernel-samples.md)|Wiele przykładów profilowania, które wystąpiło poza wykonywania docelowy plik binarny zostały zapisane. Aby zebrać dokładniejsze dane, należy wziąć pod uwagę przy użyciu metody instrumentacji.|  
|[DA0004: Znaczące wykorzystanie procesora](../profiling/da0004-high-processor-usage.md)|Danych profilowania sugeruje, że procesorów są stale zajęte podczas uruchomienia profilowania. Aby zebrać dokładniejsze dane, należy wziąć pod uwagę przy użyciu metody próbkowania.|  
|[DA0008: Kilka zebranych próbek](../profiling/da0008-few-samples-collected.md)|Liczba próbek zebrane podczas uruchomienia profilowania nie jest wystarczająco wysoka, będzie statystycznie istotne. Należy wziąć pod uwagę profilowanie ponownie i uruchamiania aplikacji przez dłuższy czas. Możesz też rozważyć przy użyciu metody instrumentacji, aby zebrać dane.|  
|[DA0026: Nadmierne zużycie czasu procesora CPU w trybie jądra](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|Wystąpił znaczną ilość czasu, w trakcie uruchomienia profilowania w trybie jądra procesora. Za pomocą wywołania systemowe jako metrykę zamiast przy użyciu czasu jako metrykę, należy wziąć pod uwagę próbkowania.|  
|[DA0029: Nieobsługiwana wersja środowiska CLR](../profiling/da0029-unsupported-clr-version.md)|Profilowane dane binarne używa wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] który nie jest obsługiwany przez profiler. Raportów profilera nie można rozpoznać nazwy symboli.|  
|[DA0030: Zbieraj pomiary interakcji warstw dla projektów bazy danych](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Znaczna liczba wywołań metod w <xref:System.Data?displayProperty=fullName> zostały zebrane w przestrzeni nazw. Aby dołączyć dane dotyczące wywołań bazy danych, należy wziąć pod uwagę uruchamia zbieranie danych o interakcji między warstwami w Twoim profilu.|



