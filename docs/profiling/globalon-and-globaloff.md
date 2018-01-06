---
title: GlobalOn i GlobalOff | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9998f0f4d46a37b1eccd3cdf5dc48dd994f651a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="globalon-and-globaloff"></a>GlobalOn i GlobalOff
VSPerfCmd.exe **GlobalOff** i **GlobalOn** opcje wstrzymywanie i wznawianie profilowania dla wszystkich procesów i wątków w sesji profilowania z wiersza polecenia.  
  
 Można określić **GlobalOn** i **GlobalOff** jak tylko opcje wiersza polecenia VSPerfCmd.exe, lub można je uwzględnić w wiersze poleceń, które zawierają również **Start**, **Uruchamianie**, lub **Attach** opcje.  
  
 **GlobalOn** i **GlobalOff** można również łączyć z **ProcessOn**, **ProcessOff**, **ThreadOn**i  **ThreadOff** opcje.  
  
 **GlobalOn** i **GlobalOff** opcje interakcji z **ProcessOn** i **ProcessOff** opcje, które kontrolują zbierania danych dla określony proces oraz z **ThreadOn** i **ThreadOff** opcje, które kontrolują zbierania danych dla określonego wątku.  
  
 **GlobalOff** i **GlobalOn** opcje wpływają na globalne uruchomień/zatrzymań zmieniany przez funkcje interfejsu API profilera.  
  
-   **GlobalOff** natychmiast Ustawia globalną liczbę uruchomień/zatrzymań równą 0 i w związku z tym wstrzymuje profilowania.  
  
-   **GlobalOn** natychmiast Ustawia globalną liczbę uruchomień/zatrzymań 1 i w związku z tym wznawia profilowania.  
  
 Aby uzyskać więcej informacji, zobacz [API narzędzi profilowania](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /{GlobalOff|GlobalOn}  
  
VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]  
  
VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 **GlobalOn** i **GlobalOff** można określić w wierszu polecenia, który zawiera również następujące opcje.  
  
 **Start:**`Method`  
 Inicjuje sesję wiersza polecenia profilera i ustawia określonej metody profilowania.  
  
 **Uruchom:**`AppName`  
 Uruchamia określony aplikację i rozpocznie się profilowania za pomocą metody pobierania próbek.  
  
 **Dołącz:**`PID`  
 Rozpoczyna się profilowania określony proces.  
  
 {**ProcessOff**&#124; **ProcessOn**}**:**`PID`  
 Zatrzymuje i uruchamia profilowanie dla określonego procesu.  
  
 {**ThreadOff**&#124; **ThreadOn**}**:**`TID`  
 Zatrzymuje i uruchamia profilowanie dla określonego procesu (tylko w przypadku metody Instrumentacji).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **GlobalOff** i **GlobalOn** opcje są używane w celu uniknięcia zbierania danych profilowania dla aplikacji, uruchamiania i wyłączania.  
  
```  
; Initialize the profiler with profiling stopped.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff  
; Start an instrumented application and wait for it to warm up.  
; Start profiling.  
VSPerfCmd.exe /GlobalOn  
; Exercise the application functionality that you want to profile.  
; Stop profiling.  
VSPerfCmd.exe /GlobalOff  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)