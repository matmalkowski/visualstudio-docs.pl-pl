---
title: Makra raportowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57b254323fac5d670cd44399cd8d22c9530c4510
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056605"
---
# <a name="macros-for-reporting"></a>Makra raportowania
W przypadku debugowania, można użyć **_rptn —** i **_rptfn —** makra zdefiniowane w CRTDBG. H, aby zastąpić użycie `printf` instrukcje. Nie trzeba je w inclose **#ifdef**s, ponieważ znikają one automatycznie w Twojej wersji podczas kompilacji **_DEBUG** nie jest zdefiniowany.  
  
|Macro|Opis|  
|-----------|-----------------|  
|**_RPT0 —**, **_RPT1 —**, **_RPT2 —**, **_RPT3 —**, **_RPT4 —**|Generuje ciąg z komunikatem i zera do czterech argumentów. Dla _rpt1 — za pośrednictwem **_rpt4 —**, ciąg z komunikatem służy jako ciąg formatowania stylu funkcji printf dla argumentów.|  
|**_RPTF0 —**, **_RPTF1 —**, **_RPTF2 —**, **_RPTF4 —**|Taki sam jak **_rptn —**, ale makra te dane wyjściowe pliku nazwę i numer wiersza którym znajduje się makra.|  
  
 Rozważmy następujący przykład:  
  
```cpp
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Ten kod wyświetla wartości `someVar` i `otherVar` do **stdout**. Można zastosować następujące wywołanie `_RPTF2` zgłoszenia te same wartości, a ponadto pliku nazwę i numer wiersza:  
  
```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
Może się okazać, że określonej aplikacji wymaga który makra dostarczony wraz z biblioteki wykonawczej języka C nie udostępniają raportowanie debugowania. W tych przypadkach można napisać makra zaprojektowany specjalnie w celu dopasowania do własnych wymagań. W jednym z plików nagłówka, na przykład możesz dołączyć kodu, takie jak następujące polecenie, aby zdefiniować makro o nazwie **ALERT_IF2**:  
  
```cpp
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 Jedno wywołanie **ALERT_IF2** może wykonać wszystkie funkcje **printf** kodu:  
  
```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Można łatwo zmienić makra niestandardowego do zgłaszania więcej lub mniej informacji do różnych miejsc docelowych. Ta metoda jest szczególnie przydatne jako rozwijać, wymagania dotyczące debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)
