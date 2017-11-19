---
title: Zdarzenia (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84f1d515722203f15b1b667df6fb7fdf72fe4fb4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="events-vsperfcmd"></a>Zdarzenia (VSPerfCmd)
VSPerfCmd.exe **zdarzenia** opcja kontroluje rejestrowanie zdarzeń śledzenia dla systemu Windows (ETW). Dane funkcji ETW są zapisywane do pliku etl, który różni się od pliku danych profilera. Dane mogą być wyświetlane w raporcie przy użyciu [VSPerfReport](../profiling/vsperfreport.md) polecenia/Summary: ETW.  
  
 **Zdarzenia** opcji można wywołać w dowolnym momencie przed VSPerfCmd **zamknięcia** polecenia jest wywoływana, aby zatrzymać profilowanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Parametry  
 **Na**&#124; **Wyłączanie**  
 Uruchamia lub zatrzymuje zbieranie danych zdarzeń.  
  
 `Guid`  
 Identyfikator GUID kontrolki dostawcy.  
  
 `ProviderName`  
 Nazwa dostawcy, który jest zarejestrowany z Instrumentacji zarządzania Windows (WMI).  
  
 `Flags`  
 "0 x"-prefiksem wartość flagi szesnastkowa, która jest definiowana za pomocą dostawcy zdarzeń.  
  
 `Level`  
 Określa ilość zbieranych danych. `Level`jest zdefiniowany przez dostawcę zdarzeń.  
  
 **Zdarzenia** opcji rozumie następujące jądra słowa kluczowe jako nazwy dostawcy:  
  
 **Proces**  
 Przetwarzania zdarzeń  
  
 **Wątek**  
 Zdarzenia wątków  
  
 **Obraz**  
 Obraz obciążenia i zwolnić zdarzenia  
  
 **Dysku**  
 We/Wy dysku zdarzenia  
  
 **Plik**  
 Zdarzenia We/Wy pliku  
  
 **Hardfault**  
 Sprzętowych błędów stron  
  
 **Pagefault**  
 Słabe strony błędów  
  
 **Sieci**  
 Zdarzenia sieci  
  
 **Rejestru**  
 Zdarzenia dostępu do rejestru  
  
 Należy pamiętać, że dostawca jądra można włączyć tylko. Nie można wyłączyć ani jej flag można modyfikować, dopóki zamknięcie monitora.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Po włączeniu zdarzenia CLR ETW uruchamiania dodatkowych danych również są zbierane w śledzenia Wyświetl raport. Aby wykluczyć zdarzenia uruchamiania były wyświetlane w raporcie, użyj następującego polecenia:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Jeśli zdarzenia uruchamiania nie jest wykluczone, ponieważ te zdarzenia nie są wymienione w pliku Managed Object Format (MOF), ich widoczny jako identyfikatorów GUID w raporcie. Aby uzyskać więcej informacji, zobacz tę stronę w witrynie sieci Web firmy Microsoft: [plik przykładowy Managed Object Format (MOF)](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)