---
title: "Widok wskaźników instrukcji (IP) - dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c37cc7b63a8f93c3b63cdda0bb9ce460a01d195a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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