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
ms.workload: multiple
ms.openlocfilehash: 27309a459128e6ed9ebb17d295bc39c6c621dcd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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