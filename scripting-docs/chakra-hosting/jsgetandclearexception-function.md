---
title: "Jsgetandclearexception — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetAndClearException
helpviewer_keywords: JsGetAndClearException function
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e7e4f89bac59aa776762586ab20fa831b5c24bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetandclearexception-function"></a>JsGetAndClearException — Funkcja
Zwraca wyjątek, który spowodował środowiska wykonawczego o bieżącym kontekście stanu wyjątku i resetuje stan wyjątku dla tego programu obsługi.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `exception`  
 Wyjątek środowiska uruchomieniowego bieżącego kontekstu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli środowisko uruchomieniowe bieżącego kontekstu nie jest w stanie wyjątek, zwraca ten interfejs API `JsErrorInvalidArgument`. Jeśli środowisko uruchomieniowe jest wyłączone, zwróci wyjątek wskazujący, że skrypt został zakończony, ale nie usunie wyjątek (wyjątek zostanie usunięty, jeśli środowisko uruchomieniowe jest ponownie włączyć za pomocą `JsEnableRuntimeExecution`).  
  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)