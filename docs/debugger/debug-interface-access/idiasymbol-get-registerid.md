---
title: IDiaSymbol::get_registerId | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f6a4583206666f90adb90cbebebf9417e66fc78
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
Pobiera oznaczeniem rejestru lokalizacji, gdy [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ma ustawioną wartość `LocIsEnregistered`.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca oznaczeniem rejestru lokalizacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli symbol jest określana względem rejestr, oznacza to, jeśli symbol [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ustawiono `LocIsRegRel`, użyj `get_registerId` metody następuje wywołanie [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) Metoda get przesunięcie z rejestru, w którym znajduje się symbol.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)