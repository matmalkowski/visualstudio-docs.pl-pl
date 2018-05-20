---
title: Widok drzewa wywołań - dane próbkowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 90035daf13008122e7d529408a6de0389b311628
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="call-tree-view---sampling-data"></a>Widok drzewa wywołań - dane próbkowania
Widok drzewa wywołań Wyświetla ścieżek wykonywania funkcji, które zostały przechodzić w profilowanych aplikacji.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Korzeń drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcja zawiera wszystkie funkcje, które mu i dane wydajności dotyczące tych wywołań funkcji.  
  
 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji do łączna liczba próbek w przebiegu profilowania.  
  
## <a name="highlight-the-execution-hot-path"></a>Wyróżnij ścieżkę aktywną wykonywania  
 Widok drzewa wywołań można rozwijać i wyróżnij ścieżkę wykonywania procesu lub funkcji, które zostało pobrane najczęściej. Aby wyświetlić najbardziej aktywne ścieżki, kliknij prawym przyciskiem myszy proces lub funkcji, a następnie kliknij przycisk **rozwiń aktywnej ścieżki**.  
  
## <a name="set-the-call-tree-root-node"></a>Ustaw węzła głównego drzewa wywołań  
 Każdy proces w przebiegu profilowania jest wyświetlana jako węzła głównego. Aby ustawić węzeł początkowy widok drzewa wywołań, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierz **ustawić głównego**.  
  
 Po ustawieniu węzła głównego pozwala wyeliminować wszystkie wpisy z widoku, z wyjątkiem poddrzewo wybranego węzła. Aby zresetować węzła głównego z powrotem do pierwotnego węzła, kliknij prawym przyciskiem myszy w oknie Widok drzewa wywołań i wybierz **zresetować głównego**.  
  
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
|**poziom**|Długość tej funkcji w drzewie wywołań. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Wyłącznych próbek**|Liczba próbek, które zostały zebrane w tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań. Ta liczba nie obejmuje przykłady, które zostały zebrane w funkcjach, które zostały wywołane przez funkcję.|  
|**% Wyłącznych próbek**|Procent wszystkich próbek w przebiegu profilowania, które zostały wyłącznych próbek w tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
|**Przykłady włącznie**|Liczba próbek, które zostały zebrane w tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań. Ta liczba uwzględnia również przykłady, które zostały zebrane w funkcjach, które zostały wywołane przez funkcję.|  
|**% Próbek włącznie**|Procent wszystkie przykłady w przebiegu profilowania, które zostały przykłady włącznie tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok drzewa wywołań - dane z próbkowania profilera](../profiling/call-Tree-view-sampling-data.md)   
 [Drzewie wywołań view - próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Widok drzewa wywołań - Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)