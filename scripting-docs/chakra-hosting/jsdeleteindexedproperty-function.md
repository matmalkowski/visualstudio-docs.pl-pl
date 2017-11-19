---
title: "Jsdeleteindexedproperty — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsDeleteIndexedProperty
helpviewer_keywords: JsDeleteIndexedProperty function
ms.assetid: cc876839-2ecd-41a8-82d0-c19b3de944e3
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e1cdf122cd721ddd50d67e1575c8dbb35bae4f70
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsdeleteindexedproperty-function"></a>JsDeleteIndexedProperty — Funkcja
Usuń wartość w określonym indeksie obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsDeleteIndexedProperty(  
   _In_ JsValueRef object,  
   _In_ JsValueRef index  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `object`  
 Obiekt do działania na.  
  
 `index`  
 Indeks do usunięcia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)