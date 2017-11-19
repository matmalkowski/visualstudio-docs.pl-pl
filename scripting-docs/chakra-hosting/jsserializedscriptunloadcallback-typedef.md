---
title: Element typedef JsSerializedScriptUnloadCallback | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f485d31367f189231d354c653c8e58cc8656eb9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptunloadcallback-typedef"></a>JsSerializedScriptUnloadCallback — typedef
Wywoływane przez środowisko uruchomieniowe, po zakończeniu ze wszystkimi zasobami związane z uruchamianiem skryptów.     Obiekt wywołujący powinna zwolnić źródła po załadowaniu, kod bajtowy i kontekstu, w tym momencie.  
  
## <a name="syntax"></a>Składnia  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `sourceContext`  
 Kontekst przekazywany do `JsParseSerializedScriptWithCallback` lub `JsRunSerializedScriptWithCallback`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!WARNING]
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)