---
title: "JsBackgroundWorkItemCallback — Typedef | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c4281ae1abf1df07d4b6374b6989377c66c1fd7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsbackgroundworkitemcallback-typedef"></a>JsBackgroundWorkItemCallback — Typedef
Wywołanie zwrotne elementu roboczego tła.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 callbackData  
 Dane argument przekazany do usługi wątku.  
  
## <a name="remarks"></a>Uwagi  
 To jest przekazywana do hosta wątku usługi (jeśli jest dostępny) umożliwia hosta do wywołania wywołania zwrotnego elementu roboczego w wątku w tle siebie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)