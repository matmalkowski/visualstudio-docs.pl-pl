---
title: Funkcje punktu zaczepienia alokacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: b87c41a6a31a2c66663ed121204611b4964b9c4d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="allocation-hook-functions"></a>Funkcje punktu zaczepienia alokacji
Funkcja punktu zaczepienia alokacji, zainstalować za pomocą [_crtsetallochook —](/cpp/c-runtime-library/reference/crtsetallochook), jest nazywany każdorazowo przydzielone, ponownie przydzielić lub zwolnienie pamięci. Ten rodzaj punktu zaczepienia może służyć do wielu różnych celów. Użyj go do testowania, jak aplikacja obsługuje sytuacjach za mało pamięci, na przykład, lub zbadać wzorce alokacji lub alokacji informacji w celu późniejszej analizy.  
  
> [!NOTE]
>  Należy pamiętać o ograniczenia dotyczące używania funkcji biblioteki wykonawczej języka C w funkcji punktów zaczepienia alokacji, opisanego w [przechwytuje alokacji i C Run-Time pamięci alokacji](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Funkcja alokacji musi mieć prototypu podobne do poniższych:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Wskaźnik, który jest przekazywany do [_crtsetallochook —](/cpp/c-runtime-library/reference/crtsetallochook) jest typu **_crt_alloc_hook —**, zgodnie z definicją w CRTDBG. H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Po biblioteki wykonawczej programu haku *nAllocType* argument wskazuje alokacji, jakie ma zostać wykonana operacja (**_HOOK_ALLOC**, **_HOOK_REALLOC**, lub **_HOOK_FREE**). W przypadku bezpłatny lub ponowne przydzielenie `pvData` zawiera wskaźnik do tematu użytkownika bloku o ma zostać zwolniony. Jednak w przypadku alokacji ten wskaźnik ma wartość null, ponieważ nie przeprowadzono jeszcze alokacji. Pozostałe argumenty zawierają rozmiar alokacji danego, jego typ bloku numer sekwencyjny żądania skojarzone z i wskaźnika do pliku nazwę i numer wiersza w których alokacji została wprowadzona, jeśli jest dostępna. Po funkcji punktów zaczepienia wykonuje niezależnie od analizy i inne zadania chce jego autora, aplikacja musi zwracać jedną **TRUE**, co oznacza, że można kontynuować operacji alokacji, lub **FALSE**, wskazujące który operacja powinna zakończyć się niepowodzeniem. Proste haku tego typu może sprawdzić ilość pamięci przydzielonej do tej pory i zwracać **FALSE** Jeśli wielkość przekracza limit mała. Następnie doświadczenie rodzaju błędów alokacji, które normalnie mogą się pojawić tylko wtedy, gdy ilość dostępnej pamięci zostało bardzo niskich aplikacji. Punkty zaczepienia bardziej złożonych może informacji o alokacji wzorce, analiza użycia pamięci lub Raportuj, gdy wystąpić w następujących sytuacjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty zaczepienia alokacji i alokacji pamięci środowiska wykonawczego języka C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Debugowanie pisanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)   
