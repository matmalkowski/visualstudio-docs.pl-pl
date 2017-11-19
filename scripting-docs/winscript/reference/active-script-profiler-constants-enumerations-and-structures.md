---
title: "Stałe profilera aktywnego skryptu, wyliczenia i struktury | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a37f64b14d0d732e48de66bb5268d47c95426937
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Stałe, wyliczenia i struktury profilera aktywnego skryptu
Następujące wyliczenia są używane przez aktywne interfejsy profilera skryptu.  
  
## <a name="constants-enumerations-and-structures"></a>Stałe, wyliczenia i struktury  
  
|Stałe|Opis|  
|---------------|-----------------|  
|[Typ PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|Adres zewnętrzny obiekt profilera. Używane w [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) i [struktura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Typ PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Identyfikator obiektu heap. Używane w [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)[struktura PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [struktura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)i [Struktura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Typ PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|Identyfikator nazwy obiektu heap. Używane w [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Wyliczenia|Opis|  
|------------------|-----------------|  
|[Wyliczenie PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md)|Określa typy zdarzeń, które powinny być profilowane.|  
|[Profiler_heap_enum_flags — wyliczenie](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Flagi, które reprezentują czy dodatkowych informacji na temat obiektu sterty wskazywana w obiekcie relacji jest widoczne. Używane w [IActiveScriptProfilerControl5::EnumHeap2 — metoda](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[Wyliczenie PROFILER_HEAP_OBJECT_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Flagi, które reprezentują podstawowe informacje o obiekcie stosu. Używane w [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[Wyliczenie PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Reprezentuje różne rodzaje opcjonalne informacje. Używane w [struktura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[Wyliczenie PROFILER_RELATIONSHIP_INFO](../../winscript/reference/profiler-relationship-info-enumeration.md)|Reprezentuje informacje o obiektach w relacji. Używane w [struktura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Wyliczenie profiler_script_type Enumeration](../../winscript/reference/profiler-script-type-enumeration.md)|Określa typ skryptu.|  
  
|Struktury|Opis|  
|----------------|-----------------|  
|[Struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)|Reprezentuje obiektów sterty zebrane przez [metoda IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Struktura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Reprezentuje opcjonalne informacje o obiektach stosu.|  
|[Struktura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Reprezentuje relację obiektu heap.|  
|[Struktura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Reprezentuje listę relacje, które należą do obiektu heap.|  
|[Struktura PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Ta struktura jest skojarzony z tylko obiekty funkcji. Na liście zakresu reprezentuje zamknięcia funkcji jako lista zakresów każdego zakresu, w przypadku obiektu sterty z listy skojarzonej właściwości reprezentujący zmienne w każdym w danym zakresie. W niektórych przypadkach nazwy obiektów w tym zakresie mogą nie być dostępne, tylko ich identyfikatorów.|  
|[Struktura PROFILER_PROPERTY_TYPE_SUBSTRING_INFO](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Reprezentuje informacje o typie podciąg.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)