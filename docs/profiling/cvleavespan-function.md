---
title: "Cvleavespan — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkers/CvLeaveSpan
helpviewer_keywords: CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1886858cfedbb3651a394b9f739feadd6c77d1a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Odwołanie do biblioteki C++](../profiling/cpp-library-reference.md)