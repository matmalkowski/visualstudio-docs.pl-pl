---
title: Widok modułów - dane Instrumentacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c849971da7681322b15365bc0d59ce8b3529f508
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256113"
---
# <a name="modules-view---instrumentation-data"></a>Widok modułów - dane Instrumentacji
Widok modułów przedstawia dane wydajności, które są grupowane według modułów, które znajdowały się w danych profilowania. Funkcji modułu są wyświetlane poniżej węzła modułu.  
  
## <a name="general"></a>Ogólne  
 Ogólne kolumn zidentyfikowanie funkcji w wierszu widoku.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa modułu lub funkcji.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Liczba wywołań**|Całkowita liczba połączeń, które zostały wprowadzone do tego modułu lub funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa modułu**|Nazwa modułu zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu, w którym wykonywania modułu lub funkcji.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji lub modułu z powodu instrumentacji.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji lub modułu i jej funkcji podrzędnych z powodu instrumentacji.|  
  
## <a name="elapsed-inclusive-values"></a>Czas wartości włącznie  
 Czas włącznie wartości wskazują czas, który został funkcji w stosie wywołań. Czas obejmuje czas przeznaczony w funkcji podrzędnych i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|— Dla funkcji, czas przeznaczony w funkcji. W tym czas przeznaczony w funkcji podrzędnych i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla modułu, czasu, w których co najmniej jedną funkcję w module był w stosie wywołań.|  
|**% Całkowity czas, który upłynął**|Procent czas łączny całkowity czas profilowania wykonywany przeznaczony na czas łączny całkowity czas tego modułu lub funkcji.|  
|**Avg, który upłynął całkowity czas**|— Dla funkcji średnią upłynął całkowity czas wywołania tej funkcji.<br />— Dla modułu średnia upłynął całkowity czas wszystkie wywołania funkcji w module.|  
|**Maksymalny czas, który upłynął włącznie**|— Dla funkcji maksymalną upłynął całkowity czas wywołania tej funkcji.<br />— Dla modułu maksymalna upłynął całkowity czas wszystkie wywołania funkcji w module.|  
|**Min, który upłynął całkowity czas**|— Dla funkcji minimalnym upłynął całkowity czas wywołanie tego modułu lub funkcji.<br />— Dla modułu minimalnym upłynął całkowity czas wszystkie wywołania funkcji w module.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wartości wyłączności  
 Czas wyłącznego wartości wskazują czas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Czas obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czas przeznaczony na funkcje podrzędne.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Czas, który upłynął wyłączności**|— Dla funkcji, czas przeznaczony na modułu lub funkcji. Zawiera wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czas przeznaczony na funkcje podrzędne.<br />— Dla modułu sumę upłynął wyłącznego razy funkcji w module.|  
|**% Wyłącznego czas, który upłynął**|Procent całkowitej czas własny czas profilowania wykonywany przeznaczony na całkowity czas własny czas tego modułu lub funkcji.|  
|**Śr. na wyłączność, który upłynął czas**|— Dla funkcji średnią upłynął własny czas wywołania tej funkcji.<br />— Dla modułu średnia upłynął własny czas wszystkie wywołania funkcji w module.|  
|**Maksymalny czas, który upłynął wyłączności**|— Dla funkcji maksymalną upłynął własny czas wywołania tej funkcji.<br />— Dla modułu maksymalna upłynął własny czas wszystkie wywołania funkcji w module.|  
|**Min na wyłączność, który upłynął czas**|— Dla funkcji minimalnym upłynął własny czas wywołanie tego modułu lub funkcji.<br />— Dla modułu minimalnym upłynął własny czas wszystkie wywołania funkcji w module.|  
  
## <a name="application-inclusive-values"></a>Wartości z wartościami granicznymi aplikacji  
 Wartości z wartościami granicznymi aplikacji wskazują czas, który został funkcji w stosie wywołań. Czas nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia. Jednakże czas obejmuje czas przeznaczony w funkcjach podrzędnych.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|— Dla funkcji, czas przeznaczony na wywołania funkcji. Obejmuje to czas przeznaczony na funkcje podrzędne, ale nie obejmuje wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla modułu, czasu, w których co najmniej jedną funkcję w module był w stosie wywołań. Obejmuje to czas przeznaczony na wywołań do systemu operacyjnego.|  
|**% Całkowity czas aplikacji**|Procent całkowitej upłynął całkowity czas uruchomienia profilowania przeznaczony na całkowity czas aplikacji tego modułu lub funkcji.|  
|**Średni całkowity czas aplikacji**|— Dla funkcji aplikacji średni całkowity czas wywołania tej funkcji.<br />— Dla modułu całkowity czas aplikacji średnią wszystkich wywołań funkcji w module.|  
|**Maksymalny całkowity czas aplikacji**|— Dla funkcji aplikacji maksymalny całkowity czas wywołania tej funkcji.<br />— Dla modułu aplikacji maksymalny całkowity czas wszystkich wywołań funkcji w module.|  
|**Minimalny całkowity czas aplikacji**|— Dla funkcji całkowity czas aplikacji minimalna wywołania do tego modułu lub funkcji.<br />— Dla modułu całkowity czas aplikacji minimalna wszystkich wywołań funkcji w module.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłącznego aplikacji  
 Wartości wyłącznego aplikacji wskazują czas przeznaczony na modułu lub funkcji. Obejmuje to czas przeznaczony na funkcje podrzędne, a także wyklucza wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|Całkowita liczba własny czas aplikacji wszystkie wywołania tego modułu lub tej funkcji.|  
|**% Własny czas aplikacji**|Procent całkowitej upłynął własny czas przebiegu profilowania, przeznaczony na własny czas aplikacji tego modułu lub funkcji.|  
|**Średni własny czas aplikacji**|— Dla funkcji aplikacji średni własny czas wywołania tej funkcji.<br />— Dla modułu własny czas aplikacji średnią wszystkich wywołań funkcji w module.|  
|**Maksymalny własny czas aplikacji**|— Dla funkcji aplikacji maksymalny własny czas wywołania tej funkcji.<br />— Dla modułu własny czas aplikacji maksymalną wszystkich wywołań funkcji w module.|  
|**Minimalny własny czas aplikacji**|— Dla funkcji własny czas aplikacji minimalna wywołania do tego modułu lub funkcji.<br />— Dla modułu własny czas aplikacji minimalna wszystkich wywołań funkcji w module.|  
  
## <a name="see-also"></a>Zobacz także  
 [Widok modułów](../profiling/modules-view-sampling-data.md)   
 [Widok modułów - Instrumentacja](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Moduły View - próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)