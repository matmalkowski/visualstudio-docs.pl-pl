---
title: Raport funkcji punktów zaczepienia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 562944404d3e02a2e5768fcd74c67302475e6190
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="report-hook-functions"></a>Raportowanie funkcji punktów zaczepienia
Raport funkcji punktów zaczepienia, zainstalować za pomocą [_crtsetreporthook —](/cpp/c-runtime-library/reference/crtsetreporthook), jest nazywany zawsze [_crtdbgreport —](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) generuje raport debugowania. Można użyć, między innymi do filtrowania raportów skupić się na określonych typów przydziałów. Raport funkcji punktów zaczepienia powinny mieć prototypu podobne do poniższych:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Wskaźnik, który jest przekazywany do **_crtsetreporthook —** jest typu **_crt_report_hook —**, zgodnie z definicją w CRTDBG. H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Gdy biblioteki wykonawczej wywołania funkcji punktów zaczepienia, *nRptType* argument zawiera kategorii raportu (**_CRT_WARN**, **_CRT_ERROR**, lub **_CRT _ASSERT**), *szMsg* zawiera wskaźnik do ciąg komunikatu raportu pełni złożony i *retVal* Określa, czy `_CrtDbgReport` powinno być kontynuowane normalnego wykonywania Po wygenerowaniu raportu lub uruchomieniu debugera. (A *retVal* wartość zero kontynuuje wykonywanie, wartość 1 uruchomienie debugera.)  
  
 Jeśli haku obsługi wiadomości w całkowicie, tak aby nie dalsze reporting jest wymagane, powinien on zwrócić **TRUE**. Jeśli zmienna zwraca **FALSE**, `_CrtDbgReport` będzie raportu zwykle wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie pisanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)   
 [Przykładowe crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)