---
title: Funkcja Debug.msTraceAsyncOperationStarting | Dokumentacja firmy Microsoft
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
ms.assetid: c8458264-07e0-4cd6-8528-ff7cf009cf9e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a50c58e352d40a06192664cdf7424348be02d466
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790390"
---
# <a name="debugmstraceasyncoperationstarting-function"></a>Funkcja Debug.msTraceAsyncOperationStarting
Inicjuje śledzenia dla operacji asynchronicznej.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.msTraceAsyncOperationStarting(operationName)  
```  
  
#### <a name="parameters"></a>Parametry  
 `operationName`  
 Wymagany. Ciąg, który identyfikuje operację asynchroniczną. Jeśli `operationName` ma wartość null lub niezdefiniowana, pusty ciąg jest używany dla nazwy operacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba całkowita reprezentująca identyfikator operacji.  
  
## <a name="remarks"></a>Uwagi  
 Tę metodę należy wywołać przed uruchomieniem operacji asynchronicznej.  
  
> [!NOTE]
>  Niektóre narzędzia debugowania nie są wyświetlane informacje wysyłane do debugera.  
  
## <a name="example"></a>Przykład  
 Poniższy kod stanowi przykład Instrumentacja wywołanie asynchroniczne dla [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji.  
  
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