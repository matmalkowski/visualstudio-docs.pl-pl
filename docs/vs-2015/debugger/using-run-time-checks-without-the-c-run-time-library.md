---
title: Za pomocą środowiska wykonawczego sprawdza, czy bez biblioteki wykonawczej języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 864e21d2c2ec2a9922d70e6b69192d9268556737
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680225"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Korzystanie ze sprawdzania w trakcie wykonywania bez biblioteki wykonawczej języka C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [przy użyciu biblioteki czasu wykonywania sprawdza, czy bez C Run-Time](https://docs.microsoft.com/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).  
  
W przypadku połączenia programu bez biblioteki wykonawczej C za pomocą **/nodefaultlib**i chcesz używać do sprawdzania w trakcie wykonywania, należy połączyć z RunTmChk.lib.  
  
 `_RTC_Initialize` Inicjuje program do sprawdzania w trakcie wykonywania. Jeśli nie łączysz się z biblioteki wykonawczej języka C, należy musi Sprawdź, czy program został skompilowany z sprawdzanie błędów czasu wykonywania przed wywołaniem `_RTC_Initialize`, wykonując następujące czynności:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Jeśli nie możesz połączyć przy użyciu biblioteki wykonawczej języka C, należy zdefiniować funkcję o nazwie `_CRT_RTC_INITW`. `_CRT_RTC_INITW` funkcja zdefiniowana przez użytkownika jest instalowany jako błąd domyślny zgłoszenie funkcji w następujący sposób:  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 Po wykonaniu procedury instalacji funkcji raportowania błędów domyślne, można zainstalować dodatkowe błędów raportowania funkcje za pomocą `_RTC_SetErrorFuncW`. Aby uzyskać więcej informacji, zobacz [_RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Korzystanie z macierzystego sprawdzania w czasie wykonywania](../debugger/how-to-use-native-run-time-checks.md)





