---
title: Widok funkcji - dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 1e3ee9fa3b927d05de9c08e913d5c8f96ead59db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="functions-view---net-memory-sampling-data"></a>Widok funkcji - dane próbkowania pamięci .NET
Widok funkcji alokacji pamięci .NET profilowania dane zebrane przy użyciu metody pobierania próbek zawiera listę funkcji, które przydzielonej pamięci podczas przebiegu profilowania i w raportach, rozmiar i liczba przydziałów.  
  
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
|**Alokacje włącznie**|Całkowita liczba obiektów przydzielonych w tej funkcji i jej funkcji podrzędnych.|  
|**% Alokacji włącznie**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu, który profilowania były alokacji włącznie tej funkcji.|  
|**Wyłączny alokacji**|Liczba obiektów, które zostały utworzone podczas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Ta liczba nie obejmuje obiekty, które zostały utworzone w funkcjach podrzędnych.|  
|**% Wyłącznego alokacji**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu, który profilowania były wyłącznego alokacji tej funkcji.|  
|**Bajty włącznie**|Liczba bajtów pamięci, które zostały przydzielone tej funkcji i jej funkcji podrzędnych.|  
|**% Bajtów włącznie**|Procent wszystkich bajtów pamięci przydzielone w przebiegu, który profilowania były bajtów włącznie tej funkcji.|  
|**Wyłączny bajtów**|Liczba bajtów pamięci, które zostały przydzielone przez tę funkcję, ale nie przez jej funkcji podrzędnych.|  
|**% Wyłącznego bajtów**|Procent wszystkich bajtów pamięci przydzielone w przebiegu, który profilowania były wyłącznego bajtów tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok funkcji - Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Widok funkcji](../profiling/functions-view-sampling-data.md)   
 [Widok funkcji](../profiling/functions-view-instrumentation-data.md)