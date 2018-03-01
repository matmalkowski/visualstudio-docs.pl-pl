---
title: "Widok modułów - dane Instrumentacji pamięci platformy .NET | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e67b1676495b6217a6134bc7e0f3f4cf74b1faf6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Widok modułów - dane Instrumentacji pamięci .NET
Widok modułów danych alokacji pamięci .NET zebrane przy użyciu metody Instrumentacji grupuje pamięci i danych o chronometrażu przez moduły, które zostały wykonane w przebiegu profilowania. Dane dla funkcji modułu profilowania znajduje się poniżej tego węzła modułu.  
  
## <a name="general"></a>Ogólne  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa modułu lub funkcji.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Liczba wywołań**|Całkowita liczba połączeń, które zostały wprowadzone do tego modułu lub funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję tej funkcji.|  
|**Nazwa modułu**|Nazwa modułu zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu, w którym wykonywania modułu lub funkcji.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji lub modułu z powodu instrumentacji.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji lub modułu i jej funkcji podrzędnych z powodu instrumentacji.|  
  
## <a name="net-memory-values"></a>Wartości pamięci .NET  
 Wraz z wartościami granicznymi wartości pamięci .NET funkcji wskazuje liczbę (alokacji) i rozmiar (w bajtach) obiektów, które zostały utworzone przez funkcji i jej funkcji podrzędnych.  
  
 Wartości wyłącznego pamięci wskazują liczby i rozmiaru obiektów, które zostały utworzone przez funkcję, a nie przez jej funkcji podrzędnych.  
  
 Wartości pamięci włącznie i wyłącznego modułu są sumę włącznie i wartości wyłącznego pamięci funkcji w module.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Alokacje włącznie**|— Dla funkcji, całkowita liczba obiektów, które zostały utworzone przez funkcję. Liczba ta obejmuje obiekty, które zostały utworzone przez funkcje, które zostały wywołane przez funkcję.<br />— Dla modułu liczbę obiektów w profilowania wykonywany przydzielone podczas wykonywania funkcji co najmniej jeden z modułu. Liczba ta obejmuje obiekty, które zostały przyznane w funkcjach, które zostały wygenerowane przez wywołania z funkcji modułu.|  
|**% Alokacji włącznie**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu, który profilowania były włącznie alokacji modułu lub funkcji.|  
|**Wyłączny alokacji**|— Dla funkcji, liczbę obiektów, które zostały utworzone podczas wykonywania kodu funkcji w treści funkcji (oznacza to, gdy funkcja znajdowała się w górnej części stosu wywołań). Ta liczba nie obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez funkcję.<br />— Dla modułu sumę wyłącznego alokacje funkcji w module.|  
|**% Wyłącznego alokacji**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu, który profilowania były wyłącznego alokacji modułu lub funkcji.|  
|**Wyłączny bajtów**|— Dla funkcji całkowita liczba bajtów pamięci przydzielone, gdy funkcja została uruchomiona kod w funkcji treści (Jeśli funkcja znajdowała się w górnej części stosu wywołań). Ta liczba nie obejmuje bajtów przydzielonych w funkcjach, które zostały wywołane przez funkcję.<br />— Dla modułu sumę wyłącznego bajtów, które zostały przydzielone funkcji w module.|  
|**% Wyłącznego bajtów**|Procent wszystkich bajtów przydzielonych w przebiegu, który profilowania były wyłącznego bajtów modułu, funkcji, wiersz lub instrukcji.|  
|**Bajty włącznie**|— Dla funkcji, liczba bajtów, które zostały przyznane przez funkcję. Liczba ta obejmuje bajtów przydzielonych w funkcjach, które zostały wywołane przez funkcję.<br />— Dla modułu liczba bajtów przydzielonych w profilowania wykonywany przydzielone podczas wykonywania funkcji co najmniej jeden z modułu. Liczba ta obejmuje obiekty, które zostały utworzone we wszystkich funkcji, które zostały wywołane przez funkcje modułu.|  
|**% Bajtów włącznie**|Procent wszystkich bajtów przydzielonych w przebiegu, który profilowania były włącznie bajtów modułu lub funkcji.|  
  
## <a name="elapsed-inclusive-values"></a>Czas wartości włącznie  
 Czas włącznie wartości wskazują czas, który został funkcji w stosie wywołań. Czas obejmuje czas przeznaczony w funkcji podrzędnych i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|— Dla funkcji, czas przeznaczony w funkcji. W tym czas przeznaczony w funkcji podrzędnych i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla modułu, okres, w których co najmniej jedną funkcję w module był w stosie wywołań.|  
