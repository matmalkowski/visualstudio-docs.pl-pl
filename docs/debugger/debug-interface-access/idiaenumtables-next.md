---
title: IDiaEnumTables::Next | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1a2a3d208bc430f95d003dfd40c5831cabf7d2c5
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Pobiera określoną liczbę tabel w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba tabel w moduł wyliczający, które mają zostać pobrane.  
  
 `rgelt`  
 [out] Tablica, która ma być wypełnione przy użyciu [idiatable —](../../debugger/debug-interface-access/idiatable.md) obiekty reprezentujące żądaną tabel.  
  
 `pceltFetched`  
 [out] Zwraca liczbę tabel w pobranych modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie ma żadnych więcej tabel. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumtables —](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)