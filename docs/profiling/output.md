---
title: Dane wyjściowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e5b588100666f54d4345c15bc3278cf4bf2b3054
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="output"></a>Dane wyjściowe
**Dane wyjściowe** opcji określa nazwę pliku danych profilowania dla sesji wydajności. **Dane wyjściowe** musi być używany z **Start** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `FileName`  
 Nazwa pliku danych. Ścieżki pełne i częściowe są akceptowane. Jeśli ścieżka nie zostanie określona, plik jest tworzony w bieżącym katalogu.  
  
## <a name="required-options"></a>Wymagane opcje  
 **Dane wyjściowe** opcji należy używać z **Start** opcji.  
  
 **Uruchom:** `Method`  
 Określa nazwę pliku wyjściowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie utworzono plik danych profilowania w bieżącym katalogu.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)