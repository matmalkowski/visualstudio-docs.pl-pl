---
title: Profiler_heap_object_relationship_flags — wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab542225e0238dbd40f90d9de66d43d0791e05e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796357"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS — Wyliczenie
Flagi, które reprezentują czy obiektu heap wskazywana w obiekcie relacji jest metody ustawiającej lub metody pobierającej. Używane w [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) metody, gdy określona jest wartość profiler_heap_object_relationship_flags — w `enumFlags` parametru.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Ten obiekt sterty wskazywana w relacji obiektu nie jest rozpoznawany jako metody pobierającej lub ustawiającej.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|Obiekt sterty wskazywana w obiekcie relacji jest metody pobierającej. Te informacje będą przechowywane w wysokiej 2 bajty (16 bitów) z [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) pola.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|Obiekt sterty wskazywana w obiekcie relacji jest metody ustawiającej. Te informacje będą przechowywane w wysokiej 2 bajty (16 bitów) z `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` pola.|