---
title: "Jsnumbertoint — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f24acb837fdf46694aa2370e2ccf1fe3c926ce19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsnumbertoint-function"></a>JsNumberToInt — funkcja
Pobiera `int` wartość wartość liczbową.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 Liczba wartość do przekonwertowania na `int` wartość.  
  
 `intValue`  
 `int` Wartość.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja pobiera wartość wartość liczbową i konwertuje `int` wartość. Powiedzie się i `JsErrorInvalidArgument` Jeśli typ wartości nie jest liczba.  
  
 Wymaga kontekstu aktywnego skryptu.  
  
 Ten interfejs API jest obsługiwana tylko w trybie krawędzi.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)