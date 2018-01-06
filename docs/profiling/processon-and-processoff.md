---
title: ProcessOn i ProcessOff | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e8a94b52ba8d2fc0ce4208014e40ab3821ecb1e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="processon-and-processoff"></a>ProcessOn i ProcessOff
VSPerfCmd.exe **ProcessOff** i **ProcessOn** podpoleceń wstrzymywanie i wznawianie, profilowanie dla określonego procesu w sesji profilowania z wiersza polecenia. **ProcessOff** zatrzymuje profilowanie proces i **ProcessOn** uruchamia profilowanie procesu.  
  
 W większości przypadków należy określić **ProcessOn** lub **ProcessOff** jako opcję tylko w VSPerfCmd.exe wiersza polecenia, ale można również łączyć z **GlobalOn**, **GlobalOff**, **ThreadOn**, i **ThreadOff** podpoleceń polecenia.  
  
 **ProcessOn** i **ProcessOff** podpoleceń interakcji z **GlobalOn** i **GlobalOff** podpoleceń polecenia, które kontrolują danych Kolekcja wszystkich procesów w sesji profilowania wiersza polecenia i **ThreadOn** i **ThreadOff** podpoleceń polecenia, które kontrolują zbierania danych dla określonego wątku.  
  
 **ProcessOff** i **ProcessOn** podpoleceń wpłynąć na liczbę procesu uruchamiania/zatrzymywania steruje się za pomocą funkcji API profilera.  
  
-   **ProcessOff** natychmiast Ustawia liczbę uruchomień/zatrzymań procesu 0 i w związku z tym wstrzymuje profilowania.  
  
-   **ProcessOn** natychmiast Ustawia liczbę uruchomień/zatrzymań procesu 1 i w związku z tym wznawia profilowania.  
  
 Aby uzyskać więcej informacji, zobacz [API narzędzi profilowania](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `PID`  
 Liczba całkowita identyfikator procesu, aby uruchomić lub zatrzymać. Identyfikatorów procesów są wyświetlane na karcie procesu Menedżera zadań systemu Windows.  
  
## <a name="required-subcommands"></a>Wymagane podpoleceń polecenia.  
 Brak  
  
## <a name="valid-subcommands"></a>Nieprawidłowa podpoleceń polecenia.  
 **ProcessOn** i **ProcessOff** można określić wiersze poleceń, zawierające następujących podpoleceń polecenia.  
  
 **Start:**`Method`  
 Inicjuje sesję profilowania wiersza polecenia i ustawia określonej metody profilowania.  
  
 **Uruchom:**`AppName`  
 Uruchamia określony aplikację i rozpocznie się profilowania za pomocą metody pobierania próbek.  
  
 **Dołącz:**`PID`  
 Rozpoczyna się profilowania określony proces.  
  
 **GlobalOff**&#124; **GlobalOn**  
 Zatrzymuje i uruchamia profilowanie dla wszystkich procesów w sesji profilowania z wiersza polecenia.  
  
 {**ThreadOff**&#124; **ThreadOn**}**:**`TID`  
 Zatrzymuje i uruchamia profilowanie dla określonego wątku (tylko w przypadku metody Instrumentacji).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **ProcessOff** podpolecenia służy do zbierania danych profilowania do uruchomienia aplikacji.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)