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
ms.openlocfilehash: 0551545835a530ae63d53f8988ef89aab6476293
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="markerseriesisenabled-method"></a>marker_series::is_enabled — Metoda
Określa, czy dowolnej sesji jest włączony dostawca.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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