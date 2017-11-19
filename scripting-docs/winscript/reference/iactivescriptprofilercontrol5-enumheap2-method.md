---
title: "IActiveScriptProfilerControl5::EnumHeap2 — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c493acdb2843877c506d9d84e145a79ac2d60d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2 — Metoda
Zwraca interfejs ([interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) który może służyć do wykonywania iteracji w kontekście aparat skryptu skojarzone obiekty sterty GC.  
  
 Można wywołać tę metodę w obu debugowania lub wyłączenie trybu. Ta metoda powinna być wywoływana, gdy wątku interfejsu użytkownika jest w stanie bezczynności. Po wywołaniu metody, nie ma operacji należy wykonać przed aparat skryptu, z wyjątkiem [metoda IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) do momentu [metoda IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)zwraca wartości S_FALSE lub [interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) zwolnieniu wskaźnika interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametry  
 enumFlags  
 Wartość określająca, czy dodatkowych informacji na temat obiektu wskazywana w obiekcie relacji jest widoczna. Dodatkowe informacje może wskazywać, czy obiekt wskazywany jest metody ustawiającej lub metody pobierającej. Aby uzyskać więcej informacji, zobacz [profiler_heap_enum_flags — wyliczenie](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Zwraca [interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT. Dopuszczalne są następujące wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Wyliczenie sterty, została ukończona pomyślnie.|  
|`E_OUTOFMEMORY`|Nie był wystarczająco dużo dostępnej pamięci do przeprowadzenia wyliczenie sterty.|  
|`E_FAIL`|Wystąpił błąd wewnętrzny.|