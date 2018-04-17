---
title: Widok linii | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7c5565ea8cecb50166536d399fd5a1e7b4f4dd5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="lines-view"></a>Widok linii
Widok linii jest dostępna tylko w przypadku dane zebrane przy użyciu metody próbkowania profilera. Widok nie jest dostępna dla danych, które zostały zebrane przy użyciu Instrumentacji.  
  
 Do pobierania próbek danych profilu, widok linii identyfikuje instrukcji w funkcji, która powodowała bezpośrednio po próbki został zebrany. W przypadku danych pamięci .NET widok linii identyfikuje instrukcji, które przydzielić pamięci.  
  
 W pliku źródłowym instrukcję może obejmować więcej tego wiersza w pliku źródłowym i jednym wierszu może zawierać więcej niż jedną instrukcję.  
  
 Instrukcja jest identyfikowany przez następujące czynności:  
  
-   Plik źródłowy, który zawiera deklarację funkcji.  
  
-   Funkcja, która zawiera instrukcję.  
  
-   Wiersza źródłowego, w którym rozpoczyna się instrukcji.  
  
-   Po znaku wiersza źródłowego, w którym rozpoczyna się instrukcji.  
  
-   Wiersza źródłowego, w którym kończy się instrukcji.  
  
-   Po znaku wiersza źródłowego, w którym kończy się instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok linii](../profiling/lines-view-sampling-data.md)   
 [Widok linii - próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Widok linii](../profiling/lines-view-contention-data.md)