---
title: Widok wywołujący wywoływany - dane Instrumentacji pamięci NET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6005bfcd4c69220c26929a8ad57f0e37923f388c
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265504"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Widok wywołujący/wywoływany - Instrumentacja pamięci .NET danych
Widok wywołujący/wywoływany danych, który został zebrany przy użyciu metody Instrumentacji profilowania pamięci .NET Wyświetla alokacji i danych o chronometrażu dla wybranej funkcji i funkcji nadrzędne i podrzędne tych wybranych funkcji. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** są wyświetlane w środkowym siatki i zawiera informacje na temat wybranej funkcji profilowania pamięci. Wartości obejmują wszystkie próbki wywołania funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** jest wyświetlany w górnym siatki i zawiera ilość wartość wybranych funkcji (bieżącego), który został wygenerowany przez wywołania funkcji wywołującego (nadrzędnego).  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w siatce dolnej i zawiera profilowania dane dla funkcji wywoływanych (podrzędny) wybranej funkcji podczas wywoływania funkcji podrzędnych przez bieżącą funkcję pamięci.  
  
 Kliknij dwukrotnie wywołujący lub wywoływany funkcja wiersza aby wiersz bieżącej funkcji.  
  
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
|**Identyfikator procesu**|Identyfikator procesu przebiegu profilowania.|  
|**Nazwa procesu**|Nazwa przypisana do procesu.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji z powodu instrumentacji. Narzut sondy odjęciu z wszystkich wyłącznego razy.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych z powodu instrumentacji. Narzut sondy odjęciu z zawsze włącznie.|  
|**Typ**|Kontekst funkcji:<br /><br /> **0** -bieżącą funkcję<br /><br /> **1** — funkcja, która wywołuje bieżącą funkcję<br /><br /> **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Nazwa głównej funkcji**|Nazwa bieżącej funkcji. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
  
## <a name="net-memory-allocation-values"></a>Wartości alokacji pamięci .NET  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Wyłączny alokacji**|— Dla bieżącej funkcji, liczbę obiektów, które zostały utworzone podczas wykonywania kodu funkcji w treści funkcji (oznacza to, gdy funkcja znajdowała się w górnej części stosu wywołań). Liczba nie obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.<br />— Dla funkcji wywołującego, liczbę wyłącznego alokacji bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji wywołującego.<br />— Dla funkcji wywoływany, liczbę obiektów, które zostały utworzone przez wystąpień tej funkcji, które zostały wywołane przez bieżącą funkcję. Ta liczba nie obejmuje obiekty, które zostały utworzone przez funkcje, które zostały wywołane przez funkcję wywoływany.|  
|**% Wyłącznego alokacji**|Procent wszystkich obiektów, które zostały utworzone w przebiegu, który profilowania były wyłącznego alokacji tej funkcji.|  
|**Alokacje włącznie**|— Dla bieżącej funkcji, liczba obiektów przydzielonych za pomocą funkcji w przebiegu profilowania. Liczba obejmuje obiekty, które zostały utworzone w funkcjach wywoływanych, które zostały wywołane przez funkcję.<br />— Dla funkcji wywołującego, liczba przydziałów włącznie bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji wywołującego.<br />— Dla funkcji wywoływany, liczbę obiektów, które zostały przydzielone wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba obejmuje przydziałów wykonanych przez funkcje, które zostały wywołane przez tę funkcję wywoływany.|  
|**% Alokacji włącznie**|Procent wszystkich obiektów, które zostały utworzone w przebiegu, który profilowania były alokacji włącznie tej funkcji.|  
|**Wyłączny bajtów**|— Dla funkcji bieżąca liczba bajtów pamięci, które zostały przydzielone przez funkcję w przebiegu profilowania. Liczba nie obejmuje pamięci, która została przydzielona w funkcjach wywoływanych, które zostały wywołane przez funkcję.<br />— Dla funkcji wywołującego liczba bajtów wyłącznego bieżącej funkcji, które zostały wygenerowane z wywołań przez tę funkcję wywołującego.<br />— Dla funkcji wywoływany, liczba bajtów, które zostały przydzielone wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba nie obejmuje bajtów przydzielonych przez funkcje, które zostały wywołane przez funkcję wywoływany.|  
|**% Wyłącznego bajtów**|Procent wszystkich bajtów pamięci przydzielone w przebiegu, który profilowania były wyłącznego alokacji tej funkcji.|  
|**Bajty włącznie**|— Dla funkcji bieżąca liczba bajtów w pamięci, które zostały przydzielone przez funkcję w przebiegu profilowania. Liczba obejmuje pamięci, która została przydzielona w funkcjach wywoływanych, które zostały wywołane przez funkcję.<br />— Dla funkcji wywołującego, liczba bajtów włącznie wystąpienia bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji wywołującego.<br />— Dla funkcji wywoływany, liczba bajtów, które zostały przydzielone wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba obejmuje bajtów przydzielonych przez funkcje, które zostały wywołane przez tę funkcję wywoływany.|  
|**% Bajtów włącznie**|Procent wszystkich bajtów pamięci przydzielone w przebiegu, który profilowania były alokacji włącznie tej funkcji.|  
  
