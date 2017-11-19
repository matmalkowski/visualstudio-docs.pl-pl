---
title: "Jsstringtopointer — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsStringToPointer
helpviewer_keywords: JsStringToPointer function
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ff84f929833941fed9a709497dc615189c39386
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsstringtopointer-function"></a>JsStringToPointer — Funkcja
Pobiera wskaźnik ciągu wartość ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 Wartość ciągu można przekonwertować na wskaźnik ciągu.  
  
 `stringValue`  
 Wskaźnik ciągu.  
  
 `stringLength`  
 Długość ciągu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja pobiera wskaźnik ciągu wartość ciągu. Powiedzie się i `JsErrorInvalidArgument` Jeśli typ wartości nie jest ciągiem. Okres istnienia ciąg zwrócony będzie taka sama jak okres istnienia wartość, która pochodzi z jednak wskaźnikiem do ciągu nie jest uważana za odwołania do wartości (w związku z czym nie będą przechowywane z są zbierane).  
  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)