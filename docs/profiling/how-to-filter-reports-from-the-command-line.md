---
title: "Porady: filtrowanie raportów z wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff4bae4f3071755149acdea49d312f8a9efcf31d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Porady: filtrowanie raportów z wiersza polecenia
Za pomocą opcji **VSPerfReport** polecenia, można filtrować raporty do segmentu określony czas plik danych profilowania lub ograniczanie danych do co najmniej jednego procesu lub wątki. Aby uzyskać więcej informacji na temat tego polecenia, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**Czas rozpoczęcia:**[*wartość*]|Wyświetla tylko dane zebrane po wartości (w milisekundach).|  
|**Wartość EndTime:**[*wartość*]|Wyświetla tylko dane zebrane przed wartością (w milisekundach).|  
|**FilterFile:**`VSPFFile`|Określa lokalizację pliku filtru, który został wygenerowany na podstawie **raport dotyczący wydajności programu Visual Studio** okna.|  
|**MsFilter:**[*StartTime, czas trwania*]|Wyświetla tylko dane z `StartTime` do długości `Duration` (w milisekundach).|  
|**Proces:**[*Pid*]|Wyświetla tylko dane z określonego procesu.|  
|**Wątek:**[*ThreadID*]|Wyświetla tylko dane z określonego wątku.|  
|**Wątek:**[*Identyfikator_wątku, Identyfikator_procesu*]|Wyświetla tylko dane z określonego wątku, który jest skojarzony z określonym procesem.|