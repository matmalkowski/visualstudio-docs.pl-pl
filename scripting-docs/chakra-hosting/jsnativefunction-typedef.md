---
title: JsNativeFunction — Typedef | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cf475dd6a17434ea132647b7d8bde833f0de9e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788323"
---
# <a name="jsnativefunction-typedef"></a>JsNativeFunction — Typedef
Funkcja wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 wywoływany  
 A `Function` obiekt, który reprezentuje wywoływaną funkcję.  
  
 isConstructCall  
 Wskazuje, czy jest regularne połączenia lub wywołania "new".  
  
 argumenty  
 Argumenty dla wywołania.  
  
 argumentCount  
 Liczba argumentów.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Wynik wywołania, jeśli istnieje.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)