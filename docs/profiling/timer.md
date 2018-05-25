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
ms.openlocfilehash: cc361925d26bb6274a90d62c0b0c2085b47210c4
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="timer"></a>Czasomierz
VSPerfCmd.exe **czasomierza** opcja umożliwia ustawienie profilowania zdarzenia, które jest próbkowania cykli zegara procesora i opcjonalnie zmiany z domyślnej wartości 10 000 000 liczby cykli w interwale próbkowania. Przy użyciu procesora (jeden gigaherc) 1GH cykle zegara 10 000 000 jest około 100 próbek na sekundę. Minimalna liczba cykli, które można określić wynosi 50 000.  
  
 **Czasomierz** można użyć tylko, gdy używasz metoda profilowania próbkowania i można używać tylko w wierszu polecenia, który zawiera także **uruchamianie** lub **Attach** opcji.  
  
 Domyślnie zdarzenia próbkowania profilera ustawiono cykle zegara procesora i interwał próbkowania jest ustawiony na 10 000 000. **Czasomierza**, **PF**, **Sys**, i **licznika** opcje umożliwiają skonfigurowanie zdarzenie próbkowania i interwału próbkowania. **GC** opcja służy do zbierania danych pamięci .NET w każdym zdarzeniu kolekcji alokacji i odzyskiwanie. W wierszu polecenia można określić tylko jeden z tych opcji.  
  
 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w pierwszym wierszu polecenia, zawierający **uruchamianie** lub **Attach** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)