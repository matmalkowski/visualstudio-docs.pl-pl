---
title: Caller — widok wywoływany - dane próbkowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b9b740689175f91f4bc69396121da0bed336532
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34548713"
---
# <a name="callercallee-view---sampling-data"></a>Widok wywołujący/wywoływany - dane próbkowania
Widok wywołujący/wywoływany Wyświetla informacje dotyczące profilowania dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** jest wyświetlane w środkowym siatki, a pokazuje profilowania informacji dla wybranych funkcji. Wartości obejmują wszystkie próbki wywołania funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** jest wyświetlany w górnym siatki i zawiera funkcje z wartościami wybranej funkcji (bieżącego) poszczególnych wkładów wywołującego (nadrzędnego).  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w siatce dolnej i pokazuje profilowania informacje dotyczące funkcji wywoływanych (podrzędny) wybranej funkcji podczas wywoływania funkcji podrzędnych przez bieżącą funkcję.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
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
|**Typ**|Kontekst funkcji:<br /><br /> -   **0** -bieżącą funkcję<br />-   **1** — funkcja, która wywołuje bieżącą funkcję<br />-   **2** — funkcja, która jest wywoływana przez bieżącą funkcję|  
|**Nazwa głównej funkcji**|Nazwa bieżącej funkcji.|  
|**Przykłady włącznie**|— Dla bieżącej funkcji, liczba próbek, które zostały zebrane, mimo że wykonywania tej funkcji lub jednej z jej funkcji podrzędnych.<br />— Dla funkcji wywołującego, liczba włącznie przykłady bieżącej funkcji, które zostały zebrane, gdy ta funkcja jest wywoływana bieżącej funkcji.<br />— Dla funkcji wywoływany, liczba próbek włącznie tej funkcji, które zostały zebrane podczas bieżącej funkcji wywoływania tej funkcji.|  
|**% Próbek włącznie**|Wartość procentowa próbek wszystkie, w którym profilowania były włącznie próbek w tej funkcji.|  
|**Wyłącznych próbek**|— Dla bieżącej funkcji liczba próbek w przebiegu, który profilowania zostały zebrane, gdy ta funkcja bezpośrednio było wykonywane; oznacza to, gdy ta funkcja została u góry stosu wywołań. Przykłady, które są zbierane podczas wykonywania funkcji podrzędnych tej funkcji nie są wliczane do liczby wyłącznego.<br />— Dla funkcji wywołującego, liczba wyłącznych próbek bieżącej funkcji, które zostały zebrane, gdy ta funkcja jest wywoływana bieżącej funkcji.<br />— Dla funkcji wywoływany, liczba wyłącznych próbek w tej funkcji, które zostały zebrane podczas bieżącej funkcji wywoływania tej funkcji.|  
|**% Wyłącznych próbek**|Wartość procentowa próbek wszystkie, w którym profilowania były wyłącznych próbek w tej funkcji.|  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wywołujący/wywoływany - dane próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji pamięci .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)