---
title: Element JsPromiseContinuationCallback Typedef | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 762391cb66e5298bd70beb3238720d3717554ae0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788479"
---
# <a name="jspromisecontinuationcallback-typedef"></a>JsPromiseContinuationCallback Typedef
Wywołania zwrotnego promise kontynuacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `task`  
  `callbackState`  
  
## <a name="remarks"></a>Uwagi  
 Hosta można określić kontynuacji wywołania zwrotnego promise w `JsSetPromiseContinuationCallback`. Jeśli skrypt tworzy zadanie można uruchomić później, a następnie wywołania zwrotnego promise kontynuacji zostanie wywołana z zadaniem i zadania należy umieścić w kolejce FIFO, do uruchomienia po ukończeniu bieżącego skryptu wykonywania.  
  
 Ten interfejs API jest obsługiwana tylko w trybie krawędzi.  
  
## <a name="requirements"></a>Wymagania  
 jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)