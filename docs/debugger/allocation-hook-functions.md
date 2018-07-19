---
title: Funkcje punktu zaczepienia alokacji | Dokumentacja firmy Microsoft
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c8a051641811da3658ffe556982c67649704069
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433359"
---
# <a name="allocation-hook-functions"></a>Funkcje punktu zaczepienia alokacji
Funkcji podłączania alokacji zainstalowane za pomocą [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), jest wywoływana za każdym razem, gdy przydzielone, ponownie przydzielane lub zwolnienie pamięci. Ten typ punktu zaczepienia służy do wielu różnych celów. Go używać do testowania, jak aplikacja obsługuje sytuacje braku pamięci, takich jak do zbadania wzorców przydziału lub rejestrowania informacji o alokacji do późniejszej analizy.  
  
> [!NOTE]
>  Należy pamiętać o ograniczeń dotyczących używania funkcji biblioteki wykonawczej języka C w funkcji podłączania alokacji, opisanego w [punkty zaczepienia alokacji i alokacji pamięci środowiska wykonawczego języka C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Funkcji podłączania alokacji powinny mieć prototypu, jak w poniższym przykładzie:  
  
```cpp
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Wskaźnik, który jest przekazywany do [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) typu **_crt_alloc_hook —**, zgodnie z definicją w CRTDBG. GODZ.:  
  
```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Gdy biblioteka środowiska uruchomieniowego wywołuje usługi podłączania *nAllocType* argument wskazuje alokacji, jakie ma być przeprowadzana operacja (**_HOOK_ALLOC**, **_HOOK_REALLOC**, lub **_HOOK_FREE**). Bezpłatne lub ponowne przydzielenie `pvData` zawiera wskaźnik do tego artykułu użytkownika bloku, która będzie zwolniona. Jednak dla alokacji this, wskaźnik ma wartość null, ponieważ nie wystąpiła Alokacja. Pozostałe argumenty zawierają rozmiar alokacji w danym, jego typ bloku numeru sekwencyjnego żądania skojarzonego z, a także wskaźnik do nazwy pliku. Jeśli to możliwe, argumenty również obejmować numer wiersza, w którym wykonano alokacji. Po funkcja podłączania wykonuje niezależnie od analizy i inne zadania chce jego autora, aplikacja musi zwracać jedną **TRUE**, co oznacza, że można kontynuować operacji alokacji, lub **FALSE**oznaczający, operacja powinna zakończyć się niepowodzeniem. Proste punktu zaczepienia tego typu może sprawdzić ilość pamięci przydzielonej do tej pory i powrócić **FALSE** przekroczeniu limitu małych takimi problemami znacznie mniej. Aplikacja następnie doświadczenie rodzaju błędów alokacji, które normalnie mogą się pojawić tylko wtedy, gdy ilość dostępnej pamięci była bardzo niska. Bardziej złożone punkty zaczepienia może informacje o wzorcach alokacji, analiza użycia pamięci lub raportu po wystąpieniu określonych sytuacjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty zaczepienia alokacji i alokacji pamięci środowiska wykonawczego języka C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Debugowanie pisanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)   
