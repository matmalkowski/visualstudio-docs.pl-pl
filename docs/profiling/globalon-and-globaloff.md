---
title: GlobalOn i GlobalOff | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef9d4416cdb3e1ea0d7f50b1c8baeca37ac8b15e
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238007"
---
# <a name="globalon-and-globaloff"></a>GlobalOn i GlobalOff
*VSPerfCmd.exe* **GlobalOff** i **GlobalOn** opcje wstrzymywanie i wznawianie profilowania dla wszystkich procesów i wątków w sesji profilowania z wiersza polecenia.  
  
 Można określić **GlobalOn** i **GlobalOff** jako tylko opcje *VSPerfCmd.exe* wiersza polecenia, lub można je uwzględnić w wiersze poleceń, które zawierają również  **Uruchom**, **uruchamianie**, lub **Attach** opcje.  
  
 **GlobalOn** i **GlobalOff** można również łączyć z **ProcessOn**, **ProcessOff**, **ThreadOn**i  **ThreadOff** opcje.  
  
 **GlobalOn** i **GlobalOff** opcje interakcji z **ProcessOn** i **ProcessOff** opcje, które kontrolują zbierania danych dla określony proces oraz z **ThreadOn** i **ThreadOff** opcje, które kontrolują zbierania danych dla określonego wątku.  
  
 **GlobalOff** i **GlobalOn** opcje wpływają na globalne uruchomień/zatrzymań zmieniany przez funkcje interfejsu API profilera.  
  
-   **GlobalOff** natychmiast Ustawia globalną liczbę uruchomień/zatrzymań równą 0 i w związku z tym wstrzymuje profilowania.  
  
-   **GlobalOn** natychmiast Ustawia globalną liczbę uruchomień/zatrzymań 1 i w związku z tym wznawia profilowania.  
  
 Aby uzyskać więcej informacji, zobacz [narzędzia interfejsów API profilowania](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /{GlobalOff|GlobalOn}  
  
VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]  
  
VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 **GlobalOn** i **GlobalOff** można określić w wierszu polecenia, który zawiera również następujące opcje.  
  
 **Uruchom:** `Method`  
 Inicjuje sesję wiersza polecenia profilera i ustawia określonej metody profilowania.  
  
 **Uruchom:** `AppName`  
 Uruchamia określony aplikację i rozpocznie się profilowania za pomocą metody pobierania próbek.  
  
 **Dołącz:** `PID`  
 Rozpoczyna się profilowania określony proces.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`PID`  
 Zatrzymuje i uruchamia profilowanie dla określonego procesu.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Zatrzymuje i uruchamia profilowanie dla określonego procesu (tylko w przypadku metody Instrumentacji).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **GlobalOff** i **GlobalOn** opcje są używane w celu uniknięcia zbierania danych profilowania dla aplikacji, uruchamiania i wyłączania.  
  
```cmd  
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
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)