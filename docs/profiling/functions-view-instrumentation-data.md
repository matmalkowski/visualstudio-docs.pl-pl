---
title: Widok funkcji - dane Instrumentacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7787e974b093156b27b2ace4353e94db05063d7d
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238228"
---
# <a name="functions-view---instrumentation-data"></a>Widok funkcji - dane Instrumentacji
Widoku raportu funkcji wyświetla dane profilowania według nazwy funkcji.  
  
## <a name="general"></a>Ogólne  
 Ogólne kolumn zidentyfikowanie funkcji w wierszu widoku.  
  
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
|**Nazwa procesu**|Nazwa procesu.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, która jest spowodowany przez instrumentacji. Nie obejmuje obciążenie w funkcjach, które zostały wywołane przez funkcję. Narzut sondy odjęciu z wszystkich wyłącznego razy.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych spowodowany przez instrumentacji. Posiada obciążenie w funkcjach, które zostały wywołane przez funkcję. Narzut sondy odjęciu z zawsze włącznie.|  
  
## <a name="elapsed-inclusive-values"></a>Czas wartości włącznie  
 Czas włącznie wartości wskazują czas, który został funkcji w stosie wywołań. Czas obejmują czas przeznaczony w funkcjach, które zostały wywołane przez funkcję i czas przeznaczony na wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|Łączny całkowity czas wywołania tej funkcji, który upłynął.|  
|**% Całkowity czas, który upłynął**|Procent całkowitej upłynął całkowity czas uruchomienia profilowania przeznaczony na czas całkowity czas tej funkcji.|  
|**Avg, który upłynął całkowity czas**|Średni całkowity czas wywołanie tej funkcji, który upłynął.|  
|**Maksymalny czas, który upłynął włącznie**|Maksymalny całkowity czas wywołanie tej funkcji, który upłynął.|  
|**Min, który upłynął całkowity czas**|Minimalny całkowity czas wywołanie tej funkcji, który upłynął.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wartości wyłączności  
 Czas wyłącznego wartości wskazują czasu, że funkcja została wykonywanie kodu w treści funkcji, oznacza to, gdy funkcja znajdowała się w górnej części stosu wywołań. Czas zawiera czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, jednak nie obejmuje czas przeznaczony na funkcje, które zostały wywołane przez funkcję.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Czas, który upłynął wyłączności**|Suma upłynął własny czas wywołania tej funkcji.|  
|**% Wyłącznego czas, który upłynął**|Procent całkowitej upłynął własny czas przebiegu profilowania, przeznaczony na całkowity czas własny czas tej funkcji.|  
|**Śr. na wyłączność, który upłynął czas**|Średni własny czas wywołanie tej funkcji, który upłynął.|  
|**Maksymalny czas, który upłynął wyłączności**|Maksymalny własny czas wywołanie tej funkcji, który upłynął.|  
|**Min na wyłączność, który upłynął czas**|Minimalny własny czas wywołanie tej funkcji, który upłynął.|  
  
## <a name="application-inclusive-values"></a>Wartości z wartościami granicznymi aplikacji  
 Wartości z wartościami granicznymi aplikacji wskazują czas, który został funkcji w stosie wywołań. Czas nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, jednak zawierać czas przeznaczony w funkcjach, które zostały wywołane przez funkcję.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|Łączny całkowity czas aplikacji wszystkie wywołania tej funkcji.|  
|**% Całkowity czas aplikacji**|Procent całkowitej upłynął całkowity czas uruchomienia profilowania przeznaczony na całkowity czas aplikacji całkowita tej funkcji.|  
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji.|  
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji.|  
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłącznego aplikacji  
 Wartości wyłącznego aplikacji wskazują czas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Czas nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, i nie obejmuje czas przeznaczony na funkcje, które zostały wywołane przez funkcję.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|Całkowita liczba własny czas aplikacji wszystkie wywołania tej funkcji.|  
|**% Własny czas aplikacji**|Procent całkowitej upłynął własny czas przebiegu profilowania, przeznaczony na własny czas łączny aplikacji tej funkcji.|  
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji.|  
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji.|  
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji.|  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok funkcji](../profiling/functions-view-sampling-data.md)   
 [Widok funkcji - próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Widok funkcji - Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)