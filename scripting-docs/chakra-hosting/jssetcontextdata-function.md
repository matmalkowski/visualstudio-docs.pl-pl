---
title: Funkcja JsSetContextData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be90aa6a-b001-4a6f-90c5-c2135e913be0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c03c34578855cf5ed6de10a43b8295a8273a4319
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jssetcontextdata-function"></a>Funkcja JsSetContextData
Ustawia dane wewnętrzne JsrtContext.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsSetContextData(  
  _In_ JsContextRef context,  
  _In_ void *data  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `context`  
 Kontekst ustawioną danych.  
  
 `data`  
 Wskaźnik do danych ma zostać ustawiona.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)