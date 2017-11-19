---
title: Makra raportowania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.macros
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
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c977cd5af8714e6dc0fd07b70aba9cf7f40bfe06
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="macros-for-reporting"></a>Makra raportowania
Można użyć **_rptn —**, i **_rptfn —** makra zdefiniowane w CRTDBG. H, aby zastąpić użycie `printf` instrukcje do debugowania. Te makra automatycznie znikają w Twojej wersji podczas kompilacji **_DEBUG** nie jest zdefiniowana, a więc nie trzeba umieścić je w **#ifdef**s.  
  
|Makra|Opis|  
|-----------|-----------------|  
|**_RPT0 —**, **_RPT1 —**, **_RPT2 —**, **_RPT3 —**, **_RPT4 —**|Generuje ciąg z komunikatem i zera do czterech argumentów. Dla _rpt1 — za pośrednictwem **_rpt4 —**, ciąg z komunikatem służy jako ciąg formatowania stylu funkcji printf dla argumentów.|  
|**_RPTF0 —**, **_RPTF1 —**, **, _RPTF2 —**, **_RPTF4 —**|Taki sam jak **_rptn —**, ale makra te dane wyjściowe pliku nazwę i numer wiersza którym znajduje się makra.|  
  
 Rozważmy następujący przykład:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Ten kod wyświetla wartości `someVar` i `otherVar` do **stdout**. Można zastosować następujące wywołanie `_RPTF2` zgłoszenia te same wartości, a ponadto pliku nazwę i numer wiersza:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Jeśli okaże się, że określonej aplikacji wymaga debugowania raportowania, który makra dostarczony wraz z biblioteki wykonawczej języka C nie zostanie określona, można napisać makro zaprojektowany specjalnie w celu dopasowania do własnych wymagań. W jednym z plików nagłówka, na przykład możesz dołączyć kodu, takie jak następujące polecenie, aby zdefiniować makro o nazwie **ALERT_IF2**:  
  
```  
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
  
 Jedno wywołanie **ALERT_IF2** może wykonywać wszystkie funkcje **printf** kod na początku tego tematu:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Ponieważ makra niestandardowego można łatwo zmienić na bardziej lub mniej zgłaszanie informacji do różnych miejsc docelowych (w zależności od co to jest wygodniejsze), ta metoda może być szczególnie przydatne, jak rozwijać, wymagania dotyczące debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)