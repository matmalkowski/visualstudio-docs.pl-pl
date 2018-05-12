---
title: ThreadOn i ThreadOff | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a55bcfd09a99d9808bc378e680c33594007661e1
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="threadon-and-threadoff"></a>ThreadOn i ThreadOff
VSPerfCmd.exe **ThreadOff** i **ThreadOn** podpoleceń polecenia są dostępne tylko w sesji profilowania wiersza polecenia, korzystających z metody instrumentacji. **ThreadOff** i **ThreadOn** wstrzymywanie i wznawianie profilowania dla określonego wątku. **ThreadOff** zatrzymuje profilowanie wątku i **ThreadOn** uruchamia profilowanie wątku.  
  
 W większości przypadków należy określić **ThreadOn** lub **ThreadOff** jako opcję tylko w VSPerfCmd.exe wiersza polecenia, ale można również łączyć z **GlobalOn**, **GlobalOff**, **ProcessOn**, i **ProcessOff** podpoleceń polecenia.  
  
 **ThreadOn** i **ThreadOff** podpoleceń interakcji z **GlobalOn** i **GlobalOff** podpoleceń polecenia, które kontrolują danych Kolekcja wszystkich procesów w sesji profilowania wiersza polecenia i **ProcessOn** i **ProcessOff** podpoleceń polecenia, które kontrolują zbierania danych dla określonego procesu.  
  
 **ThreadOff** i **ThreadOn** podpoleceń wpłynąć na liczbę wątków uruchomień/zatrzymań, sterowany przez funkcje interfejsu API profilera.  
  
-   **ThreadOff** natychmiast Ustawia liczbę uruchomień/zatrzymań wątku 0 i w związku z tym wstrzymuje profilowania.  
  
-   **ThreadOn** natychmiast Ustawia liczbę uruchomień/zatrzymań wątku 1 i w związku z tym wznawia profilowania.  
  
 Aby uzyskać więcej informacji, zobacz [API narzędzi profilowania](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `TID`  
 Liczba całkowita identyfikator wątku, aby uruchomić lub zatrzymać.  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 **ThreadOn** i **ThreadOff** można określić wiersze poleceń, zawierające następujących podpoleceń polecenia.  
  
 **Uruchom:** `Method`  
 Inicjuje sesję profilowania wiersza polecenia i ustawia określonej metody profilowania.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Zatrzymuje i uruchamia profilowanie dla wszystkich procesów w sesji profilowania z wiersza polecenia.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 Zatrzymuje i uruchamia profilowanie dla określonego procesu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **ThreadOff** podpolecenia służy do zatrzymania zbierania danych profilowania, dzięki czemu są zbierane tylko dane uruchamiania aplikacji.  
  
```cmd  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)