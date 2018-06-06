---
title: Zdarzenia (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb99ec5bab1098f3551548698919cb1f2fc8f8b1
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764335"
---
# <a name="events-vsperfcmd"></a>Zdarzenia (VSPerfCmd)
*VSPerfCmd.exe* **zdarzenia** opcja kontroluje rejestrowanie zdarzeń śledzenia dla systemu Windows (ETW). Dane funkcji ETW są zapisywane do pliku etl, który różni się od pliku danych profilera. Dane mogą być wyświetlane w raporcie przy użyciu [VSPerfReport](../profiling/vsperfreport.md) polecenia/Summary: ETW.  
  
 **Zdarzenia** opcji można wywołać w dowolnym momencie przed VSPerfCmd **zamknięcia** polecenia jest wywoływana, aby zatrzymać profilowanie.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Parametry  
 **Na**&#124;**wyłączone**  
 Uruchamia lub zatrzymuje zbieranie danych zdarzeń.  
  
 `Guid`  
 Identyfikator GUID kontrolki dostawcy.  
  
 `ProviderName`  
 Nazwa dostawcy, który jest zarejestrowany z Instrumentacji zarządzania Windows (WMI).  
  
 `Flags`  
 "0 x"-prefiksem wartość flagi szesnastkowa, która jest definiowana za pomocą dostawcy zdarzeń.  
  
 `Level`  
 Określa ilość zbieranych danych. `Level` jest zdefiniowany przez dostawcę zdarzeń.  
  
 **Zdarzenia** opcji rozumie następujące jądra słowa kluczowe jako nazwy dostawcy:  
  
 **Proces**  
 Przetwarzania zdarzeń  
  
 **Wątek**  
 Zdarzenia wątków  
  
 **Obraz**  
 Obraz obciążenia i zwolnić zdarzenia  
  
 **dysku**  
 We/Wy dysku zdarzenia  
  
 **Plik**  
 Zdarzenia We/Wy pliku  
  
 **Hardfault**  
 Sprzętowych błędów stron  
  
 **Pagefault**  
 Słabe strony błędów  
  
 **Sieci**  
 Zdarzenia sieci  
  
 **Registry**  
 Zdarzenia dostępu do rejestru  
  
 Należy pamiętać, że dostawca jądra można włączyć tylko. Nie można wyłączyć ani jej flag można modyfikować, dopóki zamknięcie monitora.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Po włączeniu zdarzenia CLR ETW uruchamiania dodatkowych danych również są zbierane w śledzenia Wyświetl raport. Aby wykluczyć zdarzenia uruchamiania były wyświetlane w raporcie, użyj następującego polecenia:  
  
```cmd  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Jeśli zdarzenia uruchamiania nie jest wykluczone, ponieważ te zdarzenia nie są wymienione w pliku Managed Object Format (MOF), ich widoczny jako identyfikatorów GUID w raporcie. Aby uzyskać więcej informacji, zobacz tę stronę w witrynie sieci Web firmy Microsoft: [plik przykładowy Managed Object Format (MOF)](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)