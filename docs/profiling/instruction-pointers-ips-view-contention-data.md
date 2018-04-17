---
title: Widok wskaźników instrukcji (IP) - dane Kontencji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce158a47c9556bf6b29c929ea1e042eedf1f759c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Widok wskaźników instrukcji (IP) - dane Kontencji
Adresy IP widok danych kontencji Wyświetla listę danych instrukcje zestawu, które zostały zablokowane w przebiegu profilowania.  
  
 W poniższej tabeli przedstawiono wartości w kolumnach widok wskaźników instrukcji.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Wyłączny czasu blokowania**|Czas blokowania w tej funkcji.|  
|**% Wyłącznego czasu blokowania**|Wartość procentowa czasu blokowania, podczas gdy instrukcja została wykonana.|  
|**Wyłączny rywalizacji**|Liczba rywalizacji, które wystąpiły podczas instrukcji zostało wykonane.|  
|**% Wyłącznego rywalizacji**|Procent wszystkich rywalizacji w przebiegu profilowania, które wystąpiły podczas instrukcji zostało wykonane.|  
|**Adres funkcji**|Początkowy adres pamięci funkcji w załadować dane binarne.|  
|**Nazwa funkcji**|Nazwa funkcji, która zawiera instrukcję.|  
|**Adres instrukcji**|Adres pamięci z instrukcjami w załadować dane binarne.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera instrukcję.|  
|**Identyfikator procesu**|Identyfikator PID procesu PROFILOWANEGO procesu.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Rozpocznij znaków źródła**|Przesunięcie znaku w wierszu pliku źródłowego, w którym rozpoczyna się tej instrukcji.|  
|**Źródło znak końcowy**|Przesunięcie znaku w wiersza pliku źródłowego, w którym kończy się w tej instrukcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera instrukcję.|  
|**Początek wiersza źródłowego**|Numer wiersza pliku źródłowego, w którym rozpoczyna się tej instrukcji.|  
|**Źródło końca wiersza**|Numer wiersza pliku źródłowego, w którym kończy się w tej instrukcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view.md)   
 [Wskaźników instrukcji (IP) View - próbkowanie](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)