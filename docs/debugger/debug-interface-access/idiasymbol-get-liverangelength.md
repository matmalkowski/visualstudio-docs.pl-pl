---
title: IDiaSymbol::get_liveRangeLength | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeLength
ms.assetid: ffcce3cc-085c-44eb-8145-46e3819c54f9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f6668a5c33c34ffce3cdebba0802c57e9bbf598a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetliverangelength"></a>IDiaSymbol::get_liveRangeLength
Zwraca długość zakresu adresów, w którym symbol lokalnego jest poprawna.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_liveRangeLength (   
   ULONGLONG* length  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `length`  
 [out] Zwraca długość zakresu adresów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
> [!NOTE]
>  Zwrócony kod błędu oznacza, że symbol nie ma informacji o zakresie na żywo.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia100.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)