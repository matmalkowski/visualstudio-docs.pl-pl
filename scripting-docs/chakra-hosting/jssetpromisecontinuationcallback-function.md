---
title: "Jssetpromisecontinuationcallback — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6ef0faf4-1500-4bd9-aeca-c208492af8ea
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c20b5c81bd34a44158a975f0c1aed88614e01022
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jssetpromisecontinuationcallback-function"></a>JsSetPromiseContinuationCallback — funkcja
Ustawia funkcji wywołania zwrotnego promise kontynuacji, która jest wywoływana przez kontekst, gdy zadanie musi znajdować się w kolejce do wykonania przyszłych.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsSetPromiseContinuationCallback(  
   _In_ JsPromiseContinuationCallback promiseContinuationCallback,  
   _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `promiseContinuationCallback`  
 Funkcja wywołania zwrotnego ustawiany.  
  
 `callbackState`  
 Użytkownik podał stanu, który zostanie przekazany do wywołania zwrotnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga kontekstu aktywnego skryptu.  
  
 Ten interfejs API jest obsługiwana tylko w trybie krawędzi.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)