---
title: "Dane wyjściowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b7452ad6aa8d7f190eebbc35d4be087c14dcd51a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="output"></a>Dane wyjściowe
**Dane wyjściowe** opcji określa nazwę pliku danych profilowania dla sesji wydajności. **Dane wyjściowe** musi być używany z **Start** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `FileName`  
 Nazwa pliku danych. Ścieżki pełne i częściowe są akceptowane. Jeśli ścieżka nie zostanie określona, plik jest tworzony w bieżącym katalogu.  
  
## <a name="required-options"></a>Wymagane opcje  
 **Dane wyjściowe** opcji należy używać z **Start** opcji.  
  
 **Start:**`Method`  
 Określa nazwę pliku wyjściowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie utworzono plik danych profilowania w bieżącym katalogu.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)