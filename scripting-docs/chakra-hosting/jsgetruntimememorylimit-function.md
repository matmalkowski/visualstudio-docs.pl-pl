---
title: "Jsgetruntimememorylimit — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetRuntimeMemoryLimit
helpviewer_keywords: JsGetRuntimeMemoryLimit function
ms.assetid: ed81ca60-99fd-46b0-89ae-f6ac07926904
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6373e166ff4efe6bc8c5a33d203d60647c4be9b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetruntimememorylimit-function"></a>JsGetRuntimeMemoryLimit — Funkcja
Pobiera bieżący limit pamięci dla programu obsługi.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsGetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ size_t *memoryLimit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `runtime`  
 Środowisko uruchomieniowe, których limit pamięci ma być pobrana.  
  
 `memoryLimit`  
 Środowiska uruchomieniowego bieżący limit pamięci, w bajtach lub wartość -1, jeżeli nie ustawiono żadnego limitu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Limit pamięci środowiska uruchomieniowego można zawsze może być pobrane, niezależnie od tego, czy środowisko wykonawcze jest aktywny w innym wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)