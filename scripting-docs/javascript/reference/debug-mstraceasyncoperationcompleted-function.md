---
title: Funkcja Debug.msTraceAsyncOperationCompleted | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 9b628b71-61f1-478a-857f-5e1f607db56c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41370257042a2de50d21eba51c299198a6bfb72a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790378"
---
# <a name="debugmstraceasyncoperationcompleted-function"></a>Funkcja Debug.msTraceAsyncOperationCompleted
Wskazuje, że operacja asynchroniczna została ukończona.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.msTraceAsyncOperationCompleted(asyncOperationId, status)  
```  
  
#### <a name="parameters"></a>Parametry  
 `asyncOperationId`  
 Wymagany. Identyfikator skojarzony z operacji asynchronicznej.  
  
 `status`  
 Opcjonalny. Stan operacji asynchronicznej. Jeśli nie zostanie określony, `Debug.MS_ASYNC_OP_STATUS_SUCCESS` jest używany.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji po zakończeniu operacji asynchronicznej.  
  
 `asyncOperationId`musi odpowiadać operacji identyfikator wcześniej zostały zwrócone z `Debug.msTraceAsyncOperationStarting`.  
  
 Możliwe wartości `status` obejmują:  
  
-   `Debug.MS_ASYNC_OP_STATUS_SUCCESS`  
  
-   `Debug.MS_ASYNC_OP_STATUS_CANCELED`  
  
-   `Debug.MS_ASYNC_OP_STATUS_ERROR`  
  
> [!NOTE]
>  Niektóre narzędzia debugowania nie są wyświetlane informacje wysyłane do debugera.  
  
## <a name="example"></a>Przykład  
 Poniższy kod stanowi przykład śledzenia wywołanie asynchroniczne dla [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji.  
  
```JavaScript  
function asyncWrapperFunction() {  
    var opID = Debug.msTraceAsyncOperationStarting('async trace');  
    doSomethingAsync().then(function (result) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_SUCCESS);  
        Debug.msTraceAsyncCallbackStarting(opID);  
        // Process result of async operation.  
    }, function (error) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_ERROR);  
        Debug.msTraceAsyncCallbackStarting(opID);  
    });  
  
    Debug.msTraceAsyncCallbackCompleted();  
}  
  
function doSomethingAsync() {  
    return WinJS.Promise.as(true);  
}  
  
asyncWrapperFunction();  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]