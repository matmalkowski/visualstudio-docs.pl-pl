---
title: Element JsSerializedScriptLoadSourceCallback Typedef | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff3bc206cf3779023a13166f30e8f4f719e7ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptloadsourcecallback-typedef"></a>JsSerializedScriptLoadSourceCallback — Typedef
Wywoływane przez środowisko uruchomieniowe załadować kodu źródłowego serializacji skryptu.     Obiekt wywołujący przechowuje buforu skryptu ważny do `JsSerializedScriptUnloadCallback`.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `sourceContext`  
 Kontekst przekazywany do `JsParseSerializedScriptWithCallback` lub `JsRunSerializedScriptWithCallback`.  
  
 `scriptBuffer`  
 Zwróconym przez skrypt.  
  
## <a name="remarks"></a>Uwagi  
  
> [!WARNING]
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)