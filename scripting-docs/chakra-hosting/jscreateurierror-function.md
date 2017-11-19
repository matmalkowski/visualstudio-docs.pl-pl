---
title: "Jscreateurierror — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsCreateURIError
helpviewer_keywords: JsCreateURIError function
ms.assetid: 711fd237-12a2-4ff0-b58a-ad74c91e79fb
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9750f9a554cd442c26a45fcc97e70273b15df9ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jscreateurierror-function"></a>JsCreateURIError — Funkcja
Tworzy nowy obiekt błąd JavaScript URIError  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsCreateURIError(  
   _In_ JsValueRef message,  
   _Out_ JsValueRef *error  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `message`  
 Komunikat dla obiekt błędu.  
  
 `error`  
 Nowy obiekt błędu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)