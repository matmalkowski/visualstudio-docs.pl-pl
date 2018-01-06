---
title: IDiaSymbol::get_isAggregated | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9aed3df2d960c8c2a85e642fe9e1487861bcfe08
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetisaggregated"></a>IDiaSymbol::get_isAggregated
Pobiera flagę określającą, czy symbol danych jest częścią agregacji lub zbiór symbolami; kompilator będzie traktować zagregowane symboli jako osobne jednostki, ale naprawdę są częścią tego samego symbolu większy.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_isAggregated(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFlag`  
 [out] Zwraca `TRUE` Jeśli danych jest częścią agregacji symboli od symbolu nadrzędnego; w przeciwnym razie zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="remarks"></a>Uwagi  
 [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) jest metoda `TRUE` dla symbol, który jest elementem nadrzędnym zagregowane symboli.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|DIA SDK w wersji 8.0|  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)