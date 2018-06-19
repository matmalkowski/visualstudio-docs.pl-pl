---
title: Sprawdza przy użyciu czasu wykonywania bez biblioteki wykonawczej języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 533e4254b6222af1713691a0c448cad1383cd273
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481762"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Korzystanie ze sprawdzania w trakcie wykonywania bez biblioteki wykonawczej języka C
Możesz połączyć program bez biblioteki wykonawczej języka C, za pomocą **/nodefaultlib**i chcesz używać sprawdzania w trakcie wykonywania, należy połączyć z RunTmChk.lib.  
  
 `_RTC_Initialize` Inicjuje program na potrzeby sprawdzania w trakcie wykonywania. Jeśli nie zostanie połączony z biblioteki wykonawczej języka C, musisz sprawdzić, aby zobaczyć, czy program ma być kompilowana z sprawdzanie błędów czasu wykonywania przed wywołaniem `_RTC_Initialize`w następujący sposób:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Jeśli nie możesz połączyć z biblioteki wykonawczej języka C, również muszą definiować funkcji o nazwie `_CRT_RTC_INITW`. `_CRT_RTC_INITW` funkcja zdefiniowana przez użytkownika jest instalowany jako błąd domyślny raportowania funkcji, w następujący sposób:  
  
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
  
 Po zainstalowaniu funkcji raportowania błędów domyślne, można zainstalować dodatkowe funkcje z raportowania `_RTC_SetErrorFuncW`. Aby uzyskać więcej informacji, zobacz [_rtc_seterrorfuncw —](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Użyj macierzystego sprawdzania w trakcie wykonywania](../debugger/how-to-use-native-run-time-checks.md)