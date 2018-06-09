---
title: Widok funkcji - dane Instrumentacji pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d48393a2d160e3691069a4b5f86dd814b63d935d
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237685"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Widok funkcji - dane Instrumentacji pamięci .NET
Widok funkcji .NET pamięci alokacji profilowania danych, które zostały zebrane przy użyciu metody Instrumentacji zawiera listę funkcji, które przydzielonej pamięci podczas przebiegu profilowania. Wiersz funkcji raportów, rozmiaru i liczby przydziałów i danych o chronometrażu dla funkcji.  
  
## <a name="general"></a>Ogólne  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Adres funkcji**|Adres funkcji.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Liczba wywołań**|Całkowita liczba wywołań tej funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję tej funkcji.|  
|**Nazwa modułu**|Nazwa modułu zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji z powodu instrumentacji. Narzut sondy odjęciu z wszystkich wyłącznego razy.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych z powodu instrumentacji. Narzut sondy odjęciu z zawsze włącznie.|  
  
## <a name="net-memory-values"></a>Wartości pamięci .NET  
 Wraz z wartościami granicznymi wartości pamięci .NET funkcji wskazuje liczbę (alokacji) i rozmiar (w bajtach) obiektów, które zostały utworzone przez funkcji i jej funkcji podrzędnych.  
  
 Wartości wyłącznego pamięci wskazują liczby i rozmiaru obiektów, które zostały utworzone przez funkcję, a nie przez jej funkcji podrzędnych.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Alokacje włącznie**|Całkowita liczba obiektów, które zostały utworzone w tej funkcji i funkcji, które zostały wywołane przez tę funkcję.|  
|**% Alokacji włącznie**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu, który profilowania były alokacji włącznie tej funkcji.|  
|**Wyłączny alokacji**|Całkowita liczba obiektów, które zostały utworzone podczas wykonywania kodu funkcji w treści funkcji. Ta liczba nie obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.|  
|**% Wyłącznego alokacji**|Procent wszystkich obiektów, które zostały utworzone w przebiegu, który profilowania były wyłącznego alokacji tej funkcji.|  
|**Bajty włącznie**|Liczba bajtów pamięci przydzielonych w tej funkcji i funkcji, które zostały wywołane przez tę funkcję.|  
|**% Bajtów włącznie**|Procent wszystkich bajtów pamięci przydzielone w przebiegu, który profilowania były bajtów włącznie tej funkcji.|  
|**Wyłączny bajtów**|Liczba bajtów pamięci, które zostały przydzielone przez tę funkcję, ale nie przez funkcje, które zostały wywołane przez tę funkcję.|  
|**% Wyłącznego bajtów**|Procent wszystkich bajtów pamięci przydzielone w przebiegu, który profilowania były wyłącznego bajtów tej funkcji.|  
  
## <a name="elapsed-inclusive-values"></a>Czas wartości włącznie  
 Czas włącznie wartości wskazują czas, który został funkcji w stosie wywołań. Czas obejmuje czas przeznaczony w funkcji podrzędnych i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|Łączny całkowity czas wywołania tej funkcji, który upłynął.|  
|**% Całkowity czas, który upłynął**|Procent całkowitej upłynął całkowity czas uruchomienia profilowania przeznaczony na czas całkowity czas tej funkcji.|  
|**Avg, który upłynął całkowity czas**|Średni całkowity czas wywołanie tej funkcji, który upłynął.|  
|**Maksymalny czas, który upłynął włącznie**|Maksymalny całkowity czas wywołanie tej funkcji, który upłynął.|  
|**Min, który upłynął całkowity czas**|Minimalny całkowity czas wywołanie tej funkcji, który upłynął.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wartości wyłączności  
 Czas wyłącznego wartości wskazują czas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Czas obejmuje czas w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czas przeznaczony na funkcje podrzędne.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Czas, który upłynął wyłączności**|Suma upłynął własny czas wywołania tej funkcji.|  
|**% Wyłącznego czas, który upłynął**|Procent całkowitej upłynął własny czas przebiegu profilowania, przeznaczony na całkowity czas własny czas tej funkcji.|  
|**Śr. na wyłączność, który upłynął czas**|Średni własny czas wywołanie tej funkcji, który upłynął.|  
|**Maksymalny czas, który upłynął wyłączności**|Maksymalny własny czas wywołanie tej funkcji, który upłynął.|  
|**Min na wyłączność, który upłynął czas**|Minimalny własny czas wywołanie tej funkcji, który upłynął.|  
  
## <a name="application-inclusive-values"></a>Wartości z wartościami granicznymi aplikacji  
 Wartości z wartościami granicznymi aplikacji wskazują czas, który został funkcji w stosie wywołań. Czas nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, jednak zawierać czas przeznaczony w funkcjach podrzędnych.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|Łączny całkowity czas aplikacji wszystkie wywołania tej funkcji.|  
|**% Całkowity czas aplikacji**|Procent całkowitej upłynął całkowity czas uruchomienia profilowania przeznaczony na całkowity czas aplikacji całkowita tej funkcji.|  
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji.|  
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji.|  
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłącznego aplikacji  
 Wartości wyłącznego aplikacji wskazują czas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Czas nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, ani obejmuje czas przeznaczony na funkcje podrzędne.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|Całkowita liczba własny czas aplikacji wszystkie wywołania tej funkcji.|  
|**% Własny czas aplikacji**|Procent całkowitej upłynął własny czas przebiegu profilowania, przeznaczony na własny czas łączny aplikacji tej funkcji.|  
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji.|  
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji.|  
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji.|  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok funkcji - próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Widok funkcji](../profiling/functions-view-instrumentation-data.md)   
 [Widok funkcji](../profiling/functions-view-sampling-data.md)