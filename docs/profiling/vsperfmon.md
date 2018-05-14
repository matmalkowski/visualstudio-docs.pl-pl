---
title: Vsperfmon — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be865f9fe51a1028192d54de556a52e47b241f0d
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="vsperfmon"></a>VSPerfMon
Vsperfmon — narzędzie służy do zbierania danych wydajności dla aplikacji; zwykle to narzędzie jest uruchamiana przez VSPerfCmd.exe. Vsperfmon — Wyświetla dodatkowe informacje o procesie dołączanie lub odłączanie, co nie jest możliwe za pomocą narzędzia VSPerfCmd. Aby wyświetlić te informacje, należy uruchomić vsperfmon — w osobnym oknie. Aby wywołać vsperfmon — użyj następującej składni:  
  
```cmd  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 W poniższej tabeli opisano vsperfmon — narzędzie Opcje:  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**U**|Konsola przekierowane dane wyjściowe są zapisywane jako Unicode.  Musi to być pierwszą określoną opcją.|  
|**Dane wyjściowe:** `<` *nazwy pliku* `>`|Przekierowuje do określonej nazwy pliku.|  
|**ŚLEDZENIA**|Uruchamia monitor wydajności dla instrumentowane profilowanie.|  
|**PRÓBKI**|Uruchamia monitor wydajności dla profilowanie próbkowania.|  
|**POKRYCIA**|Uruchamia monitor wydajności dla kolekcji pokrycia kodu.|  
|**WSPÓŁBIEŻNOŚĆ**|Uruchamia monitor wydajności dla profilowania kontencji zasobów.|  
|**Użytkownik:** `[` *domeny* `\]` *nazwy użytkownika*|Umożliwia dostęp klienta do monitora wydajności z określonego konta.|  
|**CROSSSESSION**|Włącza profilowanie krzyżowego sesji.|  
|**LICZNIK** `:cfg`|Gdy jest używana metoda profilowania Instrumentacji (śledzenia), określa licznika Procesora, które będą zbierane w każdym punkcie instrumentacji. Można zebrać danych w wielu liczników określając wiele opcji licznika.<br /><br /> Użyj następującej składni, aby określić licznika (*cfg*) dane:<br /><br /> **CounterName** [**, Załaduj ponownie**[,**FriendlyName**]]<br /><br /> -   **CounterName** jest nazwą licznika zwracanym przez polecenie /QueryCounters narzędzia VSPerfCmd.<br />-   **Załaduj ponownie** jest interwałem próbkowania licznika zdarzeń. Nie używaj *Załaduj ponownie* przy użyciu metody instrumentacji.<br />— W przypadku **FriendlyName** zastępuje **CounterName** w narzędziach profilowania zgłosić nazw kolumn.|  
|**WINCOUNTER** `:path`|Określa licznik wydajności systemu Windows, aby uwzględnić znak danych. `path` jest to ciąg licznika wydajności systemu Windows w formacie ścieżki licznika PDH. Na przykład:<br /><br /> \Processor(0)\\czas procesora (%)<br /><br /> \System\Context przełączniki/s|  
|**AUTOMARK** `:n`|Określa interwał (w milisekundach) między znakami automatyczne, gdy używasz /WINCOUNTER. Zaokrąglone do najbliższych 500 MS.<br /><br /> Użyj wartości 0, aby wyłączyć automatyczne znaczniki. (domyślna 500 ms)|  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Widoki raportu wydajności](../profiling/performance-report-views.md)