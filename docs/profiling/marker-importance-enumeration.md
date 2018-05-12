---
title: marker_importance — wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f4c87cfa1504c997cefdc68416dac9923fa10b4
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="markerimportance-enumeration"></a>marker_importance — Wyliczenie
Reprezentuje poziom ważności znaczników wizualizatora współbieżności.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum marker_importance;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`critical_importance`|Określa, czy znacznika ma kluczowe znaczenie.|  
|`high_importance`|Określa, czy znacznika ma wysokiej ważności.|  
|`low_importance`|Określa, czy znacznika ma niskiej ważności.|  
|`normal_importance`|Określa, czy znacznika ma znaczenie normalnego.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkersobj.h  
  
 **Namespace:** CONCURRENCY::Diagnostic —  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw diagnostic](../profiling/diagnostic-namespace.md)