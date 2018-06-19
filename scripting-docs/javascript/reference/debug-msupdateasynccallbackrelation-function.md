---
title: Funkcja Debug.msUpdateAsyncCallbackRelation | Dokumentacja firmy Microsoft
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
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c47ed7f6313646dddf86dd766d7f1027b2d38ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790375"
---
# <a name="debugmsupdateasynccallbackrelation-function"></a>Funkcja Debug.msUpdateAsyncCallbackRelation
Aktualizuje stan relacji między elementem pracy synchroniczne i skojarzone operację asynchroniczną.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### <a name="parameters"></a>Parametry  
 `relatedAsyncOperationId`  
 Wymagany. Identyfikator skojarzony z operacji asynchronicznej.  
  
 `relationType`  
 Opcjonalny. Wartość, która określa stan relacji.  
  
## <a name="remarks"></a>Uwagi  
 Element roboczy synchroniczne jest zwykle funkcja wywołania zwrotnego dla operacji asynchronicznej. Ta funkcja może zostać wywołana, gdy operacja asynchroniczna została przerwana podczas operacji tworzenia sprzężenia jest używany, lub w innych scenariuszach.  
  
 Możliwe wartości `relationType` obejmują:  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 Aby uzyskać więcej informacji, zobacz [stałe debugowania](../../javascript/reference/debug-constants.md).  
  
> [!NOTE]
>  Niektóre narzędzia debugowania nie są wyświetlane informacje wysyłane do debugera przez tę funkcję.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]