|**% Całkowity czas, który upłynął**|Procent czas łączny całkowity czas profilowania wykonywany przeznaczony na czas łączny całkowity czas tego modułu lub funkcji.|  
|**Avg, który upłynął całkowity czas**|— Dla funkcji średnią upłynął całkowity czas wywołania tej funkcji.<br />— Dla modułu średnia upłynął całkowity czas wszystkie wywołania funkcji w module.|  
|**Maksymalny czas, który upłynął włącznie**|— Dla funkcji maksymalną upłynął całkowity czas wywołania tej funkcji.<br />— Dla modułu maksymalna upłynął całkowity czas wszystkie wywołania funkcji w module.|  
|**Min, który upłynął całkowity czas**|— Dla funkcji minimalnym upłynął całkowity czas wywołanie tego modułu lub funkcji.<br />— Dla modułu minimalnym upłynął całkowity czas wszystkie wywołania funkcji w module.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wartości wyłączności  
 Czas wyłącznego wartości wskazują czas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Czas obejmuje czas w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czas przeznaczony w funkcjach podrzędnych.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Czas, który upłynął wyłączności**|— Dla funkcji, czas przeznaczony na modułu lub funkcji. Zawiera wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czas przeznaczony na funkcje podrzędne.<br />— Dla modułu sumę upłynął wyłącznego razy funkcji w module.|  
|**% Wyłącznego czas, który upłynął**|Procent całkowitej czas własny czas profilowania wykonywany przeznaczony na całkowity czas własny czas tego modułu lub funkcji.|  
|**Śr. na wyłączność, który upłynął czas**|— Dla funkcji średnią upłynął własny czas wywołania tej funkcji.<br />— Dla modułu średnia upłynął własny czas wszystkie wywołania funkcji w module.|  
|**Maksymalny czas, który upłynął wyłączności**|— Dla funkcji maksymalną upłynął własny czas wywołania tej funkcji.<br />— Dla modułu maksymalna upłynął własny czas wszystkie wywołania funkcji w module.|  
|**Min na wyłączność, który upłynął czas**|— Dla funkcji minimalnym upłynął własny czas wywołanie tego modułu lub funkcji.<br />— Dla modułu minimalnym upłynął własny czas wszystkie wywołania funkcji w module.|  
  
## <a name="application-inclusive-values"></a>Wartości z wartościami granicznymi aplikacji  
 Wartości z wartościami granicznymi aplikacji wskazują czas, który został funkcji w stosie wywołań. Czas nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, jednak zawierać czas przeznaczony w funkcjach podrzędnych.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|— Dla funkcji, czas przeznaczony na wywołania funkcji. Obejmuje to czas przeznaczony na funkcje podrzędne, ale nie obejmuje wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla modułu, okres, w których co najmniej jedną funkcję w module był w stosie wywołań, z wyłączeniem czas przeznaczony na wywołań do systemu operacyjnego.|  
|**% Całkowity czas aplikacji**|Procent całkowitej upłynął całkowity czas uruchomienia profilowania przeznaczony na całkowity czas aplikacji tego modułu lub funkcji.|  
|**Średni całkowity czas aplikacji**|— Dla funkcji aplikacji średni całkowity czas wywołania tej funkcji.<br />— Dla modułu całkowity czas aplikacji średnią wszystkich wywołań funkcji w module.|  
|**Maksymalny całkowity czas aplikacji**|— Dla funkcji aplikacji maksymalny całkowity czas wywołania tej funkcji.<br />— Dla modułu aplikacji maksymalny całkowity czas wszystkich wywołań funkcji w module.|  
|**Minimalny całkowity czas aplikacji**|— Dla funkcji całkowity czas aplikacji minimalna wywołania do tego modułu lub funkcji.<br />— Dla modułu całkowity czas aplikacji minimalna wszystkich wywołań funkcji w module.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłącznego aplikacji  
 Wartości wyłącznego aplikacji wskazują czas przeznaczony na modułu lub funkcji z wyłączeniem czas przeznaczony na funkcje podrzędne. Wskazany czas także wyklucza wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|— Dla funkcji własny czas aplikacji całkowita liczba wywołań tej funkcji.<br />— Dla modułu własny czas łączny aplikacji wszystkie wywołania funkcji w module.|  
|**% Własny czas aplikacji**|Procent całkowitej upłynął własny czas przebiegu profilowania, przeznaczony na własny czas aplikacji tego modułu lub funkcji.|  
|**Średni własny czas aplikacji**|— Dla funkcji aplikacji średni własny czas wywołania tej funkcji.<br />— Dla modułu własny czas aplikacji średnią wszystkich wywołań funkcji w module.|  
|**Maksymalny własny czas aplikacji**|— Dla funkcji aplikacji maksymalny własny czas wywołania tej funkcji.<br />— Dla modułu własny czas aplikacji maksymalną wszystkich wywołań funkcji w module.|  
|**Minimalny własny czas aplikacji**|— Dla funkcji własny czas aplikacji minimalna wywołania do tego modułu lub funkcji.<br />— Dla modułu własny czas aplikacji minimalna wszystkich wywołań funkcji w module.|  
  
## <a name="see-also"></a>Zobacz też  
 [Moduły View - próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Widok modułów](../profiling/modules-view-instrumentation-data.md)   
 [Widok modułów](../profiling/modules-view-sampling-data.md)