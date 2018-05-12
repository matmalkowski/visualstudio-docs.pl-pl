---
title: WinCounter | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4751d44afc2f54ea57866e3674a5bc150444088b
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="wincounter"></a>WinCounter
**WinCounter** opcja określa systemu Windows lub licznika wydajności aplikacji do zbierania w ustalonych odstępach czasu w profilu Uruchom. System Windows i liczniki wydajności aplikacji są wyświetlane jako znaki w pliku danych profilowania. Można określić wiele liczników wydajności zbierania oddzielne opcje.  
  
 Domyślnie są zbierane liczniki co 500 milisekund. Użyj **AutoMark** opcję, aby określić interwał innej kolekcji.  
  
 Tylko jeden **AutoMark** jest używana opcja. Jeśli wiele **AutoMark** opcje są określone, ostatnie jest używany.  
  
 **WinCounter** opcja może być używana tylko z **Start** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Path`  
 Licznik wydajności systemu Windows w formacie ścieżki licznika PDH.  
  
## <a name="required-options"></a>Wymagane opcje  
 **WinCounter** opcja może być używana tylko z **Start** opcji.  
  
 **Uruchom:** `Method`  
 **Start** opcji inicjowania profilera do określonej metody profilowania.  
  
## <a name="exclusive-options"></a>Wykluczających się opcji  
 **AutoMark** opcja może być używana tylko z **WinCounter** opcji.  
  
 **AutoMark:** `Milliseconds`  
 Określa liczbę milisekund między zbieranie danych licznika wydajności systemu Windows.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie dwa liczniki wydajności systemu Windows określono mają być zbierane z interwałem 1000 milisekund.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)