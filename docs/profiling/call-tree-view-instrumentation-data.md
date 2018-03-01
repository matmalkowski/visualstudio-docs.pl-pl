---
title: "Widok drzewa wywołań - dane Instrumentacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d528c4161b2fcdf61a7357e74e64caa124f995de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="call-tree-view---instrumentation-data"></a>Widok drzewa wywołań - dane Instrumentacji
Wartości dla funkcji w drzewie wywołań wskazują godzinę dla wystąpienia funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpień funkcji łączny całkowity czas, który upłynął, wszystkich funkcji w przebiegu profilowania.  
  
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
|**Nazwa procesu**|Nazwa przypisana do procesu.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, które zostało spowodowane przez instrumentacji. Narzut sondy odjęciu z wszystkich wyłącznego razy.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych powodujący instrumentacji. Narzut sondy odjęciu z zawsze włącznie.|  
|**Poziom**|Głębokość funkcji w drzewie wywołań. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
  
## <a name="elapsed-inclusive-values"></a>Czas wartości włącznie  
 Czas włącznie wartości wskazują godzinę na stosie wywołań wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Czas obejmuje czas przeznaczony w funkcji podrzędne, które zostały wywołane przez funkcję i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|Łączny całkowity czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**% Całkowity czas, który upłynął**|Procent czas łączny całkowity czas profilowania wykonywany przeznaczony na całkowity czas całkowity czas tej funkcji w tym kontekście.|  
|**Avg, który upłynął całkowity czas**|Średni całkowity czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Maksymalny czas, który upłynął włącznie**|Maksymalny całkowity czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Min, który upłynął całkowity czas**|Minimalny całkowity czas wywołania tej funkcji w tym kontekście, który upłynął.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wartości wyłączności  
 Czas wyłącznego wartości wskazują godzinę wystąpienia funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań zostały wykonywanie kodu w treści funkcji; oznacza to, gdy funkcja znajdowała się w górnej części stosu wywołań. Czas obejmuje czas w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia. Jednak czas nie obejmuje czas przeznaczony w funkcjach podrzędne, które zostały wywołane przez funkcję.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Czas, który upłynął wyłączności**|Suma upłynął własny czas wywołania tej funkcji w tym kontekście.|  
|**% Wyłącznego czas, który upłynął**|Procent całkowitej czas własny czas profilowania wykonywany przeznaczony na całkowity czas własny czas tej funkcji w tym kontekście.|  
|**Śr. na wyłączność, który upłynął czas**|Średni własny czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Maksymalny czas, który upłynął wyłączności**|Maksymalny własny czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Min na wyłączność, który upłynął czas**|Minimalny własny czas wywołania tej funkcji w tym kontekście, który upłynął.|  
  
## <a name="application-inclusive-values"></a>Wartości z wartościami granicznymi aplikacji  
 Wartości z wartościami granicznymi aplikacji wskazują godzinę, o której zostały wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań w stosie wywołań. Czas nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, jednak czas zawiera czas przeznaczony w funkcjach podrzędne, które zostały wywołane przez funkcję.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|Łączny całkowity czas aplikacji wszystkie wywołania tej funkcji w tym kontekście.|  
|**% Całkowity czas aplikacji**|Procent czas łączny całkowity czas profilowania wykonywany przeznaczony na całkowity czas aplikacji całkowita tej funkcji w tym kontekście.|  
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji w tym kontekście.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłącznego aplikacji  
 Wartości wyłącznego aplikacji wskazują godzinę, że wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań bezpośrednio wykonywały kod w treści funkcji; oznacza to, gdy funkcja znajdowała się w górnej części stosu wywołań. Czas nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia. On również nie obejmuje czas przeznaczony w funkcjach podrzędne, które zostały wywołane przez funkcję.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|Całkowita liczba własny czas aplikacji wszystkie wywołania tej funkcji w tym kontekście.|  
|**% Własny czas aplikacji**|Procent całkowitej czas własny czas profilowania wykonywany przeznaczony na własny czas łączny aplikacji tej funkcji w tym kontekście.|  
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji w tym kontekście.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)   
 [Widok drzewa wywołań - Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Widok drzewa wywołań - próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)