## <a name="elapsed-inclusive-values"></a>Czas wartości włącznie  
 Czas włącznie wartości wskazują czas, który został funkcji w stosie wywołań. Czas obejmuje czas przeznaczony w funkcji podrzędnych i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|— Dla bieżącej funkcji czas przeznaczony w funkcji. Wartość zawiera czas przeznaczony w funkcji podrzędnych i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującego, który upłynął czas włącznie bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującego.<br />— Dla funkcji wywoływany czas przeznaczony na tym funkcji, który został wygenerowany przez wywołanie z bieżącej funkcji. Wartość zawiera czas przeznaczony w funkcji podrzędnych i wywołań systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.|  
|**% Całkowity czas, który upłynął**|Procent całkowitej upłynął całkowity czas uruchomienia profilowania przeznaczony na czas całkowity czas tej funkcji w tym kontekście.|  
|**Avg, który upłynął całkowity czas**|Średni całkowity czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Maksymalny czas, który upłynął włącznie**|Maksymalny całkowity czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Min, który upłynął całkowity czas**|Minimalny całkowity czas wywołania tej funkcji w tym kontekście, który upłynął.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wartości wyłączności  
 Czas wyłącznego wartości wskazują czas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Czas obejmuje czas w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czas przeznaczony na funkcje podrzędne.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Czas, który upłynął wyłączności**|— Dla bieżącej funkcji czas przeznaczony na wykonanie treści funkcji. Wartość nie obejmuje czas przeznaczony na funkcje podrzędne, ale zawiera wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującego, który upłynął czas wyłącznego bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującego.<br />— Dla funkcji wywoływany czas przeznaczony na tym funkcji, który został wygenerowany przez wywołanie z bieżącej funkcji. Wartość nie obejmuje czas przeznaczony na funkcje podrzędne funkcji wywoływany, ale zawiera wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.|  
|**% Wyłącznego czas, który upłynął**|Procent całkowitej czas własny czas profilowania wykonywany przeznaczony na całkowity czas własny czas tej funkcji w tym kontekście.|  
|**Śr. na wyłączność, który upłynął czas**|Średni własny czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Maksymalny czas, który upłynął wyłączności**|Maksymalny własny czas wywołania tej funkcji w tym kontekście, który upłynął.|  
|**Min na wyłączność, który upłynął czas**|Minimalny własny czas wywołania tej funkcji w tym kontekście, który upłynął.|  
  
## <a name="application-inclusive-values"></a>Wartości z wartościami granicznymi aplikacji  
 Wartości z wartościami granicznymi aplikacji wskazują czas, który został funkcji w stosie wywołań. Czas nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia, jednak zawierać czas przeznaczony w funkcjach podrzędnych.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|— Dla bieżącej funkcji czas przeznaczony na funkcji i jej funkcji podrzędnych. Wartość nie obejmuje czas przeznaczony na wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującego, ilość całkowity czas aplikacji bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującego.<br />— Dla funkcji wywoływany, czas przeznaczony na tej funkcji i jej funkcji podrzędnych został wygenerowany przez wywołania z bieżącej funkcji. Wartość nie obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.|  
|**% Całkowity czas aplikacji**|Procent czas łączny całkowity czas profilowania wykonywany przeznaczony na całkowity czas aplikacji całkowita tej funkcji w tym kontekście.|  
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji w tym kontekście.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłącznego aplikacji  
 Wartości wyłącznego aplikacji wskazują czas przeznaczony w funkcji z wyłączeniem czas przeznaczony na funkcje podrzędne. Wskazany czas nie obejmuje również czas spędzony incalls do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|— Dla bieżącej funkcji czas przeznaczony na wykonanie treści funkcji. Wartość nie obejmuje czas przeznaczony w funkcjach podrzędnych, ani obejmuje wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującego, ilość własny czas aplikacji bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującego.<br />— Dla funkcji wywoływany czas przeznaczony na tym funkcji, który został wygenerowany przez wywołanie z bieżącej funkcji. Wartość nie obejmuje czas przeznaczony w funkcjach podrzędnych funkcji wywoływanych ani obejmuje wywołań do systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.|  
|**% Własny czas aplikacji**|Procent całkowitej czas własny czas profilowania wykonywany przeznaczony na własny czas łączny aplikacji tej funkcji w tym kontekście.|  
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji w tym kontekście.|  
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji w tym kontekście.|  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok wywołujący/wywoływany - dane próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)   
 [Widok wywołujący/wywoływany - dane próbkowania](../profiling/caller-callee-view-sampling-data.md)