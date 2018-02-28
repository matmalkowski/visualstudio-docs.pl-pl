---
title: IDiaInjectedSource::get_source | Dokumentacja firmy Microsoft
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
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c58989c6958aa8a604f5e7c7a9ef5c4d3eb84f1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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