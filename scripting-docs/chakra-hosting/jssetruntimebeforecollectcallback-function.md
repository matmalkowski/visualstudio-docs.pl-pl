---
title: "Jssetruntimebeforecollectcallback — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeBeforeCollectCallback
helpviewer_keywords:
- JsSetRuntimeBeforeCollectCallback function
ms.assetid: 7b2fb911-6007-4ed9-a307-66cefe590ea4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 469b33a324f67d17bd6f5156da7cce169b98c663
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimebeforecollectcallback-function"></a>JsSetRuntimeBeforeCollectCallback — Funkcja
Ustawia funkcję wywołania zwrotnego, która jest wywoływana przez środowisko wykonawcze przed wyrzucanie elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeBeforeCollectCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsBeforeCollectCallback beforeCollectCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `runtime`  
 Środowisko uruchomieniowe, dla którego ma zostać zarejestrowany wywołania zwrotnego alokacji.  
  
 `callbackState`  
 Użytkownik podał stanu, który zostanie przekazany do wywołania zwrotnego.  
  
 `beforeCollectCallback`  
 Funkcja wywołania zwrotnego ustawiany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie zwrotne jest wywoływana w bieżącym wątku wykonywania środowiska uruchomieniowego, dlatego wykonywanie jest zablokowana do momentu ukończenia wywołania zwrotnego.  
  
 Wywołanie zwrotne mogą posłużyć hostów do przygotowania do wyrzucanie elementów bezużytecznych. Na przykład zwalniając niepotrzebne odwołania do obiektów Chakra.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)