---
title: Widok funkcji - dane Kontencji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1250dfc781b57f3b289cbafc9d386b27b669ddf7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680547"
---
# <a name="functions-view---contention-data"></a>Widok funkcji — dane rywalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [widok funkcji - dane Kontencji](https://docs.microsoft.com/visualstudio/profiling/functions-view-contention-data).  
  
Raport funkcji widoku list danych rywalizacji o zasoby funkcji w trakcie uruchomienia profilowania, które zostały zablokowane z wykonanie w trakcie uruchomienia profilowania.  
  
 W poniższej tabeli przedstawiono wartości, które są wyświetlane w widoku funkcji w pliku danych profilowania, które zostały zebrane za pomocą metody współbieżności.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Wyłączny czas blokowania**|Ilość czasu, w którym ta funkcja został zablokowany wykonywanie kodu w treści funkcji. Czas blokowania w funkcjach, które zostały wywołane przez funkcję nie jest włączony.|  
|**% Własnego czasu blokowania**|Procent wszystkich czas blokowania podczas uruchomienia profilowania, który był wyłączny czas blokowania w tej funkcji.|  
|**Rywalizacje wyłączne**|Liczba przypadków, które tej funkcji został zablokowany wykonywanie kodu w treści funkcji. Rywalizacje w funkcjach, które zostały wywołane przez funkcję nie są uwzględniane.|  
|**% Rywalizacji wyłącznych**|Wartość procentowa rywalizacji wszystkich podczas uruchomienia profilowania były rywalizacji wyłącznych tej funkcji.|  
|**Adres funkcji**|Adres funkcji.|  
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|  
|**Całkowity czas blokowania**|Czas, jaki ta funkcja lub funkcja, która została wywołana przez tę funkcję zablokowano wykonywania.|  
|**% Całkowitego czasu blokowania**|Procent wszystkich czas blokowania podczas uruchomienia profilowania, który był całkowity czas blokowania w tej funkcji lub modułu.|  
|**Rywalizacje włączne**|Ile razy ta funkcja lub funkcja, która została wywołana przez tę funkcję zablokowano wykonywania.|  
|**% Rywalizacji włącznych**|Wartość procentowa wszystkie rywalizacje w uruchomienia profilowania były rywalizacji włącznych tej funkcji lub modułu.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym wykonywania funkcji.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok funkcji](../profiling/functions-view.md)   
 [Widok funkcji - Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Widok funkcji - próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Widok funkcji](../profiling/functions-view-instrumentation-data.md)   
 [Widok funkcji](../profiling/functions-view-sampling-data.md)



