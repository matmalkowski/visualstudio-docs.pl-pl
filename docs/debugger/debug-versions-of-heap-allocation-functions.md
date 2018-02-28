---
title: Wersja debugowania funkcji alokacji sterty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 63642402f6e98e42b2d4954a6065f61fb61159b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Wersja debugowania funkcji alokacji sterty
Biblioteki wykonawcze języka C zawiera specjalne wersje debugowania funkcji alokacji stosu. Te funkcje mają takie same nazwy co wydanie z _dbg dołączany do ich wersje. W tym temacie opisano różnice między wersji funkcji CRT i wersji _dbg przy użyciu `malloc` i `_malloc_dbg` jako przykłady.  
  
 Gdy [_DEBUG](/cpp/c-runtime-library/debug) jest zdefiniowany, CRT mapuje wszystkie [— funkcja malloc](/cpp/c-runtime-library/reference/malloc) wywołań [_malloc_dbg —](/cpp/c-runtime-library/reference/malloc-dbg). W związku z tym nie trzeba ponownie zapisuje przy użyciu kodu `_malloc_dbg` zamiast `malloc` uzyskanie korzyści podczas debugowania.  
  
 Należy wywołać `_malloc_dbg` jawnie, jednak. Wywoływanie `_malloc_dbg` jawnie niektóre dodał korzyści:  
  
-   Śledzenie `_CLIENT_BLOCK` typu alokacji.  
  
-   Przechowywanie plików i wierszy numer źródłowego której wystąpiło żądanie alokacji.  
  
 Jeśli nie chcesz konwertować z `malloc` wywołań `_malloc_dbg`, można uzyskać informacji o pliku źródłowym, definiując [_crtdbg_map_alloc —](/cpp/c-runtime-library/crtdbg-map-alloc), co powoduje, że mapa preprocesora bezpośrednio wszystkie wywołania `malloc` do `_malloc_dbg` zamiast polegania na otokę `malloc`.  
  
 Aby śledzić oddzielne typy alokacji w blokach klienta, należy wywołać `_malloc_dbg` bezpośrednio i ustaw `blockType` parametr `_CLIENT_BLOCK`.  
  
 Jeśli nie zdefiniowano _DEBUG, wywołań `malloc` nie zostaną zakłócone, wywołań `_malloc_dbg` ich do `malloc`, definicji [_crtdbg_map_alloc —](/cpp/c-runtime-library/crtdbg-map-alloc) zostanie zignorowana i w pliku informacji dotyczących źródła nie podano żądanie alokacji. Ponieważ `malloc` nie ma parametru typu bloku, żądania dotyczące `_CLIENT_BLOCK` typy są traktowane jako standardowe alokacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)