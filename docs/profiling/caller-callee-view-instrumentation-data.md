---
title: Widok wywołujący wywoływany - dane Instrumentacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f294e81b8ce38dd5661fa49aa71231d0daed30ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="callercallee-view---instrumentation-data"></a>Widok wywołujący/wywoływany - dane Instrumentacji
Widok wywołujący/wywoływany Wyświetla profilowania informacje o wybranej funkcji i jej funkcji nadrzędnej i podrzędnej w drzewie wywołań. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** jest wyświetlane w środkowym siatki i pokazuje profilowania informacji na temat wybranej funkcji. Wartości obejmują wszystkie wywołania funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** jest wyświetlany w górnym siatki i pokazuje profilowania informacje na temat funkcji wywołującego (nadrzędnego) wybranej funkcji. Wartości wskazuje ilość wartość bieżącą funkcję wygenerowana przez wywołania z tej funkcji wywołującego.  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w siatce dolnej i pokazuje profilowania informacji o wystąpieniach funkcji wywoływanych (podrzędny) wybranej funkcji. Wartości oznaczają tylko czas przeznaczony w funkcji podrzędnych wywołanego przez bieżącą funkcję.  
  
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
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, które zostało spowodowane przez instrumentacji. Narzut sondy odjęciu z wszystkich wyłącznego razy.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych powodujący instrumentacji. Narzut sondy odjęciu z zawsze włącznie.|  
|**Typ**|Kontekst funkcji:<br /><br /> **0** -bieżącą funkcję<br /><br /> **1** — funkcja, która wywołuje bieżącą funkcję<br /><br /> **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Nazwa głównej funkcji**|Nazwa bieżącej funkcji. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
  
## <a name="elapsed-inclusive-values"></a>Czas wartości włącznie  
 Czas włącznie wartości wskazują czas, który został funkcji w stosie wywołań. Czas obejmuje czas przeznaczony na funkcje podrzędne i czas przeznaczony na wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|— Dla bieżącej funkcji czas przeznaczony w funkcji. Wartość zawiera czas przeznaczony w funkcji podrzędnych i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującego, który upłynął czas włącznie bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującego.<br />— Dla funkcji wywoływany, czas przeznaczony na wystąpień tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość zawiera czas przeznaczony w podrzędnych funkcji wywołującej i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.|  
|**% Całkowity czas, który upłynął**|Procent całkowitej upłynął całkowity czas uruchomienia profilowania przeznaczony na czas całkowity czas tej funkcji w tym kontekście.|  
|**Avg, który upłynął całkowity czas**|Średni całkowity czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Maksymalny czas, który upłynął włącznie**|Maksymalny całkowity czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Min, który upłynął całkowity czas**|Minimalny całkowity czas wywołania tej funkcji w tym kontekście, który upłynął.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wartości wyłączności  
 Czas wyłącznego wartości wskazują czas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Czas obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czas przeznaczony na funkcje podrzędne.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Czas, który upłynął wyłączności**|— Dla bieżącej funkcji czas przeznaczony na bezpośrednie wykonywanie funkcji. Wartość zawiera czas przeznaczony w funkcji podrzędnych i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującego, który upłynął czas wyłącznego bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującego.<br />— Dla funkcji wywoływany, czas przeznaczony na wystąpień tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość nie obejmuje czas przeznaczony na funkcje podrzędne funkcji wywoływany, ale zawiera wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.|  
|**% Wyłącznego czas, który upłynął**|Procent całkowitej czas własny czas profilowania wykonywany przeznaczony na całkowity czas własny czas tej funkcji w tym kontekście.|  
|**Śr. na wyłączność, który upłynął czas**|Średni własny czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Maksymalny czas, który upłynął wyłączności**|Maksymalny własny czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Min na wyłączność, który upłynął czas**|Minimalny własny czas wywołania tej funkcji w tym kontekście, który upłynął.|  
  
## <a name="application-inclusive-values"></a>Wartości z wartościami granicznymi aplikacji  
 Wartości z wartościami granicznymi aplikacji wskazują czas, który został funkcji w stosie wywołań. Czas nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, jednak zawierać czas przeznaczony w funkcjach podrzędnych.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|— Dla bieżącej funkcji czas przeznaczony na funkcji i jej funkcji podrzędnych. Wartość nie obejmuje czas przeznaczony na wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującego, ilość całkowity czas aplikacji bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującego.<br />— Dla funkcji wywoływany, czas przeznaczony na wystąpień tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość zawiera czas przeznaczony w funkcjach podrzędnych funkcji wywoływany, ale nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.|  
|**% Całkowity czas aplikacji**|Procent czas łączny całkowity czas profilowania wykonywany przeznaczony na całkowity czas aplikacji całkowita tej funkcji w tym kontekście.|  
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji w tym kontekście.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłącznego aplikacji  
 Wartości wyłącznego aplikacji wskazują czas przeznaczony w funkcji. Obejmuje to czas przeznaczony na funkcje podrzędne, a także wyklucza wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|— Dla bieżącej funkcji czas przeznaczony na bezpośrednie wykonywanie funkcji. Wartość nie obejmuje czas przeznaczony w funkcjach podrzędnych, ani obejmuje wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującego, ilość własny czas aplikacji bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującego.<br />— Dla funkcji wywoływany, czas przeznaczony na wystąpień tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość nie obejmuje czas przeznaczony w funkcjach podrzędnych funkcji wywoływanych ani obejmuje wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.|  
|**% Własny czas aplikacji**|Procent całkowitej czas własny czas profilowania wykonywany przeznaczony na własny czas łączny aplikacji tej funkcji w tym kontekście.|  
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji w tym kontekście.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Obiekt wywołujący / wywoływany widok - dane próbkowania](../profiling/caller-callee-view-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji NET pamięci](../profiling/caller-callee-view-net-memory-instrumentation-data.md)