---
title: Element JsProjectionEnqueueCallback Typedef | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bda4a3a80edac38ab2c3885c2256cdf9d03eb8c1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788392"
---
# <a name="jsprojectionenqueuecallback-typedef"></a>JsProjectionEnqueueCallback Typedef
Wywołanie zwrotne aplikacji, która jest wywoływana przez JsRT, po zakończeniu projekcji interfejsu API w innym wątku niż oryginalna.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `jsCallback`  
 Wywołanie zwrotne do wywołania w oryginalnym wątku.  
  
 `jsContext`  
 Kontekst aplikacji.  
  
 `callbackState`  
 Kontekst JsRT, które muszą być przekazywane do `jsCallback`.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga wywołania metody jssetprojectionenqueuecallback — na odbieranie wywołań zwrotnych.  
  
 Ten interfejs API jest obsługiwana tylko w trybie krawędzi.  
  
## <a name="requirements"></a>Wymagania  
 jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)