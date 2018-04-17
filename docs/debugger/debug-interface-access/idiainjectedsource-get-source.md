---
title: IDiaInjectedSource::get_source | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9d3019d7a2a36f032f4c1e68fa1e60adbe2fede
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Pobiera bajtów kodu źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbData`  
 [in] Liczba bajtów reprezentujący rozmiar buforu danych.  
  
 `pcbData`  
 [out] Zwraca liczbę bajtów reprezentujący bajtów zwracana. Jeśli `data` jest `NULL`, następnie `pcbData` jest całkowita liczba bajtów danych jest dostępna.  
  
 `data[]`  
 [out] Buforu, który ma zostać wypełnione bajtów źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)