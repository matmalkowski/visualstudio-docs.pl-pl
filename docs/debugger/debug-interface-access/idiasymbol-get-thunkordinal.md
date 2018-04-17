---
title: IDiaSymbol::get_thunkOrdinal | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e00c2287d00859d25d740c7c7c011518c0746442
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Pobiera typ thunk funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca wartość z zakresu od [thunk_ordinal — wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md) wyliczenia, który określa typ thunk funkcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest prawidłowa tylko wtedy, gdy symbol jako [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartość `SymTagThunk`.  
  
 "thunk" to fragment kodu, który wykonuje konwersję między przestrzeni adresowej pamięci 32-bitowej (znanej także jako płaska adres miejsca) i spacją 16-bitowego adresu (znany jako przestrzeń adresów segmentu).  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Thunk_ordinal — wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)