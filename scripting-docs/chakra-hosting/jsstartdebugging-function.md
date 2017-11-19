---
title: "Jsstartdebugging — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsStartDebugging
helpviewer_keywords: JsStartDebugging function
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd9b7e3deb407d1a1e9d16db38e17c85ccc8c797
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsstartdebugging-function"></a>JsStartDebugging — Funkcja
Rozpoczyna debugowania w bieżącym kontekście.  
  
## <a name="syntax"></a>Składnia  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `debugApplication`  
 Aplikacja debugowania używany do debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Host upewnij się, że `CoInitializeEx` jest wywoływana z `COINIT_MULTITHREADED` lub `COINIT_APARTMENTTHREADED` co najmniej raz, przed użyciem tego interfejsu API  
  
 `debugApplication` Parametr nie jest obsługiwany w trybie krawędzi. Aby uzyskać więcej informacji na temat używania tego interfejsu API w trybie krawędzi, zobacz [krawędzi przeznaczonych dla wersji programu vs. Starsze aparaty](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)