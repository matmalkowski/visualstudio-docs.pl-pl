---
title: Funkcja Debug.msTraceAsyncCallbackStarting | Dokumentacja firmy Microsoft
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
ms.assetid: 0e2ca7c4-103c-44f2-b76c-102fb1e42543
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49203cdf16e7cbd74493c882d9cf17b7629da79a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790384"
---
# <a name="debugmstraceasynccallbackstarting-function"></a>Funkcja Debug.msTraceAsyncCallbackStarting
Kojarzy stosu wywołania zwrotnego z wcześniej określonej operacji asynchronicznej.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.msTraceAsyncCallbackStarting(asyncOperationId)  
```  
  
#### <a name="parameters"></a>Parametry  
 `asyncOperationId`  
 Wymagany. Identyfikator skojarzony z operacji asynchronicznej.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji w funkcji wywołania zwrotnego asynchronicznej operacji po wywołaniu `Debug.msTraceAsyncOperationCompleted`.  
  
> [!NOTE]
>  Niektóre narzędzia debugowania nie są wyświetlane informacje wysyłane do debugera.  
  
 `asyncOperationId`Nazwa operacji, które wcześniej zostały zwrócone z musi odpowiadać `Debug.msTraceAsyncOperationStarting`.  
  
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