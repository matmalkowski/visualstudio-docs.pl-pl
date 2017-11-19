---
title: Funkcja JsCreateExternalArrayBuffer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95459f9a9ff676f47d56ed584ad44a30f24fd4cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jscreateexternalarraybuffer-function"></a>Funkcja JsCreateExternalArrayBuffer
Tworzy Javascript `ArrayBuffer` obiekt, aby uzyskiwać dostęp do zewnętrznych pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `data`  
 Wskaźnik do pamięci zewnętrznej.  
  
 `byteLength`  
 Liczba bajtów w pamięci zewnętrznej.  
  
 `finalizeCallback`  
 Wywołanie zwrotne dla gdy obiekt jest zakończona. Może mieć wartość zerową.  
  
 `callbackState`  
 Stan, który zostanie przekazany do finalizeCallback podane przez użytkownika.  
  
 `result`  
 Nowe `ArrayBuffer` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)