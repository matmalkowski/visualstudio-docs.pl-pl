---
title: "Stałe debugowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2c50181dc9f40d8665d6caca407232231682d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="debug-constants"></a>Stałe debugowania
Debugowanie stałe zwracany stałe wartości, które są właściwościami `Debug` obiektu.  
  
## <a name="debug-object-constants"></a>Obiekt stałe debugowania  
 W poniższej tabeli wymieniono stałe wartości, które są właściwościami [obiektu debugowania](../../javascript/reference/debug-object-javascript.md).  
  
|Stała|Opis|Wartość|  
|--------------|-----------------|-----------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|Element roboczy synchroniczne przypisane wywołania zwrotnego lub kontynuacji do uruchomienia przez operację asynchroniczną.|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|Element roboczy synchroniczne spełnione częścią sprzężenia operację asynchroniczną.|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|Element roboczy synchroniczne spełnione wybór operację asynchroniczną.|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|Element roboczy synchronicznego zostało anulowane.|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|Element roboczy synchroniczne spowodował błąd w operacji asynchronicznej.|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|Operacja asynchroniczna powiodło się.|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|Operacja asynchroniczna została anulowana.|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|Operacja asynchroniczna spowodowało wystąpienie błędu.|3|  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcja Debug.msTraceAsyncOperationCompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Funkcja Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)