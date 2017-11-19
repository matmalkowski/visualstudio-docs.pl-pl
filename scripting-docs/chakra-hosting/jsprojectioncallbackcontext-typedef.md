---
title: Element JsProjectionCallbackContext Typedef | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7548dc14ab4b3dddc1633a1ba948aba564d8438a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsprojectioncallbackcontext-typedef"></a>JsProjectionCallbackContext Typedef
Kontekst przekazany do wywołania zwrotnego aplikacji, JsProjectionEnqueueCallback, z JsRT i następnie przekazywane z powrotem do JsRT w dostarczone wywołanie zwrotne `JsProjectionCallback`, przez aplikację na zorganizuj poprawny wątek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymaga wywołania `JsSetProjectionEnqueueCallback` na odbieranie wywołań zwrotnych.  
  
 Ten interfejs API jest obsługiwana tylko w trybie krawędzi.  
  
## <a name="requirements"></a>Wymagania  
 jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)