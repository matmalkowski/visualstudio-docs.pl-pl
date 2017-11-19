---
title: "Jshasexception — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsHasException
helpviewer_keywords: JsHasException function
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32334f4b8787bebaffb9553fcdd40f85334462cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jshasexception-function"></a>JsHasException — Funkcja
Określa, czy środowisko uruchomieniowe bieżącego kontekstu jest w stanie wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hasException`  
 Określa, czy środowisko uruchomieniowe bieżącego kontekstu jest w stanie wyjątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wywołanie wyniki środowiska uruchomieniowego wyjątku (albo w wyniku uruchomienia skryptu lub z powodu coś, takich jak błędu konwersji), środowisko wykonawcze jest umieszczany w "wyjątku stan." Wszystkie wywołania w dowolnym kontekście tworzone przez środowisko uruchomieniowe (z wyjątkiem wyjątek interfejsów API) zakończy się niepowodzeniem z `JsErrorInExceptionState` dopóki wyjątek jest wyczyszczone.  
  
 Jeśli środowisko uruchomieniowe bieżącego kontekstu jest w stanie wyjątek, gdy wywołanie zwrotne powróci do silnika, aparat zostanie automatycznie ponownie Zgłoś wyjątek.  
  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)