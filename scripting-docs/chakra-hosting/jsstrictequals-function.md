---
title: "Jsstrictequals — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsStrictEquals
helpviewer_keywords: JsStrictEquals function
ms.assetid: b35bc655-7ff8-496a-b678-8950bb976047
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d5d88bc98db3d0ec7fa8e80fd72a287ef8957e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsstrictequals-function"></a>JsStrictEquals — Funkcja
Porównuje dwie wartości JavaScript strict pod kątem równości.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsStrictEquals(  
   _In_ JsValueRef object1,  
   _In_ JsValueRef object2,  
   _Out_ bool *result  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `object1`  
 Pierwszy obiekt, który ma zostać porównany.  
  
 `object2`  
 Drugi obiekt, który będzie porównywany.  
  
 `result`  
 Określa, czy wartości są ściśle równe.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest odpowiednikiem `===` operator w Javascript.  
  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)