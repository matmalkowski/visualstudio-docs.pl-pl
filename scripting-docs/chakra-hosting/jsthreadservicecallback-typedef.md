---
title: "JsThreadServiceCallback — Typedef | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4b7ea4d0d5eaba17269a1777cdf96b5a2a5cda3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsthreadservicecallback-typedef"></a>JsThreadServiceCallback — Typedef
Wywołanie zwrotne wątku usługi.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 wywołanie zwrotne  
 Wywołanie zwrotne dla elementu roboczego w tle.  
  
 callbackData  
 Argument dane do przekazania do wywołania zwrotnego.  
  
## <a name="remarks"></a>Uwagi  
 Hosta można określić usługa wątku w tle podczas wywoływania metody jscreateruntime —. Jeśli zostanie określona, elementów roboczych w tle zostaną przekazane do hosta, za pomocą tego wywołania zwrotnego. Oczekuje się rozpoczęcie wykonywania elementu roboczego tła natychmiast i zwrócić wartość true lub zwróci wartość false, hosta i środowiska uruchomieniowego obsłuży pracy elementu w wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)