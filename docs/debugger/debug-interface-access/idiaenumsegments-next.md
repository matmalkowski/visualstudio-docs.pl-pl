---
title: IDiaEnumSegments::Next | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 210976ad2cbe44d4f94758c9c1fe9d2216e7f44c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Pobiera określoną liczbę segmentów w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba segmentów w moduł wyliczający, które mają zostać pobrane.  
  
 rgelt  
 [out] Tablica, która ma być wypełnione z żądaną [idiasegment —](../../debugger/debug-interface-access/idiasegment.md) obiekty reprezentujące segmenty.  
  
 pceltFetched  
 [out] Zwraca liczbę segmentów w pobranych modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie ma żadnych więcej segmentów. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumsegments —](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [Idiasegment —](../../debugger/debug-interface-access/idiasegment.md)