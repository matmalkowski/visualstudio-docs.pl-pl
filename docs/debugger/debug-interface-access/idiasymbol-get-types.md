---
title: IDiaSymbol::get_types | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6521d2a7ffdf5bb285f571e0d3975626f34d84d1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470039"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
Pobiera tablicę typów kompilatora specyficzne dla tego symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cTypes`  
 [in] Rozmiar buforu do przechowywania danych.  
  
 `pcTypes`  
 [out] Zwraca liczbę typów zapisywane, lub jeśli `types` parametr jest `NULL`, następnie całkowita liczba dostępnych typów.  
  
 `types[]`  
 [out] Tablica, która ma być wypełnione przy użyciu [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiektów, które reprezentują wszystkie typy dla tego symbolu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)