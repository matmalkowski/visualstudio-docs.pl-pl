---
title: "Widok modułów - dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft"
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
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 32eb0b4e34edde03cd455384d7b1c6d36e0365c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="modules-view---net-memory-sampling-data"></a>Widok modułów - dane próbkowania pamięci .NET
Widok modułów danych alokacji pamięci .NET, które są zbierane za pomocą metody pobierania próbek grupuje dane pamięci przez moduły, które zostały wykonane w przebiegu profilowania. Każdy moduł jest katalogiem głównym drzewa hierarchicznej. Funkcji modułu są wyświetlane poniżej tego węzła modułu.  
  
 Numery wierszy pliku źródłowego instrukcji, które przydzielić pamięci są wymienione poniżej tego węzła funkcji, a adresy instrukcji, które wykonują Alokacja są wymienione poniżej tego węzła wiersza. Wartości włącznie i wyłącznego zawsze są takie same dla wiersza danych i instrukcji.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa modułu, funkcji, numer wiersza lub adres instrukcji.|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka do modułu.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Alokacje włącznie**|— Dla funkcji, całkowita liczba obiektów, które zostały utworzone przez funkcję. Numer obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.<br />— Dla modułu wykonywania liczbę obiektów w przebiegu profilowania przydzielone podczas co najmniej jedną funkcję z modułu. Liczba obejmuje obiekty, które zostały utworzone w funkcje, które zostały wywołane przez funkcje modułu.<br />— Dla wiersza lub instrukcji, całkowita liczba obiektów, które zostały przydzielone wiersza lub instrukcji.|  
|**% Alokacji włącznie**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu, który profilowania były włącznie alokacji modułu, funkcji, wiersz lub instrukcji.|  
|**Wyłączny alokacji**|— Dla bieżącej funkcji, liczbę obiektów, które zostały utworzone, gdy funkcja została uruchomiona kodu treść funkcji (oznacza to, gdy funkcja znajdowała się w górnej części stosu wywołań). Liczba nie obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.<br />— Dla modułu sumę wyłącznego alokacje funkcji w module.<br />— Dla wiersza lub instrukcji, całkowita liczba obiektów, które zostały utworzone przez tego wiersza lub instrukcji.|  
|**% Wyłącznego alokacji**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu, który profilowania były wyłącznego alokacji modułu, funkcji, wiersz lub instrukcji.|  
|**Bajty włącznie**|— Dla funkcji, liczba bajtów, które zostały przyznane przez funkcję. Liczba zawiera bajtów przydzielonych w funkcje, które zostały wywołane przez tę funkcję.<br />— Dla modułu wykonywania liczba bajtów przydzielonych do uruchomienia profilowania przydzielone podczas co najmniej jedną funkcję z modułu. Liczba obejmuje obiekty, które zostały utworzone we wszystkich funkcji, które zostały wywołane przez funkcje modułu.<br />— Dla wiersza lub instrukcji, całkowita liczba obiektów, które zostały utworzone przez wiersz lub instrukcji.|  
|**% Bajtów włącznie**|Procent wszystkich bajtów przydzielonych w przebiegu, który profilowania były włącznie bajtów modułu, funkcji, wiersz lub instrukcji.|  
|**Wyłączny bajtów**|— Dla funkcji, całkowita liczba bajtów, które zostały przyznane przez funkcję. Liczba nie obejmuje bajtów przydzielonych w funkcje, które zostały wywołane przez tę funkcję.<br />— Dla modułu sumę wyłącznego bajtów, które zostały przydzielone funkcji w module.<br />— Dla wiersza lub instrukcji, całkowita liczba obiektów, które zostały przydzielonej przez ten wiersz lub instrukcji.|  
|**% Wyłącznego bajtów**|Procent wszystkich bajtów przydzielonych w przebiegu, który profilowania były wyłącznego bajtów modułu, funkcji, wiersz lub instrukcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok modułów - Instrumentacja](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Widok modułów](../profiling/modules-view-sampling-data.md)   
 [Widok modułów](../profiling/modules-view-instrumentation-data.md)