---
title: "Jsgetundefinedvalue — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetUndefinedValue
helpviewer_keywords: JsGetUndefinedValue function
ms.assetid: e118eaf6-452c-42f2-86b8-e63c7d987cba
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c1788f7edeeb6df1ccf7eb3b6918322a65f2db8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetundefinedvalue-function"></a>JsGetUndefinedValue — Funkcja
Pobiera wartość `undefined` w bieżącym kontekście skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsGetUndefinedValue(  
   _Out_ JsValueRef *undefinedValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `undefinedValue`  
 `undefined` Wartość.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)