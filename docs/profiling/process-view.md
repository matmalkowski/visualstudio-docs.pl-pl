---
title: Widok procesu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c730169988d931d3e1e57dd22f2793b1f8a16a72
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="process-view"></a>Widok procesu
Widok procesu wyświetla dane profilowania dla procesów i wątków, które zostały wykonane podczas przebiegu profilowania.  
  
 Procesy są wyświetlane według nazwy. Wątki są wyświetlane jako węzły podrzędne procesu, który je utworzył. Wątki są nazywane przez funkcję uruchomiony wątek lub etykieta **[ntdll.dll]** Jeśli symboli nie są dostępne.  
  
 Aby dodać lub usunąć kolumny, kliknij prawym przyciskiem myszy w widoku, a następnie wybierz **Dodaj/Usuń kolumny**. Ponadto można sortować dane, klikając nazwę kolumny. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md).  
  
 Kolumny widoku procesu są takie same dla danych, który jest generowany przy użyciu metody próbkowania i instrumentacji i danych, który zawiera dane pamięci .NET. W poniższej tabeli opisano wartości w kolumnie.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Unikatowy identyfikator.**|Identyfikator generowanych przez profiler jest unikatowy dla proces lub wątek.|  
|**IDENTYFIKATOR**|Wygenerowana przez system identyfikator proces lub wątek.|  
|**Nazwa**|Nazwa proces lub wątek.|  
|**Godzina rozpoczęcia**|Liczba milisekund lub cyklów procesora od początku profilowania na początku proces lub wątek.|  
|**Godzina zakończenia**|Liczba milisekund lub cyklów procesora od początku profilowania na końcu proces lub wątek.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)   
 [Widok danych metody Instrumentacji](../profiling/instrumentation-method-data-views.md)   
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)