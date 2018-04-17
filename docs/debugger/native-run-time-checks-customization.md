---
title: Natywny środowiska wykonawczego sprawdza dostosowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 2c0318a5a711fd99338fb3d4e812cb3b07c449fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="native-run-time-checks-customization"></a>Dostosowanie macierzystego sprawdzania w trakcie wykonywania
Podczas kompilacji z **/RTC** (sprawdzania w trakcie wykonywania) lub użyj `runtime_checks` pragma, biblioteki wykonawczej języka C zapewnia macierzystego sprawdzania w trakcie wykonywania. W niektórych przypadkach można dostosować sprawdzanie czasu wykonywania:  
  
-   Można przekierować wiadomości wyboru środowiska wykonawczego do pliku lub docelowej innej niż domyślna.  
  
-   Aby określić dane wyjściowe miejsce docelowe dla środowiska wykonawczego, sprawdź komunikaty w debugerze innych firm.  
  
-   Aby zgłosić wiadomości wyboru środowiska wykonawczego programu skompilowana przy użyciu wersji biblioteki wykonawcze języka C. Nie należy używać wersji biblioteki `_CrtDbgReportW` może raportować błędy czasu wykonywania. Zamiast tego są one wyświetlane **Assert** okno dialogowe dla każdego błędu czasu wykonywania.  
  
 Aby dostosować sprawdzanie błędów czasu wykonywania, można:  
  
-   Pisanie funkcji raportowania błędów czasu wykonywania. Aby uzyskać więcej informacji, zobacz [porady: pisanie funkcji raportowania błędów czasu wykonywania](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
-   Dostosowywanie docelowego komunikat błędu.  
  
-   Zapytanie o informacje czasu wykonywania Sprawdź błędy.  
  
## <a name="customize-the-error-message-destination"></a>Dostosowywanie docelowego komunikat błędu  
 Jeśli używasz `_CrtDbgReportW` może raportować błędy, można użyć `_CrtSetReportMode` do określenia lokalizacji komunikaty o błędach.  
  
 Jeśli używasz niestandardowego funkcję raportowania, należy użyć `_RTC_SetErrorType` do skojarzenia z typem raportu wystąpił błąd.  
  
## <a name="query-for-information-about-run-time-checks"></a>Zapytanie o informacji na temat sprawdzania w trakcie wykonywania  
 `_RTC_NumErrors` Zwraca liczbę typów błędów wykrytych przez sprawdzanie błędów czasu wykonywania. Aby uzyskać krótki opis każdego błędu, można pętli z zakresu od 0 do wartość zwracaną `_RTC_NumErrors`, przekazując wartość iteracji, aby `_RTC_GetErrDesc` na każdej pętli. Aby uzyskać więcej informacji, zobacz [_rtc_numerrors —](/cpp/c-runtime-library/reference/rtc-numerrors) i [_rtc_geterrdesc —](/cpp/c-runtime-library/reference/rtc-geterrdesc).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Użyj macierzystego sprawdzania w trakcie wykonywania](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](/cpp/preprocessor/runtime-checks)   
 [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)