---
title: Licznik | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eaebb7afc76066e9c1c53b0649c70dd346ddb72f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="counter"></a>Licznik
**Licznika** opcji zbiera dane z liczników wydajności procesora (sprzęt).  
  
-   Gdy używana jest metoda, profilowania próbkowania **licznika** Określa licznik wydajności na układ i liczba licznik zdarzeń do użycia jako interwał próbkowania. Można określić tylko jeden licznik, gdy używasz próbkowania.  
  
-   Gdy używana jest metoda profilowania instrumentacji, numerem zdarzenia liczników, które wystąpiły w przedziale między zdarzeniami poprzedni i bieżącej kolekcji są wyświetlane jako oddzielne pola w raportów profilera. Wiele **licznika** opcje można określić podczas korzystania z Instrumentacji.  
  
 Każdy typ procesora ma swój własny zestaw liczników wydajności sprzętu. Profiler definiuje zestaw liczników wydajności ogólnych, które są wspólne dla prawie wszystkie procesory. Aby wyświetlić listę liczników ogólnych i specyficznych dla procesora na komputerze, należy użyć narzędzia VSPerfCmd **QueryCounters** polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]  
```  
  
```  
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Name`  
 Nazwa licznika. Użyj VSPerfCmd.exe **/QueryCounters** opcję, aby wyświetlić listę nazw dostępne liczniki na komputerze.  
  
 `Reload`  
 Liczba zdarzeń licznika w interwale próbkowania. Nie należy używać przy użyciu metody instrumentacji.  
  
 `FriendlyName`  
 (Opcjonalnie) Ciąg używany zamiast `Name` w nagłówkach kolumn widoków i raportów profilera.  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcja licznik może służyć tylko z jednym z następujących opcji:  
  
 **Uruchom:** `Trace`  
 Inicjuje przy użyciu metody Instrumentacji profilera.  
  
 **Uruchom:** `AppName`  
 Uruchamia określonej aplikacji i profilera. Profiler musi zostać zainicjowany przy użyciu metody pobierania próbek.  
  
 **Dołącz:** `PID`  
 Uruchamia profilera i dołącza go do proces określony przez identyfikator procesu. Profiler musi zostać zainicjowany przy użyciu metody pobierania próbek.  
  
## <a name="example"></a>Przykład  
 W przykładzie metoda pobierania próbek pokazano, jak przykładowa aplikacja w każdym 1000 wystąpienia licznika ogólnego profilera NonHaltedCycles.  
  
 Przykład metody Instrumentacji demonstruje sposób inicjowania profilera do zbierania zdarzeń liczników L2InstructionFetches. Nazwa licznika L2InstructionFetches jest specyficznych dla procesora.  
  
```  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)