---
title: Metoda IActiveScriptProfilerHeapEnum::GetOptionalInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6ad237f2feb173408e895984dab7e7455004d16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793498"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>Metoda IActiveScriptProfilerHeapEnum::GetOptionalInfo
Pobiera opcjonalne informacje w określonym obiekcie (z zestawu sterty obiektów zwracanych z [metoda IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Nie powinna zwolnić zwrócony pamięć przypisana do zwracanych obiektów. Zamiast tego należy wywołać [metoda IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 `heapObject`  
 [Struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) której informacje.  
  
 `celt`  
 Liczba [struktura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) struktury do zwrócenia.  
  
 `optionalInfo`  
 [out] Tablica [struktura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) struktur dla określonego obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 HRESULT.