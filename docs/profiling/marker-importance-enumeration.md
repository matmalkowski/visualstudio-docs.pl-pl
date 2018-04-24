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
ms.openlocfilehash: 4b193ff33d979917342679e115cdb973cb3b7ad5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="markerimportance-enumeration"></a>marker_importance — Wyliczenie
Reprezentuje poziom ważności znaczników wizualizatora współbieżności.  
  
## <a name="syntax"></a>Składnia  
  
```  
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