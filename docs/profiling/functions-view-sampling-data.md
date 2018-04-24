---
title: Widok funkcji - dane próbkowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f4b1eddfd2d4b0ab0f285b727b6bc6638ca2e8d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="functions-view---sampling-data"></a>Widok funkcji - dane próbkowania
Widoku raportu funkcji dla metody próbkowania profil zawiera funkcje, które zostały poddane próbkowaniu podczas przebiegu profilowania.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera funkcję.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa funkcji**|Pełna nazwa funkcji.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Adres funkcji.|  
|**Przykłady włącznie**|Łączna liczba próbek, które zostały zebrane podczas wykonywania tej funkcji; oznacza to, liczba próbek, które zostały zebrane, gdy ta funkcja była w stosie wywołań. Numer zawiera przykłady, które zostały zebrane podczas wykonywania zostały funkcje, które zostały wywołane przez tę funkcję.|  
|**% Próbek włącznie**|Wartość procentowa próbek wszystkie, w którym profilowania były włącznie próbek w tej funkcji.|  
|**Wyłącznych próbek**|Łączna liczba próbek, które zostały zebrane podczas wykonywania kodu w treści tej funkcji; oznacza to, gdy ta funkcja została szczycie stosu wywołań. Przykłady, które zostały zebrane w funkcjach, które zostały wywołane przez tę funkcję, nie są uwzględniane.|  
|**% Wyłącznych próbek**|Wartość procentowa próbek wszystkie, w którym profilowania były wyłącznych próbek w tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok funkcji - Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Widok funkcji - próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Widok funkcji](../profiling/functions-view-instrumentation-data.md)