---
title: Widok funkcji - dane Kontencji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d9dcf9ab34e5d0441f3c1ce3a47d5e148c9394d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="functions-view---contention-data"></a>Widok funkcji - dane Kontencji
Raport funkcji wyświetlania list danych kontencji funkcje w zostały zablokowane przebiegu profilowania pochodzący z wykonania podczas przebiegu profilowania.  
  
 W poniższej tabeli przedstawiono wartości, które są wyświetlane w widoku funkcje pliku danych profilowania, zebrane przy użyciu metody współbieżności.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Wyłączny czasu blokowania**|Ilość czasu, w którym ta funkcja została zablokowana wykonywanie kodu w treści funkcji. Czas blokowania w funkcje, które zostały wywołane przez funkcję nie jest włączony.|  
|**% Wyłącznego czasu blokowania**|Procent wszystkich czas blokowania w przebiegu profilowania, który był wyłącznego czas blokowania w tej funkcji.|  
|**Wyłączny rywalizacji**|Ile razy tej funkcji została zablokowana wykonywanie kodu w treści funkcji. Rywalizacji w funkcjach, które zostały wywołane przez funkcję nie są uwzględniane.|  
|**% Wyłącznego rywalizacji**|Wartość procentowa rywalizacji wszystkich w przebiegu profilowania były wyłącznego rywalizacji tej funkcji.|  
|**Adres funkcji**|Adres funkcji.|  
|**Nazwa funkcji**|Pełna nazwa funkcji.|  
|**Całkowity czas blokowania**|Czas, jaki tej funkcji lub funkcja, która została wywołana przez tę funkcję zostało zablokowane z wykonywania.|  
|**Całkowity czas blokowania %**|Procent wszystkich czasu blokowania w przebiegu profilowania, która była całkowity czas blokowania w tej funkcji lub modułu.|  
|**Wraz z wartościami granicznymi rywalizacji**|Ile razy tej funkcji lub funkcja, która została wywołana przez tę funkcję zostało zablokowane z wykonywania.|  
|**% Rywalizacji włącznie**|Wartość procentowa rywalizacji wszystkie, w którym profilowania były rywalizacji włącznie tej funkcji lub modułu.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym funkcja została uruchomiona.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok funkcji](../profiling/functions-view.md)   
 [Widok funkcji - Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Widok funkcji - próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Widok funkcji](../profiling/functions-view-instrumentation-data.md)   
 [Widok funkcji](../profiling/functions-view-sampling-data.md)