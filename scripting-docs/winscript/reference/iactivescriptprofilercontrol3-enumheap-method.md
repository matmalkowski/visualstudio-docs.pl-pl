---
title: Metoda IActiveScriptProfilerControl3::EnumHeap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d6fc79a9d6d35e35181c3505e07af2d9a1962c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793453"
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>Metoda IActiveScriptProfilerControl3::EnumHeap
Zwraca interfejs ([interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) który może służyć do wykonywania iteracji w kontekście aparat skryptu skojarzone obiekty sterty GC.  
  
 Można wywołać tę metodę w obu debugowania lub wyłączenie trybu. Ta metoda powinna być wywoływana, gdy wątku interfejsu użytkownika jest w stanie bezczynności. Po wywołaniu metody, nie ma operacji należy wykonać przed aparat skryptu, z wyjątkiem [metoda IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) do momentu [metoda IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)zwraca wartości S_FALSE lub [interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) zwolnieniu wskaźnika interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametry  
 ppEnum  
 [out] Zwraca [interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 HRESULT.