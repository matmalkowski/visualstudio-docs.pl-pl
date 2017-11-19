---
title: Sys (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c733e9ce91ede2e8944616c5db1a727349854b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
VSPerfCmd.exe **Sys** opcji ustawienie profilowania zdarzenia, które jest próbkowany zdarzenia wywołania systemowe (wywołania funkcji profilowanych aplikacji dla systemu operacyjnego), a opcjonalnie zmian liczba systemu wywołań w próbki Interwał w domyślnej 10.  
  
 **Sys** można używać tylko w wierszu polecenia, który zawiera także **uruchamianie** lub **Attach** opcji.  
  
 Domyślnie zdarzenia próbkowania profilera ustawiono cykle zegara procesora i interwał próbkowania jest ustawiony na 10 000 000. **Czasomierza**, **PF**, **Sys**, i **licznika** opcje umożliwiają skonfigurowanie zdarzenie próbkowania i interwału próbkowania. **GC** opcja służy do zbierania danych pamięci .NET w każdym zdarzeniu kolekcji alokacji i odzyskiwanie. W wierszu polecenia można określić tylko jeden z tych opcji.  
  
 Zdarzenie próbkowania i interwał próbkowania można ustawić tylko w pierwszym wierszu polecenia, zawierający **uruchamianie** lub **Attach** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Events`  
 Wartość całkowita określająca liczbę systemu wywołać zdarzenia w interwale próbkowania. Jeśli `Events` nie zostanie określony, interwał jest ustawiony na 10.  
  
## <a name="required-options"></a>Wymagane opcje  
 **Sys** wymaga jednego z następujących opcji.  
  
 **Uruchom:**`AppName`  
 Uruchamia profilera i aplikacji określonej przez `AppName`.  
  
 **Dołącz:**`PID`  
 Dołącza profiler do procesu, który został określony przez `PID`.  
  
## <a name="invalid-options"></a>Nieprawidłowe opcje  
 Nie można określić następujące opcje w wierszu polecenia jako **Sys**.  
  
 **PF**[**:**`Events`]  
 Ustawia zdarzenie próbkowania błędów stron i opcjonalnie ustawia interwał próbkowania `Events`. Domyślny interwał PF wynosi 10.  
  
 **Czasomierz**[**:**`Cycles`]  
 Ustawia cykli zdarzenie próbkowania zegara procesora i opcjonalnie ustawia interwał próbkowania `Cycles`. Domyślny interwał czasomierza wynosi 10 000 000.  
  
 **Licznik:** `Name`[`,Reload`[`,FriendlyName`]]  
 Ustawia zdarzeń pobierania próbek wydajności procesora CPU licznika określony przez `Name` i ustawia interwał próbkowania `Reload`.  
  
 **Wykaz Globalny**[**:**{**alokacji**&#124; **Okres istnienia**}]  
 Umożliwia zbieranie danych pamięci .NET. Domyślnie (**alokacji**), dane są zbierane w każdym zdarzeniu alokacji pamięci. Gdy **okres istnienia** parametr jest określony, również zbieranych danych w każdym zdarzeniu kolekcji pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób ustawioną profilera zdarzenie próbkowania wywołań systemowych i ustaw interwał próbkowania do 20 wywołań na próbkę.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)