---
title: "Jsrunserializedscript — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsRunSerializedScript
helpviewer_keywords: JsRunSerializedScript function
ms.assetid: 3fd3f6f1-eb3e-4751-92a5-c93b1035f3b2
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b770edbcaa4e7dc36f295407627c10a8b574b88b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsrunserializedscript-function"></a>JsRunSerializedScript — Funkcja
Uruchamia skrypt serializacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScript(  
   _In_z_ const wchar_t *script,  
   _In_ BYTE *buffer,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `script`  
 Kod źródłowy skryptu serializacji.  
  
 `buffer`  
 Skrypt serializacji.  
  
 `sourceContext`  
 Plik cookie identyfikowanie skrypt, który może służyć kontekstów możliwością debugowania skryptu.  
  
 `sourceUrl`  
 Lokalizacja skryptu pochodzi z.  
  
 `result`  
 Wynik uruchomienia skryptu, jeśli istnieje. Ten parametr może mieć wartości null.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga kontekstu aktywnego skryptu.  
  
 Bufor nie jest trwały w pamięci przez aparat skryptów, więc kodu muszą zapewnić aktywności dla tak długo, jak długo może służyć do wykonywania skryptów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)