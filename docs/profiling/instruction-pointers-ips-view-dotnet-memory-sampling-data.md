---
title: Widok wskaźników instrukcji (IP) - dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 035ddb85410b1b5d4b883425ecbb2af35c73c58f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Widok wskaźników instrukcji (IP) - dane próbkowania pamięci .NET
Wyświetlanie adresów IP dla danych pamięci .NET alokacji profilowania zebrane przy użyciu metody pobierania próbek list instrukcje zestawu, które przydzielonej pamięci podczas przebiegu profilowania. Kolumny w widoku listy również rozmiaru i liczby alokacji.  
  
 Tylko wyłączne wartości są wymienione.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera instrukcję.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera instrukcję.|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Początkowy adres funkcji.|  
|**Początek wiersza źródłowego**|Numer wiersza początkowego w pliku źródłowym, w którym wystąpiła Alokacja.|  
|**Źródło końca wiersza**|Końcowy numer wiersza pliku źródłowego, w którym wystąpiła Alokacja.|  
|**Rozpocznij znaków źródła**|Przesunięcie początkowy znaku w wierszu pliku źródłowego, o której wystąpiła Alokacja.|  
|**Źródło znak końcowy**|Przesunięcie znak końcowy w wiersza pliku źródłowego, w którym wystąpiła Alokacja.|  
|**Adres instrukcji**|Adres instrukcji.|  
|**Wyłączny alokacji**|Całkowita liczba obiektów, które zostały utworzone przez instrukcję.|  
|**% Wyłącznego alokacji**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, przydzielone przez instrukcję.|  
|**Wyłączny bajtów**|Liczba bajtów pamięci przydzielone w przebiegu, który profilowania przydzielone przez instrukcję.|  
|**% Wyłącznego bajtów**|Procent wszystkich bajtów pamięci, która była przydzielona w przebiegu profilowania przydzielone przez instrukcję.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)