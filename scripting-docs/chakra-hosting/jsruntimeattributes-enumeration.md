---
title: "Jsruntimeattributes — wyliczenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsRuntimeAttributes
helpviewer_keywords: JsRuntimeAttributes enumeration
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a7917ad5468b8d2924526f953ae444c5d8381eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsruntimeattributes-enumeration"></a>JsRuntimeAttributes — Wyliczenie
Atrybuty czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum JsRuntimeAttributes;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|Środowisko uruchomieniowe powinien obsługiwać skryptów niezawodny przerwania. Powoduje to zwiększenie liczby miejsc, gdy środowisko wykonawcze będzie sprawdzać dostępność żądanie przerwania skryptu kosztem małej ilości wydajność środowiska uruchomieniowego.|  
|`JsRuntimeAttributeDisableBackgroundWork`|Środowisko uruchomieniowe nie będzie wykonywał żadnych pracy (np. pamięci) na wątki w tle.|  
|`JsRuntimeAttributeDisableEval`|Przy użyciu `eval` lub `function` Konstruktor spowoduje zgłoszenie wyjątku.|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|Środowisko uruchomieniowe nie będą generowane kodu natywnego.|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|Środowisko uruchomieniowe zostaną włączone wszystkie funkcje eksperymentalne.|  
|`JsRuntimeAttributeEnableIdleProcessing`|Host będzie wywoływać `JsIdle`, więc Włącz bezczynności przetwarzania. W przeciwnym razie środowiska uruchomieniowego będzie nieco bardziej agresywnie zarządzać pamięcią.|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|Wywoływanie `JsSetException` spowoduje również wysyłki wyjątek do debugera skryptów (jeśli istnieją) nadanie debuger możliwość podział na wyjątek.|  
|`JsRuntimeAttributeNone`|Żadne specjalne atrybuty.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)