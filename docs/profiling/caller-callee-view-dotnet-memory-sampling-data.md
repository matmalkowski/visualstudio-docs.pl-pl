---
title: Widok wywołujący wywoływany - dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c5a67bff623ce3cfa55e89057e918d19f4ba5868
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Widok wywołujący/wywoływany - dane próbkowania pamięci .NET
Widok wywołujący/wywoływany wyświetla danych dla wybranej funkcji i jej nadrzędne i podrzędne funkcji profilowania pamięci platformy .NET. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** są wyświetlane w środkowym siatki i zawiera informacje na temat wybranej funkcji profilowania pamięci. Wartości obejmują wszystkie próbki wywołania funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** jest wyświetlany w górnym siatki i zawiera ilość wartość wybranych funkcji (bieżącego), który został wygenerowany przez wywołania funkcji wywołującego (nadrzędnego).  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w siatce dolnej i zawiera profilowania dane dla funkcji wywoływanych (podrzędny) wybranej funkcji podczas wywoływania funkcji podrzędnych przez bieżącą funkcję pamięci.  
  
 Kliknij dwukrotnie wywołujący lub wywoływany funkcja wiersza aby wiersz bieżącej funkcji.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera funkcję.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa funkcji**|Pełna nazwa funkcji.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Adres funkcji.|  
|**Typ**|Kontekst funkcji:<br /><br /> **0** -bieżącą funkcję<br /><br /> **1** — funkcja, która wywołuje bieżącą funkcję<br /><br /> **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**poziom**|Głębokość funkcji w drzewie wywołań. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Alokacje włącznie**|— Dla bieżącej funkcji, liczba obiektów przydzielonych za pomocą funkcji w przebiegu profilowania. Liczba ta obejmuje obiekty, które zostały utworzone w funkcjach wywoływanych.<br />— Dla funkcji wywołującego, liczba przydziałów włącznie bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji.<br />— Dla funkcji wywoływany, liczbę obiektów, które zostały przydzielone wystąpienia tej funkcji, które zostały wywołane przez bieżącą funkcję. Liczba obejmuje przydziałów, które zostały dokonane przez funkcje, które zostały wywołane przez funkcję wywoływany.|  
|**% Alokacji włącznie**|Procent wszystkich obiektów, które zostały utworzone w przebiegu, który profilowania były alokacji włącznie tej funkcji.|  
|**Wyłączny alokacji**|— Dla bieżącej funkcji, liczbę obiektów, które zostały utworzone, gdy funkcja została uruchomiona kodu treść funkcji (oznacza to, gdy funkcja znajdowała się w górnej części stosu wywołań). Liczba nie obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez funkcję.<br />— Dla funkcji wywołującego, liczba przydziałów wyłącznego bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji.<br />— Dla funkcji wywoływany, liczbę obiektów, które zostały utworzone przez wystąpień tej funkcji, które zostały wywołane przez bieżącą funkcję. Liczba nie obejmuje obiekty, które zostały utworzone przez funkcje, które zostały wywołane przez funkcję wywoływany.|  
|**% Wyłącznego alokacji**|Procent wszystkich obiektów, które zostały utworzone w przebiegu, który profilowania były alokacji włącznie tej funkcji.|  
|**Bajty włącznie**|— Dla funkcji bieżąca liczba bajtów pamięci, które zostały przydzielone przez funkcję w przebiegu profilowania. Liczba zawiera pamięci, która została przydzielona w funkcje, które zostały wywołane przez tę funkcję.<br />— Dla funkcji wywołującego liczba bajtów włącznie z bieżącej funkcji, które zostały wygenerowane z wywołań za pomocą funkcji wywołującego.<br />— Dla funkcji wywoływany, liczba bajtów, które zostały przydzielone wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba obejmuje bajtów przydzielonych przez funkcje, które zostały wywołane przez funkcję wywoływany.|  
|**% Bajtów włącznie**|Procent wszystkich bajtów pamięci przydzielone w przebiegu, który profilowania były alokacji włącznie tej funkcji.|  
|**Wyłączny bajtów**|— Dla funkcji bieżąca liczba bajtów pamięci, które zostały przydzielone przez funkcję w przebiegu profilowania. Ta liczba nie obejmuje pamięci, która została przydzielona przez funkcje, które zostały wywołane przez bieżącą funkcję.<br />— Dla funkcji wywołującego, liczba bajtów wyłącznego bieżącej funkcji, które zostały wygenerowane przez wywołania funkcji wywołującego.<br />— Dla funkcji wywoływany, liczba bajtów, które zostały przydzielone wystąpień funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba nie obejmuje bajtów przydzielonych przez funkcje, które zostały wywołane przez funkcję wywoływany.|  
|**% Wyłącznego bajtów**|Procent wszystkich bajtów pamięci przydzielone w przebiegu, który profilowania były wyłącznego alokacji tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji pamięci .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Widok wywołujący/wywoływany - dane próbkowania](../profiling/caller-callee-view-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)