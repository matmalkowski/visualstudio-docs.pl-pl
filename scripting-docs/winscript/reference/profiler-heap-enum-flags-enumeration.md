---
title: Profiler_heap_enum_flags — wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a7a27f4d9d7f834b07a2db5ba8433b63222a3b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796387"
---
# <a name="profilerheapenumflags-enumeration"></a>PROFILER_HEAP_ENUM_FLAGS — Wyliczenie
Flagi, które reprezentują czy dodatkowych informacji na temat obiektu sterty wskazywana w obiekcie relacji jest widoczne. Używane w [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|Ten obiekt sterty nie ujawnia dodatkowych informacji na temat relacji obiektu. Ten obiekt stosu zachowuje się w taki sam sposób jak [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|Ten obiekt sterty będzie ujawnienie informacji o tym, czy obiekt wskazywana w relacji obiektu jest metoda ustawiająca lub metoda pobierająca. Te informacje będą przechowywane w wysokiej 2 bajty (16 bitów) z [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) pole jako jeden z [profiler_heap_object_relationship_flags —](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) wartości wyliczenia.|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|Ten obiekt sterty jest używany do poprawnego wyświetlania podciąg.|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|Ten obiekt sterty jest używany do poprawnego wyświetlania podciąg.|