---
title: "Obiekt wywołujący — widok wywoływany - dane Kontencji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 47e4f57ffac71d6fb4f1c3e8cd8176c80d9f002a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="caller--callee-view----contention-data"></a>Obiekt wywołujący / wywoływany widok - dane Kontencji
Widok wywołujący/wywoływany Wyświetla informacje rywalizacji o wybranej funkcji i jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** są wyświetlane w środkowym siatki i zawiera informacje rywalizacji dla wybranych funkcji. Wartości obejmują wszystkie blokujące rywalizacji dla funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** jest wyświetlany w górnym siatki i zawiera funkcje z wartościami wybranej funkcji (bieżącego) poszczególnych wkładów wywołującego (nadrzędnego).  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w siatce dolnej i zawiera informacje rywalizacji o wywoływany (podrzędny) funkcje wybranej funkcji podczas wywoływania funkcji podrzędnych przez bieżącą funkcję.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Typ**|Kontekst funkcji:<br /><br /> -   **0** -bieżącą funkcję<br />-   **1** — funkcja, która wywołuje bieżącą funkcję<br />-   **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Wyłączny czasu blokowania**|— Dla bieżącej funkcji czas, jaki ta funkcja została zablokowana wykonywanie kodu w treści funkcji. Czas blokowania w funkcjach wywoływanych przez funkcję nie jest włączony.<br />— Dla funkcji wywołującego, część własny czas zablokowanych bieżącej funkcji, który wystąpił podczas tej funkcji wywołały bieżącą funkcję.<br />— Dla funkcji wywoływany, czas, jaki ta funkcja została zablokowana wykonywanie własnego kodu, gdy ta funkcja została wywołana przez bieżącą funkcję. Czas blokowania w funkcjach podrzędnych wywoływanych przez funkcję wywoływanego nie jest włączony.|  
|**% Wyłącznego czasu blokowania**|Procent wszystkich czas blokowania w przebiegu profilowania, który był własny czas zablokowanych dla tej funkcji w tym kontekście.|  
|**Wyłączny rywalizacji**|— Dla bieżącego funkcji, ile razy tej funkcji została zablokowana wykonywanie kodu w treści funkcji. Rywalizacji, które wystąpiły w funkcjach, które zostały wywołane przez funkcję nie są uwzględniane.<br />— Dla funkcji wywołującego, liczba rywalizacji wyłącznego bieżącej funkcji, który wystąpił podczas tej funkcji wywołały bieżącą funkcję.<br />— Dla funkcji wywoływany, ile razy tej funkcji został zablokowany w treści funkcji wykonywanie kodu, gdy ta funkcja została wywołana przez bieżącą funkcję. Rywalizacji, które wystąpiły w funkcjach wywoływanych przez funkcję wywoływanego nie są uwzględniane.|  
|**% Wyłącznego rywalizacji**|Wartość procentowa rywalizacji wszystkie, w którym profilowania były wyłącznego rywalizacji dla tej funkcji w tym kontekście.|  
|**Adres funkcji**|Adres funkcji lub token.|  
|**Nazwa funkcji**|Pełna nazwa funkcji.|  
|**Całkowity czas blokowania**|— Dla bieżącej funkcji podczas tej funkcji lub jednej z funkcji, które zostały wywołane przez tę funkcję zostało zablokowane z wykonywania. Czas blokowania w funkcje, które zostały wywołane przez bieżącą funkcję jest dołączony.<br />— Dla funkcji wywołującego część z wartościami granicznymi zablokowane czasu bieżącej funkcji, który wystąpił podczas tej funkcji wywołały bieżącą funkcję.<br />— Dla funkcji wywoływanych funkcji tej funkcji lub jednej z funkcji, które została wywołana przy użyciu funkcji została zablokowana wykonywanie, gdy ta funkcja została wywołana przez bieżący czas. Czas blokowania w funkcje, które zostały wywołane przez funkcję wywoływany jest dołączony.|  
|**Całkowity czas blokowania %**|Procent wszystkich czas blokowania w przebiegu profilowania, która była całkowity czas blokowania dla tej funkcji w tym kontekście.|  
|**Wraz z wartościami granicznymi rywalizacji**|— Dla bieżącej funkcji liczbę tej funkcji lub jednej z funkcji, które zostały wywołane przez funkcję zostało zablokowane z wykonywania. Uwzględniono rywalizacji, które wystąpiły w funkcjach, które zostały wywołane przez funkcję.<br />— Dla funkcji wywołującego, liczba rywalizacji włącznie z bieżącej funkcji, który wystąpił podczas tej funkcji wywołały bieżącą funkcję.<br />— Dla funkcji wywoływany, ile razy tej funkcji lub jednej z funkcji, które zostały wywołane przez funkcję zostało zablokowane wykonywanie, gdy ta funkcja została wywołana przez bieżącą funkcję. Rywalizacji, które wystąpiły w funkcjach wywoływanych przez funkcję wywoływany są uwzględniane.|  
|**% Rywalizacji włącznie**|Wartość procentowa rywalizacji wszystkie, w którym profilowania były wyłącznego rywalizacji dla tej funkcji w tym kontekście.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym wystąpił rywalizacji.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa głównej funkcji**|Nazwa bieżącej funkcji. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok wywołujący/wywoływany](../profiling/caller-callee-view.md)   
 [Obiekt wywołujący / wywoływany widok - dane próbkowania](../profiling/caller-callee-view-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji NET pamięci](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Widok wywołujący/wywoływany - dane próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)