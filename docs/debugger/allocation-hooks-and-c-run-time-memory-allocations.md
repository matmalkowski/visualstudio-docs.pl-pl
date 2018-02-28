---
title: "Punkty zaczepienia alokacji i alokacji pamięci środowiska wykonawczego języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b123e0e03f33f54e6d4fe82313c9a017e3baafff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Punkty zaczepienia alokacji i alokacja pamięci środowiska wykonawczego języka C
Bardzo ważne ograniczenie funkcji punktów zaczepienia alokacji jest, że jawnie należy zignorować `_CRT_BLOCK` blokach (wewnętrznie wprowadzone przez funkcje biblioteki wykonawczej języka C alokacji pamięci) nawiązując wszelkie wywołania funkcji biblioteki wykonawczej języka C, których alokacji pamięć. `_CRT_BLOCK` Bloki można zignorować przez dołączenie kodu, takie jak funkcji punktów zaczepienia na początku alokacji z następujących:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Jeśli Twoje punktu zaczepienia alokacji pomija `_CRT_BLOCK` blokuje, a następnie dowolnej funkcji biblioteki wykonawczej języka C w Twojej haku można przechwytywać programu w pętli nieskończonej. Na przykład `printf` sprawia, że przydział wewnętrznego. Jeśli kod punktu zaczepienia wywołuje `printf`, następnie wynikowy alokacji spowoduje, że Twoje haku ma być wywoływana ponownie, która wywoła **printf** ponownie, i tak dalej aż do przepełnienia stosu. Jeśli potrzebujesz raport `_CRT_BLOCK` operacji alokacji jednym ze sposobów obejścia tego ograniczenia jest używane funkcje interfejsu Windows API, zamiast funkcje wykonawcze języka C, formatowanie i danych wyjściowych. Ponieważ sterty biblioteki wykonawczej języka C nie używają interfejsów API systemu Windows, zostanie nie pułapki z punktu zaczepienia alokacji w pętli nieskończonej.  
  
 Jeśli pliki źródłowe biblioteki wykonawczej należy zbadać, zostanie wyświetlony czy funkcji punktów zaczepienia alokacji domyślne **CrtDefaultAllocHook** (która zwraca po prostu **TRUE**), znajduje się w oddzielnym pliku własnych, DBGHOOK. C. Jeśli chcesz, aby Twoje punktu zaczepienia alokacji wywoływanie nawet w przypadku przydziały kod uruchomienia środowiska wykonawczego, który jest wykonywany przed aplikacji **głównego** funkcji, można zastąpić to domyślna funkcja własny, zamiast przy użyciu [_crtsetallochook —](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie pisanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)   
