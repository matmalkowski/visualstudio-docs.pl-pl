---
title: "Jspointertostring — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsPointerToString
helpviewer_keywords: JsPointerToString function
ms.assetid: c71ce07e-4359-450c-afbf-a6ab7d48dddf
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ac3d8ede644178527591b77fdb42f2b8c3e579b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jspointertostring-function"></a>JsPointerToString — Funkcja
Tworzy wartość typu ciąg ze wskaźnikiem do ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsPointerToString(  
   _In_reads_(stringLength) const wchar_t *stringValue,  
   _In_ size_t stringLength,  
   _Out_ JsValueRef *value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stringValue`  
 Wskaźnik ciągu można przekonwertować na ciąg.  
  
 `stringLength`  
 Długość ciąg do przekonwertowania.  
  
 `value`  
 Nową wartość ciągu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)