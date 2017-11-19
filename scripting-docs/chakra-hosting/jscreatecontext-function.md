---
title: "Jscreatecontext — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsCreateContext
helpviewer_keywords: JsCreateContext function
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee756158401468ee00007a764e18a0846f35a3dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jscreatecontext-function"></a>JsCreateContext — Funkcja
Tworzy kontekst skryptu do uruchamiania skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `runtime`  
 Środowisko uruchomieniowe kontekstu skryptu jest tworzony w.  
  
 `debugApplication`  
 Aplikacja debugowania używany do debugowania. Ten parametr może być null, w którym to przypadku debugowanie nie jest włączone dla kontekstu.  
  
 `newContext`  
 Kontekst utworzony skrypt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Każdy kontekst skrypt ma własną globalny obiekt, który jest odizolowana od innych kontekstach skryptu.  
  
 `debugApplication` Parametr nie jest obsługiwany w trybie krawędzi. Aby uzyskać więcej informacji na temat używania tego interfejsu API w trybie krawędzi, zobacz [krawędzi przeznaczonych dla wersji programu vs. Starsze aparaty](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)