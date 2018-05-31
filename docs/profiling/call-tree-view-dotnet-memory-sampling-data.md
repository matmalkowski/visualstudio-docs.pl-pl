---
title: Widok drzewa wywołań - dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c3c7c70057380289272e86cf7187680746dafdd2
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
ms.locfileid: "34336048"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Widok drzewa wywołań - dane próbkowania pamięci .NET
Widok drzewa wywołań Wyświetla ścieżek wykonywania funkcji, które zostały przechodzić w profilowanych aplikacji. Korzeń drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcja zawiera wszystkie funkcje, które mu i danych alokacji pamięci .NET o wywołania tych funkcji.  
  
 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji do liczby całkowitej lub rozmiar alokacji w przebiegu profilowania.  
  
## <a name="highlight-the-execution-hot-path"></a>Wyróżnij ścieżkę aktywną wykonywania  
 Widok drzewa wywołań można rozwijać i wyróżnij ścieżkę wykonywania procesu lub funkcja, która utworzyła największej większość obiektów pamięci. Aby wyświetlić najbardziej aktywne ścieżki, kliknij prawym przyciskiem myszy proces lub funkcji, a następnie kliknij **rozwiń aktywnej ścieżki**.  
  
## <a name="set-the-call-tree-root-node"></a>Ustaw węzła głównego drzewa wywołań  
 Każdy proces w przebiegu profilowania jest wyświetlana jako węzła głównego. Aby ustawić węzeł początkowy widok drzewa wywołań do innego węzła, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierz **ustawić głównego**.  
  
 Po ustawieniu węzła głównego pozwala wyeliminować wszystkie wpisy z widoku, z wyjątkiem poddrzewo wybranego węzła. Możesz przywrócić węzła głównego węzła, który wyświetlana; Kliknij prawym przyciskiem myszy w oknie Widok drzewa wywołań i wybierz **zresetować głównego**.  
  
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
|**poziom**|Głębokość funkcji w drzewie wywołań.|  
|**Alokacje włącznie**|Liczba obiektów, które zostały przydzielone wystąpień tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Liczba ta obejmuje przydziałów, które zostały dokonane za pomocą funkcji podrzędnych.|  
|**% Alokacji włącznie**|Procent wszystkich obiektów, które zostały utworzone w przebiegu, który profilowania były alokacji włącznie tej funkcji.|  
|**Wyłączny alokacji**|Liczba obiektów, które zostały przydzielone wystąpień tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Ta liczba nie obejmuje przydziałów, które zostały dokonane za pomocą funkcji podrzędnych.|  
|**% Wyłącznego alokacji**|Procent wszystkich obiektów, które zostały utworzone w przebiegu, który profilowania były wyłącznego alokacji wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań.|  
|**Bajty włącznie**|Liczba bajtów w pamięci, które zostały przydzielone wystąpień tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Liczba ta obejmuje przydziałów, które zostały dokonane za pomocą funkcji podrzędnych.|  
|**% Bajtów włącznie**|Procent wszystkich bajtów pamięci przydzielone w przebiegu, który profilowania były alokacji włącznie tej funkcji.|  
|**Wyłączny bajtów**|Liczba bajtów w pamięci, które zostały przydzielone wystąpień tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Ta liczba nie obejmuje przydziałów, które zostały dokonane za pomocą funkcji podrzędnych.|  
|**% Wyłącznego bajtów**|Procent wszystkich bajtów pamięci przydzielone w przebiegu, który profilowania były wyłącznego alokacji tej funkcji.|  
  
## <a name="see-also"></a>Zobacz także  
 [Widok drzewa wywołań - Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)