---
title: IDiaEnumSymbolsByAddr::Prev | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c9d2309b2cb8343cfb964e2bd90f196497c4dfef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Pobiera symbole poprzedniej w kolejności według adresu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba symboli w moduł wyliczający, które mają zostać pobrane.  
  
 rgelt  
 [out] Tablica, która ma być wypełnione przy użyciu [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekty reprezentujące żądaną symboli.  
  
 pceltFetched  
 [out] Zwraca liczbę symboli w pobranych modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` przypadku żadnych poprzednich symboli. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda aktualizuje pozycja modułu wyliczającego liczba pobranych elementów.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumsymbolsbyaddr —](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)