---
title: ProcessOn i ProcessOff | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd2d33a6d0e333600c31e540f03d6140853e796d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681536"
---
# <a name="processon-and-processoff"></a>ProcessOn i ProcessOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [ProcessOn i ProcessOff](https://docs.microsoft.com/visualstudio/profiling/processon-and-processoff).  
  
VSPerfCmd.exe **ProcessOff** i **ProcessOn** podpoleceń polecenia wstrzymywanie i wznawianie profilowania dla określonego procesu w sesji profilowania z wiersza polecenia. **ProcessOff** zatrzymuje profilowanie procesu i **ProcessOn** uruchamia profilowanie procesu.  
  
 W większości przypadków należy określić **ProcessOn** lub **ProcessOff** jako jedyną opcję w VSPerfCmd.exe wiersza polecenia, ale można również łączyć z **GlobalOn**, **GlobalOff**, **ThreadOn**, i **ThreadOff** podpoleceń polecenia.  
  
 **ProcessOn** i **ProcessOff** podpoleceń polecenia interakcji z **GlobalOn** i **GlobalOff** podpoleceń polecenia, które kontrolują danych zbieranie dla wszystkich procesów w sesji profilowania wiersza polecenia i **ThreadOn** i **ThreadOff** podpoleceń polecenia, które kontroluje zbierania danych dla określonego wątku.  
  
 **ProcessOff** i **ProcessOn** podpoleceń polecenia wpływa na liczbę procesu uruchamiania/zatrzymywania, który jest przetwarzany przez profiler interfejsu API funkcji.  
  
-   **ProcessOff** natychmiast Ustawia liczbę uruchomień/zatrzymań procesu 0 i w związku z tym wstrzymuje profilowania.  
  
-   **ProcessOn** natychmiast Ustawia liczbę uruchomień/zatrzymań procesu 1 i w związku z tym wznawia profilowania.  
  
 Aby uzyskać więcej informacji, zobacz [API narzędzi profilowania](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `PID`  
 Liczba całkowita identyfikator procesu, aby rozpocząć lub zatrzymać. Identyfikatory procesów są wyświetlane na karcie Procesy Menedżera zadań Windows.  
  
## <a name="required-subcommands"></a>Wymagane podpoleceń polecenia.  
 Brak  
  
## <a name="valid-subcommands"></a>Nieprawidłowa podpoleceń polecenia.  
 **ProcessOn** i **ProcessOff** można określić w wierszach polecenia, które również zawierać następujących podpoleceń polecenia.  
  
 **Początek:** `Method`  
 Inicjuje sesję profilowania wiersza polecenia, a następnie ustawia określonej metody profilowania.  
  
 **Uruchom:** `AppName`  
 Uruchamia określoną aplikację i rozpoczyna się profilowanie przy użyciu metody pobierania próbek.  
  
 **Dołącz:** `PID`  
 Rozpoczyna się profilowanie określonego procesu.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Zatrzymuje się lub uruchamia profilowanie dla wszystkich procesów w sesji profilowania z wiersza polecenia.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Zatrzymuje się lub uruchamia profilowanie dla określonego wątku (tylko w przypadku metody Instrumentacji).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **ProcessOff** podpolecenia jest używany do zbierania danych profilowania dla uruchamiania aplikacji.  
  
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
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



