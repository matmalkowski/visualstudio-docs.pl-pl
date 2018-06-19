---
title: Struktura PROFILER_HEAP_OBJECT_SCOPE_LIST | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67f0972faee11e15bd5d0e9a219e439df49d9672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796444"
---
# <a name="profilerheapobjectscopelist-structure"></a>Struktura PROFILER_HEAP_OBJECT_SCOPE_LIST
Ta struktura jest skojarzony z tylko obiekty funkcji. Na liście zakresu reprezentuje zamknięcia funkcji jako lista zakresów każdego zakresu, w przypadku obiektu sterty z listy skojarzonej właściwości reprezentujący zmienne w każdym w danym zakresie. W niektórych przypadkach nazwy obiektów w zakresie będą niedostępne, a tylko ich indeks w liście właściwość jest dostępna.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Typ|Opis|  
|------------|----------|-----------------|  
|count|UINT|Liczba zakresów|  
|scopes|[Typ PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Tablica zakresów.|