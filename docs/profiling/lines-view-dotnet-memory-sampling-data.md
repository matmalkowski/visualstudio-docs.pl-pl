---
title: Widok linii - dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b2863c5c3441240593035a933a6224d95c0b4474
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="lines-view---net-memory-sampling-data"></a>Widok linii - dane próbkowania pamięci .NET
Widok linii dla platformy .NET pamięci alokacji profilowania danych przy użyciu metody próbkowania wymieniono instrukcje, które przydzielonej pamięci podczas przebiegu profilowania. Kolumny także rozmiaru i liczby alokacji.  
  
 W pliku źródłowym instrukcję może obejmować więcej niż jeden wiersz w pliku źródłowym, a jednym wierszu może zawierać więcej niż jedną instrukcję.  
  
 Instrukcja jest identyfikowany przez następujące czynności:  
  
-   Plik źródłowy, który zawiera deklarację funkcji.  
  
-   Funkcja, która zawiera instrukcję.  
  
-   Wiersza źródłowego, w którym rozpoczyna się instrukcji.  
  
-   Po znaku wiersza źródłowego, w którym rozpoczyna się instrukcji.  
  
-   Wiersza źródłowego, w którym kończy się instrukcji.  
  
-   Po znaku wiersza źródłowego, w którym kończy się instrukcji.  
  
 Kolumna nazw wiersza zawiera sortowanie łączenia danych identyfikator.  
  
 Zgodnie z definicją instrukcję nie wywołuje inne funkcje. W związku z tym są wyświetlane tylko wartości wyłącznego.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu zawiera instrukcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera instrukcję.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera instrukcję.|  
|**Nazwa funkcji**|Nazwa funkcji, która zawiera instrukcję.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Początkowy adres funkcji.|  
|**Początek wiersza źródłowego**|Numer wiersza początkowego w pliku źródłowym, w którym wystąpiła Alokacja.|  
|**Źródło końca wiersza**|Końcowy numer wiersza pliku źródłowego, w którym wystąpiła Alokacja.|  
|**Rozpocznij znaków źródła**|Przesunięcie początkowy znaku w wierszu pliku źródłowego, o której wystąpiła Alokacja.|  
|**Źródło znak końcowy**|Przesunięcie znak końcowy w wiersza pliku źródłowego, w którym wystąpiła Alokacja.|  
|**Nazwa linii**|Generowane przez profiler identyfikator wiersza przy użyciu następującej składni:`Source File`**; [**  `Line Number Start` **,**`Character Start`**] ->; [** `Line Number Start,Character Start`**]**|  
|**Wyłączny alokacji**|Całkowita liczba obiektów, które zostały utworzone w tym wierszu.|  
|**% Wyłącznego alokacji**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, przydzielone w tym wierszu.|  
|**Wyłączny bajtów**|Procent wszystkich bajtów pamięci, która była przydzielona w przebiegu profilowania przydzielone w tym wierszu.|  
|**% Wyłącznego bajtów**|Procent wszystkich bajtów pamięci, która była przydzielona w przebiegu profilowania przydzielone w tym wierszu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok linii](../profiling/lines-view-sampling-data.md)