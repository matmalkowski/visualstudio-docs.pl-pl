---
title: Widok drzewa wywołań - dane Instrumentacji pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 09c87c3bcde262eac0865bd43046eea722a94b8d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Widok drzewa wywołań - dane Instrumentacji pamięci .NET
Widok drzewa wywołań danych pamięci .NET alokacji profilowania zebrane przy użyciu metody Instrumentacji Wyświetla ścieżek wykonywania funkcji, które zostały przechodzić w profilowanych aplikacji. Korzeń drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcja zawiera wszystkie funkcje mu i pamięci platformy .NET i danych o chronometrażu dla funkcji.  
  
 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji do liczby całkowitej lub rozmiar alokacji w przebiegu profilowania.  
  
## <a name="highlighting-the-execution-hot-path"></a>Wyróżnianie ścieżkę aktywną wykonywania  
 Widok drzewa wywołań można rozwijać i wyróżnij ścieżkę wykonywania procesu lub funkcja, która utworzyła największej większość obiektów pamięci. Aby wyświetlić najbardziej aktywne ścieżki, kliknij prawym przyciskiem myszy proces lub funkcji, a następnie kliknij **rozwiń aktywnej ścieżki**.  
  
## <a name="setting-the-call-tree-root-node"></a>Ustawienie węzła głównego drzewa wywołań  
 Każdy proces w przebiegu profilowania jest wyświetlana jako węzła głównego. Można ustawić węzeł początkowy widok drzewa wywołań prawym przyciskiem myszy węzeł, aby ustawić jako węzeł początkowy, a następnie wybierając **ustawić głównego**.  
  
 Po ustawieniu węzła głównego pozwala wyeliminować wszystkie wpisy z widoku, z wyjątkiem poddrzewo wybranego węzła. Możesz przywrócić węzła głównego węzła przeglądana; Kliknij prawym przyciskiem myszy w oknie Widok drzewa wywołań i wybierz **zresetować głównego**.  
  
## <a name="general"></a>Ogólne  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Adres funkcji**|Adres funkcji.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Liczba wywołań**|Całkowita liczba wywołań tej funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa modułu**|Nazwa modułu zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa przypisana do procesu.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, która jest spowodowany przez instrumentacji. Narzut sondy odjęciu z wszystkich wyłącznego razy.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych spowodowany przez instrumentacji. Narzut sondy odjęciu z zawsze włącznie.|  
|**Typ**|Kontekst funkcji:<br /><br /> -   **0** -bieżącą funkcję<br />-   **1** — funkcja, która wywołuje bieżącą funkcję<br />-   **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Nazwa głównej funkcji**|Nazwa bieżącej funkcji. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
  
## <a name="net-memory-values"></a>Wartości pamięci .NET  
 Wraz z wartościami granicznymi wartości pamięci .NET funkcji wskazuje liczbę (alokacji) i rozmiar (w bajtach) obiektów, które zostały utworzone przez funkcji i funkcji, które zostały wywołane przez funkcję.  
  
 Wartości wyłącznego pamięci wskazują liczby i rozmiaru obiektów, które zostały utworzone przez kod w treści funkcji, a nie przez funkcje, które zostały wywołane przez funkcję.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Alokacje włącznie**|Liczba obiektów, które zostały przydzielone wystąpień tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Liczba ta obejmuje przydziałów, które zostały dokonane za pomocą funkcji podrzędnych.|  
|**% Alokacji włącznie**|Procent wszystkich obiektów, które zostały utworzone w przebiegu, który profilowania były włącznie alokacji wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań.|  
|**Wyłączny alokacji**|Liczba obiektów, które zostały przydzielone wystąpień tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Ta liczba nie obejmuje przydziałów, które zostały dokonane za pomocą funkcji podrzędnych.|  
|**% Wyłącznego alokacji**|Procent wszystkich obiektów, które zostały utworzone w przebiegu, który profilowania były wyłącznego alokacji wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań.|  
  
## <a name="elapsed-inclusive-values"></a>Czas wartości włącznie  
 Czas włącznie wartości wskazują czas, który został funkcji w stosie wywołań. Czas obejmuje czas przeznaczony w funkcje, które zostały wywołane przez funkcję i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|Suma upłynął całkowity czas wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**% Całkowity czas, który upłynął**|Procent całkowitej upłynął całkowity czas uruchomienia profilowania przeznaczony na całkowity czas całkowity czas tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
|**Avg, który upłynął całkowity czas**|Średnia upłynął całkowity czas wywołanie tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Maksymalny czas, który upłynął włącznie**|Maksymalna upłynął całkowity czas wywołanie tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Min, który upłynął całkowity czas**|Minimalna upłynął całkowity czas wywołanie tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wartości wyłączności  
 Czas wyłącznego wartości wskazują czas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Czas obejmuje czas w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia. Jednak czas nie zawiera czas przeznaczony na funkcje, które zostały wywołane przez funkcję.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Czas, który upłynął wyłączności**|Suma upłynął własny czas wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**% Wyłącznego czas, który upłynął**|Procent całkowitej upłynął własny czas przebiegu profilowania, przeznaczony na całkowity czas własny czas tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
|**Śr. na wyłączność, który upłynął czas**|Średnia upłynął własny czas wywołanie tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Maksymalny czas, który upłynął wyłączności**|Maksymalna upłynął własny czas wywołanie tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Min na wyłączność, który upłynął czas**|Minimalna upłynął własny czas wywołanie tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
  
## <a name="application-inclusive-values"></a>Wartości z wartościami granicznymi aplikacji  
 Wartości z wartościami granicznymi aplikacji wskazują czas, który został funkcji w stosie wywołań. Czas nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia. Czas obejmują czas przeznaczony w funkcjach podrzędne, które zostały wywołane przez funkcję.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|Łączny całkowity czas aplikacji wszystkie wywołania tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
|**% Całkowity czas aplikacji**|Procent całkowitej upłynął całkowity czas uruchomienia profilowania przeznaczony na całkowity czas aplikacji całkowita tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłącznego aplikacji  
 Wartości wyłącznego aplikacji wskazują czas przeznaczony w funkcji z wyłączeniem czas przeznaczony na funkcje podrzędne, które zostały wywołane przez funkcję. Czas także wyklucza wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|Całkowita liczba własny czas aplikacji wszystkie wywołania tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
|**% Własny czas aplikacji**|Procent całkowitej upłynął własny czas przebiegu profilowania, przeznaczony na własny czas łączny aplikacji tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|  
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji, gdy została wywołana przez funkcję nadrzędnego w drzewie wywołań.|