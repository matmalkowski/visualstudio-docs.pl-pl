---
title: Cvleavespan — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 381a6742dbedbe50b350764ca9e2637895db7ae2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="cvleavespan-function"></a>CvLeaveSpan — Funkcja
Oznacza koniec zakresu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvLeaveSpan(  
   _In_ PCV_SPAN pSpan  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSpan`  
 Obiekt zakresu zwrócony przez poprzednie wywołanie cventerspan — *. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, gdy wiadomość zostanie pomyślnie zapisany. Kod błędu w przypadku, gdy było żadnych błędów. Użyj makra powiodło się/nie powiodło się, aby sprawdzić warunku błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)