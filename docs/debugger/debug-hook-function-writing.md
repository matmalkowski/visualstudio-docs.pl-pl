---
title: Pisanie funkcji punktów zaczepienia debugowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 365196a01ba9e62ef0b26eb3a99278d4d77a4dd4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457345"
---
# <a name="debug-hook-function-writing"></a>Pisanie debugowanie funkcji punktów zaczepienia
W tej sekcji opisano różne niestandardowych debugowania funkcji punktów zaczepienia, który może zapisać umożliwiające Wstaw kod w niektórych punktach wstępnie zdefiniowane wewnątrz normalnego przetwarzania debugera.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcje punktu zaczepienia bloku klienta](../debugger/client-block-hook-functions.md)  
 Zawiera również wskazówki i prototyp do pisania funkcji, które sprawdza, czy lub zawartości danych przechowywanych w blokach _client_block — raport.  
  
 [Funkcje punktu zaczepienia alokacji](../debugger/allocation-hook-functions.md)  
 Definiuje funkcję punktu zaczepienia alokacji, Eksploruje różnych zastosowań, punkty ograniczenia i udostępnia prototypu.  
  
 [Punkty zaczepienia alokacji i alokacji pamięci CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 Opisuje ograniczenia w funkcji punktów zaczepienia alokacji jawnie zignorowanie `_CRT_BLOCK` blokuje nawiązując wszelkie wywołania funkcji biblioteki wykonawczej języka C przydzielania pamięci wewnętrznej. W tym temacie wymieniono także konsekwencje Jeśli Twoje punktu zaczepienia alokacji pomija `_CRT_BLOCK` bloków (wraz z przykładami) i jak zmienić Alokacja domyślna utworzenie punktu zaczepienia funkcji **CrtDefaultAllocHook**.  
  
 [Raportowanie funkcji punktów zaczepienia](../debugger/report-hook-functions.md)  
 W tym artykule omówiono `_CrtSetReportHook`, które służy do filtrowania raportów skupić się na określonych typów przydziałów. Ten temat zawiera również prototypu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)  
 Łącza do debugowania techniki biblioteki C Run-Time, łącznie z biblioteki debugowania CRT, makra raportowania, różnice między `malloc` i `_malloc_dbg`, pisanie debugowanie funkcji punktów zaczepienia i sterty debugowania CRT.