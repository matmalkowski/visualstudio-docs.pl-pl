---
title: Wyliczenie PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fcb55f5f-ce75-4d05-9ce9-ba28c622f97d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a73d6917f78a85bee1471fc54b01d5e691be8cdc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796423"
---
# <a name="profilerheapobjectoptionalinfotype-enumeration"></a>Wyliczenie PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE
Reprezentuje różne rodzaje opcjonalne informacje. Używane w [struktura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE                    = 0x00000001,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME                = 0x00000002,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST                   = 0x00000003,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY            = 0x00000004,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES              = 0x00000005,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES             = 0x00000006,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE      = 0x00000007,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE   = 0x00000008,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS                = 0x00000009,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS                  = 0x0000000A,    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_MAX_VALUE                    = PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS} PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE|0x00000001|Informacje o prototypu obiektu heap.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME|0x00000002|Informacje o nazwę funkcji obiektu heap.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST|0x00000003|Informacje o obiektach sterty [struktura PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md).|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY|0x00000004|Informacje dotyczące stosu wewnętrznego obiektu.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES|0x00000005|Informacje o właściwości name obiektu heap.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES|0x00000006|Informacje o właściwości indeksu obiektu heap.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE|0x00000007|Rozmiar atrybuty, które są skojarzone z elementem modelu DOM.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE|0x00000008|Rozmiar tekstu, który jest skojarzony z elementem modelu DOM.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS|0x00000009|Informacje dotyczące relacji obiektu heap.|  
|ROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS|0x0000000A|Informacje o zdarzeniach środowiska uruchomieniowego systemu Windows obiektu heap.|  
|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_MAX_VALUE|PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS|Wartość maksymalna to wyliczenie.|