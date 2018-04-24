---
title: Czasomierz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acd9a024ee20428bb8d90369da5b29994e939baa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="timer"></a>Czasomierz
VSPerfCmd.exe **czasomierza** opcja umożliwia ustawienie profilowania zdarzenia, które jest próbkowania cykli zegara procesora i opcjonalnie zmiany z domyślnej wartości 10 000 000 liczby cykli w interwale próbkowania. Przy użyciu procesora (jeden gigaherc) 1GH cykle zegara 10 000 000 jest około 100 próbek na sekundę. Minimalna liczba cykli, które można określić wynosi 50 000.  
  
 **Czasomierz** można użyć tylko, gdy używasz metoda profilowania próbkowania i można używać tylko w wierszu polecenia, który zawiera także **uruchamianie** lub **Attach** opcji.  
  
 Domyślnie zdarzenia próbkowania profilera ustawiono cykle zegara procesora i interwał próbkowania jest ustawiony na 10 000 000. **Czasomierza**, **PF**, **Sys**, i **licznika** opcje umożliwiają skonfigurowanie zdarzenie próbkowania i interwału próbkowania. **GC** opcja służy do zbierania danych pamięci .NET w każdym zdarzeniu kolekcji alokacji i odzyskiwanie. W wierszu polecenia można określić tylko jeden z tych opcji.  
  
 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w pierwszym wierszu polecenia, zawierający **uruchamianie** lub **Attach** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Cycles`  
 Wartość całkowita określająca liczbę cykli zegara procesora w interwale próbkowania. Jeśli `Cycles` nie zostanie określony, interwał jest ustawiony na 10 000 000. Określ wartość, bez spacji.  
  
## <a name="required-options"></a>Wymagane opcje  
 **Czasomierz** można określić tylko w wierszu polecenia, która zawiera jeden z następujących opcji.  
  
 **Uruchom:** `AppName`  
 Uruchamia profilera i aplikacji określonej przez `AppName`.  
  
 **Dołącz:** `PID`  
 Dołącza profiler do procesu, który został określony przez identyfikator procesu (`PID`).  
  
## <a name="invalid-options"></a>Nieprawidłowe opcje  
 Nie można określić następujące opcje w wierszu polecenia jako **czasomierza**.  
  
 **PF**[**:**`Events`]  
 Ustawia zdarzenie próbkowania błędów stron i opcjonalnie ustawia interwał próbkowania `Events`. Domyślny interwał PF wynosi 10.  
  
 **Sys**[**:**`Events`]  
 Ustawia wywołuje zdarzenie próbkowania do systemu operacyjnego i opcjonalnie ustawia interwał próbkowania `Events`. Sys domyślny interwał wynosi 10.  
  
 **Licznik**[**:**`Name,Reload,FriendlyName`]  
 Ustawia zdarzeń pobierania próbek wydajności procesora CPU licznika określony przez `Name` i ustawia interwał próbkowania `Reload`.  
  
 **Wykaz Globalny**[**:**{**alokacji**&#124;**okres istnienia**}]  
 Umożliwia zbieranie danych pamięci .NET. Domyślnie (**alokacji**), dane są zbierane w każdym zdarzeniu alokacji pamięci. Gdy **okres istnienia** parametr jest określony, również zbieranych danych w każdym zdarzeniu kolekcji pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak ustawić interwał próbkowania profilera do 1 000 000 cykli procesora.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)