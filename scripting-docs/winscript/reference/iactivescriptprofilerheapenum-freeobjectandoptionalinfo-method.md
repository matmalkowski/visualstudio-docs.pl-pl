---
title: Metoda IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 748e5dbc948cc22e084a4e0b1e13222174bb739e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilerheapenumfreeobjectandoptionalinfo-method"></a>Metoda IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo
Zwalnia określony [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) struktury i skojarzone z nimi [struktura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FreeObjectAndOptionalInfo (    [in] ULONG celt,    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 Liczba obiektów zwolnienia.  
  
 `heapObjects`  
 Tablica [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 HRESULT.