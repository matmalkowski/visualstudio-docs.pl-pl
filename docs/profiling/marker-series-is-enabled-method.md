---
title: marker_series::is_enabled — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d7889fc8b02bcaa09ca1fb33efbd84e524695c0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="markerseriesisenabled-method"></a>marker_series::is_enabled — Metoda
Określa, czy dowolnej sesji jest włączony dostawca.  
  
## <a name="syntax"></a>Składnia  
  
```  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Importance`  
 Poziom ważności.  
  
 `_Category`  
 Kategoria.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkersobj.h  
  
 **Namespace:** CONCURRENCY::Diagnostic —  
  
## <a name="see-also"></a>Zobacz też  
 [marker_series, klasa](../profiling/marker-series-class.md)