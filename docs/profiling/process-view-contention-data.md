---
title: "Widok procesu — dane Kontencji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4de13644837c3fd21b38e0be6f4414700eb92414
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="process-view---contention-data"></a>Widok procesu — dane Kontencji
Widok procesu przedstawia dane rywalizacji procesów i wątków, które zostały wykonane podczas przebiegu profilowania.  
  
 Gdy są dostępne symbole, procesy są wyświetlane według nazwy. Jeśli symbole nie są dostępne, procesy są wyświetlane według ich adres pamięci w formacie szesnastkowym. Wątki są wyświetlane jako elementy podrzędne procesu, który je utworzył.  
  
 W poniższej tabeli przedstawiono wartości kolumn w tabeli widoku procesu.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Godzina rozpoczęcia**|Liczba milisekund lub cyklów procesora od początku profilowania na początku proces lub wątek.|  
|**Czas blokowania**|Łączny czas, w którym funkcje proces lub wątek został zablokowany wykonywania.|  
|**% Czasu blokowania**|Procent istnienia proces lub wątek, w którym funkcje proces lub wątek został zablokowany wykonywania.|  
|**Rywalizacji**|Ile razy wykonywania funkcji proces lub wątek został zablokowany.|  
|**% Rywalizacji**|Wartość procentowa rywalizacji wszystkie, w którym profilowania były rywalizacji proces lub wątek.|  
|**Godzina zakończenia**|Liczba milisekund lub cyklów procesora od początku profilowania na końcu proces lub wątek.|  
|**IDENTYFIKATOR**|Wygenerowana przez system identyfikator proces lub wątek.|  
|**Okres istnienia**|Liczba milisekund lub cyklów procesora od początku proces lub wątek do końca proces lub wątek lub zakończenia profilowania.|  
|**Typ**|Typ wiersza, przetwarzania lub wątku.<br /><br /> Tylko w **VSReport** raporty wiersza polecenia. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nazwa**|Nazwa proces lub wątek.|  
|**Unikatowy identyfikator.**|Identyfikator generowanych przez profiler jest unikatowy dla proces lub wątek.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok procesu](../profiling/process-view.md)