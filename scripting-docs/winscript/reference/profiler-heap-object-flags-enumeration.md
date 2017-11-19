---
title: Wyliczenie PROFILER_HEAP_OBJECT_FLAGS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96e05d67bedcf03c97edc1015c80b212b6021562
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectflags-enumeration"></a>Wyliczenie PROFILER_HEAP_OBJECT_FLAGS
Flagi, które reprezentują podstawowe informacje o obiekcie stosu. Używane w [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,} PROFILER_HEAP_OBJECT_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT|0x00000001|Ten obiekt sterty została przydzielona po poprzednie żądanie wyliczenia stosu. [Typ PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md) wartości mogą być ponownie używane, jeśli obiekt są zbierane.|  
|PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT|0x00000002|Ten obiekt sterty jest obiektem głównym wykresu obiektu.|  
|PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED|0x00000004|Ten obiekt sterty jest z witryny skryptu, który został zamknięty.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL|0x00000008|Ten obiekt sterty została przydzielona poza sterty JavaScript wyrzucania elementów w kolekcji.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN|0x00000010|Ten obiekt sterty została przydzielona poza pamięci sterty kolekcji i implementuje IUnknown.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH|0x00000020|Ten obiekt sterty została przydzielona poza pamięci sterty kolekcji i implementuje interfejs IDISPATCH.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE|0x00000040|Rozmiar tego obiektu sterty jest przybliżona.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE|x00000080|Rozmiar tego obiektu sterty jest niedostępny.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE|0x00000200|Obiekt sterty jest wystąpieniem środowiska wykonawczego systemu Windows.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS|0x00000400|Obiekt sterty jest klasa środowiska uruchomieniowego środowiska wykonawczego systemu Windows.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE|0x00000800|Obiekt sterty jest delegata środowiska wykonawczego systemu Windows.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE|0x00001000|Obiekt sterty znajduje się w przestrzeni nazw środowiska wykonawczego systemu Windows.|