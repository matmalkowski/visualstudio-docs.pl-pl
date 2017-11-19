---
title: IDiaSymbol::get_length | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_length method
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94cdb52f21a5dd8a6bc41eaf21092013abffdc3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetlength"></a>IDiaSymbol::get_length
Pobiera liczbę bitów lub bajty pamięci używanej przez obiekt reprezentowany przez ten symbol.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_length (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca liczbę bajtów lub bitów pamięci używanej przez obiekt reprezentowany przez ten symbol.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) symbolu jest `LocIsBitField`, długość zwróconych przez tę metodę w bitach; w przeciwnym razie jest długość w bajtach dla wszystkich typów lokalizacji.  
  
## <a name="example"></a>Przykład  
  
```C++  
IDiaSymbol* pSymbol;  
ULONGLONG   length;  
pSymbol->get_length( &length );  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)