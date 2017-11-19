---
title: "Jssetprojectionenqueuecallback — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abdc575c5066ade4a700a0c88e09e3476a65366
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jssetprojectionenqueuecallback-function"></a>JsSetProjectionEnqueueCallback — funkcja
Ustawia wywołanie zwrotne do użycia w celu wywołania zakończenia projekcji, powrót do wątku wymagane obiekty wywołujące.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `projectionEnqueueContext`  
 Wywołanie zwrotne wywoływane zawsze, gdy występuje ukończenia projekcji wątku w tle.  
  
 `callbackState`  
 Kontekst aplikacji do `projectionEnqueueContext`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga kontekstu aktywnego skryptu.  
  
 Wywołanie powinien pochodzić z innego apartamentu COM lub z innego wątku, w tym samym MTA.  
  
 Ten interfejs API jest obsługiwana tylko w trybie krawędzi.  
  
> [!CAUTION]
>  PInvoke nie jest obecnie obsługiwana dla tego interfejsu API.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)