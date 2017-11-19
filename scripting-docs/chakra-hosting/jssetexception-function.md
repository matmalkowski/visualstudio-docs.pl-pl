---
title: "Jssetexception — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsSetException
helpviewer_keywords: JsSetException function
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d8fce71f14dedea02e1809fb72281f575f60604
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jssetexception-function"></a>JsSetException — Funkcja
Ustawia środowisko uruchomieniowe bieżącego kontekstu w stanie wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `exception`  
 Wyjątek JavaScript można ustawić bieżącego kontekstu środowiska uruchomieniowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `JsNoError`Jeśli aparat został ustawiony w stan wyjątek, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli środowisko uruchomieniowe bieżącego kontekstu jest już w stanie wyjątek, zwraca ten interfejs API `JsErrorInExceptionState`.  
  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)